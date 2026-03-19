# 01 - 项目架构总览

> 本文档是你学习 FastAPI 框架源码的第一站。我们将从宏观视角了解这个项目"长什么样"，每个目录和文件是做什么的，以及一个 HTTP 请求是如何从进入到返回的。

## 1. 这个项目是什么？

这个项目就是 **FastAPI 框架本身的源代码**（版本 0.133.1），不是一个"用 FastAPI 写的应用"，而是 FastAPI 这个工具本身。

打个比方：如果说 FastAPI 是一把锤子，普通开发者是"用锤子盖房子"，而我们现在要做的是"研究这把锤子是怎么造出来的"。

---

## 2. 根目录结构

```
Anlaysis-fastapi/                  ← 项目根目录
├── fastapi/                       ← ⭐ 核心源码（框架本体）
├── docs_src/                      ← ⭐ 官方教程示例代码（学习的宝库）
├── tests/                         ← 测试代码（200+ 个测试文件）
├── docs/                          ← 文档网站内容
├── scripts/                       ← 开发脚本（格式化、测试、部署等）
├── fastapi-slim/                  ← 精简版 FastAPI 构建配置
├── pyproject.toml                 ← ⭐ 项目配置文件（依赖、构建、工具配置）
├── README.md                      ← 项目说明
├── LICENSE                        ← MIT 开源协议
├── CONTRIBUTING.md                ← 贡献指南
├── SECURITY.md                    ← 安全策略
├── CITATION.cff                   ← 学术引用信息
├── .python-version                ← Python 版本要求
├── .pre-commit-config.yaml        ← 代码提交前自动检查配置
├── uv.lock                        ← 依赖锁定文件
└── .venv/                         ← Python 虚拟环境
```

### 对你最重要的三个目录

| 目录 | 作用 | 你应该怎么用 |
|------|------|-------------|
| `fastapi/` | FastAPI 框架的全部源码 | 深入理解框架原理时阅读 |
| `docs_src/` | 官方文档里每一个教程的示例代码 | **最适合新手学习的入口**，每个子目录对应一个知识点 |
| `tests/` | 框架的测试代码 | 了解每个功能的预期行为 |

---

## 3. 核心源码目录：`fastapi/`

```
fastapi/
├── __init__.py          ← ⭐ 包入口：定义了你能 import 的所有公开 API
├── __main__.py          ← 允许 `python -m fastapi` 运行 CLI
├── applications.py      ← ⭐ FastAPI 类定义（整个框架的"大脑"，4692 行）
├── routing.py           ← ⭐ APIRouter 和路由处理（4685 行）
├── params.py            ← ⭐ Path/Query/Body/Header/Cookie 参数定义
├── param_functions.py   ← 参数的快捷函数（供用户调用）
│
├── dependencies/        ← ⭐ 依赖注入系统
│   ├── models.py        ←   依赖模型定义
│   └── utils.py         ←   依赖解析工具
│
├── middleware/           ← 中间件（请求前/后的处理逻辑）
│   ├── cors.py          ←   跨域资源共享(CORS)
│   ├── gzip.py          ←   Gzip 压缩
│   ├── httpsredirect.py ←   HTTPS 重定向
│   ├── trustedhost.py   ←   可信主机检查
│   └── asyncexitstack.py←   异步退出栈（清理资源）
│
├── security/            ← 安全与认证
│   ├── api_key.py       ←   API Key 认证
│   ├── http.py          ←   HTTP Basic/Bearer/Digest 认证
│   ├── oauth2.py        ←   OAuth2 认证
│   └── open_id_connect_url.py ← OpenID Connect
│
├── openapi/             ← OpenAPI 文档自动生成
│   ├── docs.py          ←   Swagger UI / ReDoc 页面生成
│   ├── models.py        ←   OpenAPI 数据模型
│   └── utils.py         ←   OpenAPI Schema 生成工具
│
├── _compat/             ← Pydantic 兼容层
│   ├── v2.py            ←   Pydantic v2 适配
│   └── shared.py        ←   共享兼容代码
│
├── requests.py          ← 请求对象
├── responses.py         ← 响应对象
├── exceptions.py        ← 异常定义（HTTPException 等）
├── exception_handlers.py← 异常处理器
├── encoders.py          ← JSON 编码器
├── background.py        ← 后台任务
├── concurrency.py       ← 并发工具
├── datastructures.py    ← 数据结构（如 UploadFile）
├── staticfiles.py       ← 静态文件服务
├── templating.py        ← 模板引擎
├── testclient.py        ← 测试客户端
├── websockets.py        ← WebSocket 支持
├── cli.py               ← 命令行接口入口
├── logger.py            ← 日志
├── types.py             ← 类型定义
└── utils.py             ← 工具函数
```

