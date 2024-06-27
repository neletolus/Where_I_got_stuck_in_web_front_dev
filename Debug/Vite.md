# Viteでデバッグする時のメモ

## 実機デバッグ
`vite.config.ts`のdefineConfigに、下記を追加
```ts
server: {
    host: true,
    port: 5173,
}
```

