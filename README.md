# panbox-dist

PanBox 三平台发布构建与 Release 分发仓（构建壳，不含源码）。

- **构建**：Actions 经最小权限 fine-grained PAT（只读私有源码仓 `alonjoik/panbox` 的 Contents）检出源码，三平台并行构建后统一挂 Draft Release。
- **触发**：`workflow_dispatch`（手动输版本号）或 push `v*` tag。
- **产物**：Windows NSIS 安装包 / Android APK（arm64+armv7）/ iOS TrollStore IPA。
- **安全边界**：PAT 仅 `Contents: Read-only` 且只授 `panbox` 一仓；构建日志公开，勿在构建中打印敏感信息；源码不落本仓、构建结束即随 runner 销毁。

方案全文见私有源码仓 `docs/ci-cd-multiplatform.md`。
