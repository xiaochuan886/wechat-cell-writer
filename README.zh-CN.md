# wechat-cell-writer

[English](./README.md) | 简体中文

`wechat-cell-writer` 是一个本地 skill，用于围绕细胞治疗和生物医学主题，完成微信公众号文章的检索、选题、写作、配图规划、校验和发布前整理。

## 包含内容

- `SKILL.md`：总控入口和工作流说明
- `references/`：写作、配图、引用、发布、合规等参考文档
- `scripts/`：初始化、图片规划、校验、清洗、论文截图等可执行脚本
- `agents/openai.yaml`：OpenAI 兼容 skill 场景的 UI 元数据

## 工作流

1. 初始化文章工作目录
2. 在 `research.md` 中整理最新资料
3. 在 `topics.md` 中形成选题候选
4. 完成 `article.md` 写作
5. 生成配图和论文截图
6. 在发布前完成校验和清洗

## 快速开始

```bash
cd scripts
npm install

npm run workflow:init -- --topic "NK细胞科普"
```

或者直接运行 workflow runner：

```bash
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step init --topic "NK细胞科普"
```

## 常用命令

```bash
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step plan-images --dir "$ARTICLE_DIR"
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step validate-images --dir "$ARTICLE_DIR"
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step validate-research --dir "$ARTICLE_DIR"
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step validate --dir "$ARTICLE_DIR"
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step sanitize --dir "$ARTICLE_DIR"
```

## 默认约束

- 固定作者：`细胞小境`
- 目标受众：中文微信公众号读者
- 图片中面向读者的核心文字必须为简体中文
- `CAR-T`、`NK`、`TIL`、`iPSC` 等专业缩写可保留
- 如论文原站页面被拦截或遮挡，`screenshot-paper.ts` 可通过 `--pubmed-url` 自动回退到 PubMed

## License

MIT