### 最重要的 5 个文件（按学习优先级排序）

| 文件 | 行数 | 作用 | 为什么重要 |
|------|------|------|-----------|
| `__init__.py` | 25行 | 公开 API 导出清单 | 告诉你 FastAPI 对外暴露了哪些功能 |
| `applications.py` | 4692行 | `FastAPI` 类（继承自 Starlette） | 整个框架的核心，所有路由注册都在这里 |
| `routing.py` | 4685行 | `APIRouter` 类和路由处理 | 请求是如何被分发到正确的函数的 |
| `params.py` | 755行 | 参数类定义 | 理解 `Query()`, `Path()`, `Body()` 的内部实现 |
| `dependencies/utils.py` | — | 依赖注入解析 | FastAPI 最核心的"魔法"之一 |

---

## 4. 教程示例目录：`docs_src/`

这是**对新手最友好的目录**，包含 73 个子目录，每个对应一个 FastAPI 官方教程主题：

```
docs_src/
├── first_steps/              ← 🟢 入门第一步（Hello World）
├── path_params/              ← 🟢 路径参数
├── query_params/             ← 🟢 查询参数
├── body/                     ← 🟢 请求体
├── body_fields/              ← 请求体字段验证
├── body_multiple_params/     ← 多个请求体参数
├── body_nested_models/       ← 嵌套模型
├── response_model/           ← 响应模型
├── extra_models/             ← 多模型复用
├── handling_errors/          ← 错误处理
├── dependencies/             ← 🟡 依赖注入
├── security/                 ← 🟡 安全认证
├── middleware/               ← 中间件
├── cors/                     ← 跨域请求
├── sql_databases/            ← 🟡 数据库集成
├── bigger_applications/      ← 🔴 大型项目结构（多文件组织）
├── background_tasks/         ← 后台任务
├── websockets/               ← WebSocket
├── ...还有 50+ 个主题
```

> 🟢 = 入门级 | 🟡 = 进阶级 | 🔴 = 高级

### 最简单的入门示例

文件 `docs_src/first_steps/tutorial001_py310.py`（仅 8 行代码）：

```python
from fastapi import FastAPI          # 第1行：导入 FastAPI 类

app = FastAPI()                      # 第3行：创建应用实例

@app.get("/")                        # 第6行：注册一个 GET 路由
async def root():                    # 第7行：定义处理函数
    return {"message": "Hello World"} # 第8行：返回 JSON 响应
```

这 8 行代码就是一个**完整的、可运行的 Web API**！

### 大型项目结构示例

当项目变大后，FastAPI 推荐使用 `APIRouter` 拆分模块。参见 `docs_src/bigger_applications/app_an_py310/`：

```
app_an_py310/
├── __init__.py          ← 标记为 Python 包
├── main.py              ← ⭐ 主入口：创建 app，挂载所有路由
├── dependencies.py      ← 公共依赖（如认证检查）
├── routers/             ← 路由模块目录
│   ├── __init__.py
│   ├── items.py         ← /items 相关的路由
│   └── users.py         ← /users 相关的路由
└── internal/            ← 内部管理模块
    ├── __init__.py
    └── admin.py          ← /admin 相关的路由
```

**`main.py` 的代码**（23行）：

```python
from fastapi import Depends, FastAPI
from .dependencies import get_query_token, get_token_header
from .internal import admin
from .routers import items, users

app = FastAPI(dependencies=[Depends(get_query_token)])  # 全局依赖

app.include_router(users.router)                         # 挂载用户路由
app.include_router(items.router)                         # 挂载商品路由
app.include_router(                                      # 挂载管理路由
    admin.router,
    prefix="/admin",                                     # URL 前缀
    tags=["admin"],                                      # API 文档分组标签
    dependencies=[Depends(get_token_header)],             # 路由级依赖
)

@app.get("/")
async def root():
    return {"message": "Hello Bigger Applications!"}
```

---

## 5. FastAPI 的核心依赖关系

FastAPI 不是从零开始写的，它站在两个巨人的肩膀上：

