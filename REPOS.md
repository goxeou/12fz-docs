# 12FZ 仓库结构

| 仓库 | 说明 | 负责人 | 状态 |
|------|------|--------|------|
| **12fz-docs** | 开发文档/架构设计/会议记录 | chaogu-ai | ✅ v9.2已推 |
| **12fz-sso** | 统一用户认证（Go） | gong3 | 🔧 待开发 |
| **12fz-chat** | 聊天系统（Go WebSocket） | gong3 | 🔧 待开发 |
| **12fz-ai** | AI服务层（Python） | chaogu-ai | 🔧 待开发 |
| **12fz-erp** | ERP核心业务（Java/Go） | 高级工程师 | 🔧 待开发 |
| **12fz-payment** | 支付服务 | gong3 | 🔧 待开发 |
| **12fz-infra** | 基础设施（Docker/CI/CD） | 服务器技术 | 🔧 待开发 |

## 开发路线（并行）

### gong3 — Go开发
1. `12fz-sso` → Go项目骨架 + 统一用户系统 + 认证网关
2. 代码推该仓库，我审核后合并
3. 依赖：PG部署（服务器技术给连接串）

### 服务器技术 — 基础设施
1. 202机器装 PG 18 + pgvector
2. 建biz/chat/sys三个Schema
3. Docker Compose（PG + Redis + Nginx）
4. 给gong3提供PG连接信息

### 高级工程师 — 数据迁移
1. `12fz-erp` → ERP数据迁移Oracle→PG
2. 清理 sys_permission 重复URL
3. 用此前导出的CSV导入PG

### chaogu-ai — Python AI
1. `12fz-ai` → AI服务骨架
2. 大模型接口（OpenAI兼容）
3. 后续对接聊天系统
