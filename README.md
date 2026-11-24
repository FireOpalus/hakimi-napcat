# hakimi-napcat

哈基米境内 NapCat OneBot v11 独立部署编排与配置模板仓库（部署于境内 `/opt/hakimi-napcat/`），并归档历史语音转写中继。

## 文件说明

- `docker-compose.napcat.yml` / `docker-compose.napcat.official-node.yml.example` / `compose.napcat.yml`：境内 NapCat 编排模板（WebUI 仅绑定 `127.0.0.1:6099`）。
- `.env.napcat.example` / `napcat-onebot11.json.example`：环境变量与 OneBot 反向 WSS 配置示例（不含真实凭证）。
- `legacy/napcat_voice_relay/`：已撤线归档的历史境内语音转写中继（现已切换为 QQ 语音原生直传 Gemini）。

## 部署示例

```bash
cp .env.napcat.example .env.napcat
chmod 600 .env.napcat
cp docker-compose.napcat.official-node.yml.example docker-compose.napcat.official-node.yml
docker compose --env-file .env.napcat \
  -f docker-compose.napcat.yml -f docker-compose.napcat.official-node.yml up -d
```

## 归档中继测试

```bash
uv sync
uv run ruff check .
uv run ruff format --check .
uv run pytest -q
```
