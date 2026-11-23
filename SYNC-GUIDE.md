# DOPI 知识库：另一台电脑使用与更新指南

**仓库：** `stanley-yuhaowen/dopi-knowledge-base`（Private）

## 方式 A：GitHub Desktop（不熟悉命令行最推荐）

1. 在第二台电脑安装 GitHub Desktop，并用拥有仓库访问权的 GitHub 账号登录。
2. 选择 **File → Clone repository**，找到 `stanley-yuhaowen/dopi-knowledge-base`，选本地保存位置。
3. 安装 Obsidian，选择 **Open folder as vault**，打开刚刚克隆的 `dopi-knowledge-base` 文件夹。
4. **每次开始编辑前：** 在 GitHub Desktop 点 **Fetch origin**，有更新就点 **Pull origin**。
5. 在 Obsidian 里新增、编辑 Markdown 后，回 GitHub Desktop 查看 Changes，填写摘要 → **Commit to main** → **Push origin**。
6. 换回第一台电脑，先 Pull 再开始编辑。不要让两台电脑在未同步时改同一篇文章。

## 方式 B：命令行

前提：安装 Git、完成 GitHub 身份验证；私有仓库必须登录或使用适当的凭据。以下命令仅用于已完成身份验证的电脑。

```bash
git clone https://github.com/stanley-yuhaowen/dopi-knowledge-base.git
cd dopi-knowledge-base
git pull --ff-only
# 在 Obsidian 中编辑并保存文件后：
git add .
git commit -m "docs: 更新知识库"
git push origin main
```

若 `git pull --ff-only` 提示无法快进，表示存在本地与远程不同提交；先处理冲突，不要强制覆盖。

## 方式 C：Obsidian Git 社区插件（可选）

可以在已经 clone 的 Vault 中安装 Obsidian Git，配置启动时拉取和定时备份/同步。插件依赖本机 Git、仓库权限和认证；首次必须正确配置，不能仅靠安装插件完成同步。移动设备与不同系统的兼容性需要单独检查。

## AI 怎么读取
- **Cursor / Codex / Claude Code 等本地工具：** 打开本仓库文件夹，明确要求 AI 先读 `AGENTS.md`、`knowledge/9-首页.md`，再读相关章节。不同工具自动加载规则可能不同，不能假设必然自动阅读。
- **支持 GitHub 连接器的在线 AI：** 授权它访问本私有仓库，并让它先读 `README.md`、`AGENTS.md` 与 `manifest.json`。没有访问授权时，即使给了仓库 URL 也不能读取。
- **只支持公开网址的 AI：** 私有仓库无法用 `raw.githubusercontent.com` 匿名访问。需要授权访问，或另建脱敏的公开资料库。

## 更新索引
- 更新原文件的文字，无需改变 `manifest.json`。
- 新增、删除或改名文件，要同步修改 `manifest.json` 的 `files` 列表。
- 如果多人或多设备协作，建议先 Pull，再改，最后 Push；GitHub 保留历史便于追踪。

## 安全
不要把 `.env`、访问令牌、客户身份证明、验光处方原图、详细收件信息或私人聊天记录提交到 Git 仓库。即使后来删除，历史提交也可能保留旧内容。