```
┌─────────────────────────────────────────┐
│              你的应用代码                 │
├─────────────────────────────────────────┤
│         FastAPI（本项目）                │  ← 提供：参数验证、依赖注入、
│                                         │     OpenAPI 文档自动生成
├──────────────────┬──────────────────────┤
│    Starlette     │     Pydantic         │
│  （Web 框架底层） │  （数据验证引擎）     │
│  处理 HTTP 请求   │  处理数据类型检查     │
│  路由分发         │  JSON 序列化/反序列化 │
│  中间件           │  模型定义             │
│  WebSocket        │                      │
├──────────────────┴──────────────────────┤
│             Uvicorn / ASGI              │  ← Web 服务器
└─────────────────────────────────────────┘
```

从 `pyproject.toml` 可以看到核心依赖：
- **starlette >= 0.40.0**：Web 框架底层（HTTP、路由、中间件）
- **pydantic >= 2.7.0**：数据验证和序列化
- **typing-extensions >= 4.8.0**：增强的类型提示支持

> **ASGI 是什么？** Asynchronous Server Gateway Interface（异步服务器网关接口），是 Python 异步 Web 应用和 Web 服务器之间的标准接口协议。你可以把它理解为"Python 异步 Web 世界的通用插座标准"。

---

## 6. 一个 HTTP 请求的完整旅程

当用户发送 `GET /items/42` 时，请求在框架内部的流转路径：

```
客户端请求 GET /items/42
       │
       ▼
  ┌─────────────┐
  │  Uvicorn     │  ① Web 服务器接收 HTTP 请求
  │  (ASGI 服务器)│
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │  中间件链    │  ② 依次执行中间件（CORS、GZip 等）
  │  middleware/ │
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │  路由匹配    │  ③ routing.py 匹配 URL 模式
  │  routing.py  │     "/items/{item_id}" 匹配成功
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │  依赖注入    │  ④ dependencies/ 解析并执行依赖
  │  dependencies│     （如数据库连接、认证检查）
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │  参数解析    │  ⑤ params.py 从 URL/Header/Body 中
  │  params.py   │     提取参数并用 Pydantic 验证
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │  执行端点    │  ⑥ 调用你写的 async def read_item()
  │  你的函数    │
  └──────┬──────┘
         ▼
  ┌─────────────┐
  │  响应处理    │  ⑦ 将返回值序列化为 JSON
  │  responses.py│
  └──────┬──────┘
         ▼
    返回 JSON 响应给客户端
```

---

## 7. `__init__.py`：FastAPI 的"公开菜单"

文件 `fastapi/__init__.py` 只有 25 行，但它定义了 FastAPI 对外暴露的所有核心 API：

```python
from .applications import FastAPI      # 应用类
from .routing import APIRouter          # 路由器
from .requests import Request           # 请求对象
from .responses import Response         # 响应对象
from .param_functions import (
    Path, Query, Body, Header,          # 参数声明函数
    Cookie, Form, File,                 # 参数声明函数
    Depends, Security,                  # 依赖注入
)
from .exceptions import HTTPException   # HTTP 异常
from .background import BackgroundTasks # 后台任务
from .datastructures import UploadFile  # 文件上传
from .websockets import WebSocket       # WebSocket
```

当你写 `from fastapi import FastAPI` 时，Python 就是从这个文件找到 `FastAPI` 类的。

---

## 8. 下一步学习计划

现在你已经了解了整个项目的结构，接下来我们将进入**交错式学习循环（Step 2）**，按照以下顺序逐一深入学习 FastAPI 核心概念：

| 序号 | FastAPI 核心概念 | 对应源码位置 | 对应示例目录 |
|------|-----------------|-------------|-------------|
| 1 | 应用创建与路由注册 | `applications.py`, `routing.py` | `first_steps/` |
| 2 | 路径参数 | `params.py` | `path_params/` |
| 3 | 查询参数 | `params.py` | `query_params/` |
| 4 | 请求体与 Pydantic 模型 | `params.py` | `body/` |
| 5 | 依赖注入 | `dependencies/` | `dependencies/` |
| 6 | 异常处理 | `exceptions.py` | `handling_errors/` |
| 7 | 中间件 | `middleware/` | `middleware/` |
| 8 | 安全与认证 | `security/` | `security/` |
| 9 | 响应模型 | `responses.py` | `response_model/` |
| 10 | 大型项目组织 | `routing.py` (APIRouter) | `bigger_applications/` |

每个概念我们都会：先讲 FastAPI 概念 → 确认理解 → 再讲其中的 Python 语法 → 确认理解 → 进入下一个。
