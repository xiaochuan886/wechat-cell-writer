# wechat-cell-writer

`wechat-cell-writer` is a local skill for researching, drafting, illustrating, validating, and preparing WeChat Official Account articles about cell therapy and biomedical topics.

## What It Includes

- `SKILL.md`: the orchestration entrypoint and workflow guidance
- `references/`: writing, image, citation, publishing, and compliance references
- `scripts/`: executable workflow helpers for init, image planning, validation, sanitizing, and paper screenshots
- `agents/openai.yaml`: UI metadata for OpenAI-compatible skill surfaces

## Workflow

1. Initialize an article workspace
2. Fill `research.md` with current findings
3. Draft topic candidates in `topics.md`
4. Write `article.md`
5. Generate images and paper screenshots
6. Validate and sanitize before publishing

## Quick Start

```bash
cd scripts
npm install

npm run workflow:init -- --topic "NK细胞科普"
```

Or run the workflow runner directly:

```bash
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step init --topic "NK细胞科普"
```

## Key Commands

```bash
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step plan-images --dir "$ARTICLE_DIR"
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step validate-images --dir "$ARTICLE_DIR"
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step validate-research --dir "$ARTICLE_DIR"
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step validate --dir "$ARTICLE_DIR"
node /Users/massifserver/.agents/skills/wechat-cell-writer/scripts/run-workflow.js --step sanitize --dir "$ARTICLE_DIR"
```

## Defaults

- Fixed author: `细胞小境`
- Audience: Chinese WeChat readers
- Core reader-facing image text must be Simplified Chinese
- Domain abbreviations such as `CAR-T`, `NK`, `TIL`, and `iPSC` are allowed
- If a cited paper page is blocked or overlaid, `screenshot-paper.ts` can fall back to PubMed via `--pubmed-url`

## License

MIT
