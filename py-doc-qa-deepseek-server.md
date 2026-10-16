# 外部项目：py-doc-qa-deepseek-server

- 来源：https://github.com/YuiGod/py-doc-qa-deepseek-server
- 授权：MIT License
- 定位：本地知识库问答系统的服务端，实现基础 RAG；可与 `vue-doc-qa-chat` 前端配合。

## 技术栈

- Python、FastAPI、Uvicorn
- LangChain、DeepSeek R1（通过 Ollama 本地运行）
- SQLModel、SQLite
- Chroma 向量数据库

## 主要功能

1. 文档上传、保存、列表、读取、更新、删除与向量化。
2. 使用 SQLite 保存文档元数据、聊天会话和聊天历史。
3. 聊天接口支持 JSON 对象流式响应（`application/x-ndjson`）。
4. 基础 RAG：读取文档、切分、向量化并检索后生成回答。

## 后端目录职责

- `app/core/base.py`：LangChain 常量及模型配置。
- `app/core/langchain_retrieval.py`：检索链构建。
- `app/core/langchain_vector.py`：文档读取、切分与向量化。
- `app/crud`：文档、会话和聊天历史的数据库 CRUD。
- `app/models`：SQLModel 数据模型。
- `app/routers`：聊天、会话及文档 API 路由。
- `app/main.py`：服务启动入口。

## 数据与 API

- `document`：文档名称、文件名、路径、后缀、是否已向量化、创建时间。
- `chatsession`：会话标题和创建时间。
- `chathistory`：角色、内容、思考内容、所属会话和时间。
- `POST /chat`：流式聊天。
- 文档接口包括：`/documents/page`、`/documents/add`、`/documents/update`、`/documents/delete`、`/documents/read`、`/documents/vector-all`。

## 运行前提

- 安装 Ollama 并部署 `deepseek-r1:7b`，模型名可在 `app/core/base.py` 调整。
- 安装依赖：`pip install -r requirements.txt`。
- 在 `app` 目录运行：`python main.py`。

> 资料依据：项目公开 README，2026-10-16 收录。
