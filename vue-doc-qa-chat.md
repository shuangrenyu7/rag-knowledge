# 外部项目：vue-doc-qa-chat

- 来源：https://github.com/YuiGod/vue-doc-qa-chat
- 授权：MIT License
- 定位：本地知识库问答系统的 Web 前端，需与 `py-doc-qa-deepseek-server` 配合使用。

## 技术栈

- Vue 3、TypeScript、Vite、Element Plus
- LangChain 与 DeepSeek R1 的本地知识库问答场景
- Pinia、Vue Router
- markdown-it 用于 Markdown 渲染与代码高亮
- Axios 与 Fetch 的统一请求封装，并提供请求/响应拦截和取消请求能力

## 主要功能

1. 聊天页面，支持流式响应并渲染 Markdown。
2. 文档上传、预览与向量化的前端交互。
3. 会话历史管理：列表、重命名和删除。
4. 代码块高亮和自定义 Markdown 样式。

## 前端目录职责

- `src/api`：聊天、会话历史、文档管理 API。
- `src/http`：Axios / Fetch 封装、拦截器、取消请求、错误处理和类型定义。
- `src/stores`：Pinia 状态管理。
- `src/router`：路由。
- `src/views/chat`：聊天页面及子组件。
- `src/views/documents`：文档管理页面。
- `src/utils/markdownit`：Markdown 和代码高亮封装。
- `src/styles/markdown`：Markdown 主题样式。

## 关键接口约定

- `POST /chat`：接收模型名、`stream: true` 和用户消息；返回 `application/x-ndjson` 流。
- 会话接口包括：`GET /session/list`、`POST /session/add`、`PUT /session/update`、`DELETE /session/delete`。
- 文档接口与后端文档管理 API 对接。

## 运行前提

- Node.js 18 或更高。
- 常规启动：`npm install` 后执行 `npm run dev`。

> 资料依据：项目公开 README，2026-10-16 收录。
