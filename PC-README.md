# DeWEB PC Shell 0.1.0

Windows 桌面版 DeWEB：WPF + WebView2，链上 Web 容器直读，钱包操作由 OKX App 完成。

## 安装

运行 `DeWEB-PC-0.1.0-win-x64.msi`，或解压 `DeWEB-PC-0.1.0-win-x64.zip` 后启动
`DeWebPcShellPoc.exe`。

- Windows 10/11 x64
- 需要 Microsoft Edge WebView2 Runtime（系统通常已安装）
- 安装包未做 Authenticode 代码签名，Windows 可能显示“未知发布者”

## 数据与卸载

运行数据位于 `%LocalAppData%\DeWEB`，包括 WebView2 profile、站点会话、日志和缓存。

- 应用内：设置 → 高级诊断 → 程序目录/日志路径
- 清理运行数据：`DeWebPcShellPoc.exe --cleanup --quiet`
- MSI 卸载会清理上述运行数据

## 主容器校验

默认行为与手机端一致：

- 从 X Layer 读取主容器 `index.html`
- 链上 `fileInfo` 需要 2 家独立 RPC 一致
- 页面字节 SHA-256 必须等于链上 `fileInfo.sha256`
- 主文档缓存按当前链上 hash 校验，旧缓存不会遮住新页面

设置中可打开“严格固定主文档”：

- 只接受内置 root hash 或签名 policy 授权的 hash
- 适合高风险用户；Web 更新前必须先发布签名 policy

## 安全边界

- 站点和钱包窗口有精确 origin 校验
- 站点会话使用 Windows DPAPI CurrentUser
- 所有下载需要原生确认
- Assets 清单和更新清单使用 ECDSA P-256/SHA-256 签名
- 钱包签名、交易确认由 OKX App 完成
- 私钥、助记词、云同步密码不在本应用内保存

## 更新

- PC 更新清单：`https://download.dewebdesk.link/pc-latest.json`
- 严格模式 policy：`https://download.dewebdesk.link/pc-main-policy.json`
- 检查更新只打开官方下载页，不自动下载或安装

## 限制

- 安装包/EXE 没有 Authenticode 签名
- 运行数据不承诺跨版本兼容
- 同用户恶意软件仍可篡改同用户可写文件；本应用不能提供操作系统级隔离
- 链上主文档默认跟随当前链上 hash；严格模式需要正确发布 policy

## 许可证

- 应用二进制许可证：`LICENSE`
- 第三方组件声明：`THIRD_PARTY_NOTICES.md`

第三方组件仍适用其各自许可证。
