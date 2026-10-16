# flame-lzcapp

[Flame](https://github.com/pawelmalak/flame) 的 LazyCat LPK 打包 —— 自托管服务器启动页（Docker 容器）。

## 形态

- 单容器镜像：`pawelmalak/flame`，端口 5005
- 镜像交付：mirror 模式（`docker.1ms.run/pawelmalak/flame:{tag}`）
- 版本发现：Docker Hub 严格 SemVer tag，排除 `multiarch` 前缀与 `latest`
- 密码体系：部署参数 `login_password`（自动生成），PASSWORD env + 免密登录注入
- 数据持久化：`/lzcapp/var/data` -> `/app/data`
- 未挂载 docker.sock（不启用 Docker 集成）

## 结构

- `package.yml` — LPK v2 包元数据（`community.lazycat.app.flame`）
- `lzc-manifest.yml` — 单服务 + upstreams + simple-inject-password 免密注入
- `lzc-deploy-params.yml` — 登录密码部署参数
- `.github/lazycat-action.yml` — 镜像版本源，mirror 交付，仅私有商店
- `.github/workflows/lazycat.yml` — 每日自动跟版 + 发布喵喵商店
