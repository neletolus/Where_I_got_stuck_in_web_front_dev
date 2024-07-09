# CloudFront メモ

## CloudFrontでサブディレクトリにスラッシュ・htmlファイル指定なしのアドレスでアクセスしたい
- example.com/game/index.html
- example.com/game/

に対してアクセスするよう、ハンドラを作るのは簡単だが、
- example.com/game
にアクセスした時の挙動を作るのは結構面倒


下記のように対応する
```javascript
function handler(event) {
  var request = event.request;
  var host = request.headers.host.value;
  var uri = request.uri;
  var newurl = 'https://elleactive2024.com/'; // Product server URI

  var redirect = false;
  // Fireworks AR page
  if (uri === '/fireworks') {
    newurl = `https://${host}/fireworks/`
    redirect = true;
  }
  // Stairs AR page
  else if (uri === '/stairs') {
    newurl = `https://${host}/stairs/`
    redirect = true;
  }
  
  if (redirect === true) {
    const response = {
      statusCode: 302,
      statusDescription: 'Found',
      headers:
        { "location": { "value": newurl } }
    }
    return response;
  }
  
  // Check whether the URI is missing a file name.
  if (uri.endsWith("/")) {
    request.uri += "index.html";
  }
  // Check whether the URI is missing a file extension.
  else if (!uri.includes(".")) {
    request.uri += "/index.html";
  }

  return request;
}
```