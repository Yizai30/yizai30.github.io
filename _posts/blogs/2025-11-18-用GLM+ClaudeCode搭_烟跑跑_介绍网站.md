---
title: 用GLM+Claude Code，快速搭一个游戏介绍网站！
tags: [GLM, Claude Code]
categories: [AI Agent]
---
## 1 环境配置
### 1.1 官方文档
阅读[官方文档](https://docs.bigmodel.cn/cn/coding-plan/tool/claude)，按照步骤操作。
### 1.2 实操
笔者在 Windows 上开发，已有 git 环境，那么只需要安装 node 环境即可。

创建工作目录 glm-agent ，在其中创建 `docker-compose.yml`，文件由 deepseek 生成，内容如下。
```yml
version: '3.8'

services:
  node-dev:
    image: node:22-alpine # 拉取的镜像名称
    container_name: node-dev # 创建的容器名称
    working_dir: /app
    volumes:
      - .:/app
      - /app/node_modules  # 防止主机 node_modules 覆盖容器内的 node_modules
    ports:
      - 9020:3000 # 将主机的 9020 端口映射到容器的 3000 端口
    environment:
      - NODE_ENV=development
    stdin_open: true
    tty: true
```
- 在工作目录下执行 `docker-compose up -d` 启动 node-dev 容器。
- 启动成功后，执行 `docker exec -it node-dev sh` 进入容器内部。
- 执行 `npm install -g @anthropic-ai/claude-code` 安装 claude code。
- 执行 `touch ~/.claude/settings.json` 创建配置文件，在 Windows 记事本中编辑官方给的配置，配置内容如下，在 `your_zhipu_api_key` 处填入自己的 api。
```json
{
    "env": {
        "ANTHROPIC_AUTH_TOKEN": "your_zhipu_api_key",
        "ANTHROPIC_BASE_URL": "https://open.bigmodel.cn/api/anthropic",
        "API_TIMEOUT_MS": "3000000",
        "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": 1
    }
}
```
- 然后复制配置内容到粘贴板，回到 docker 容器的终端。
- 输入 `cat > ~/.claude/settings.json << 'EOF'` 回车，并粘贴修改好的配置，回车，输入 `EOF`，回车，完成环境配置。


## 2 使用
输入 `claude` 启动 Claude Code。只需要在终端输入自然语言指令，agent 就会反复进行“感知→思考→行动→反馈”的步骤，直到完成目标。

{% if site.cdn %}
![感知→思考→行动→反馈](/images/2025-11-18-用GLM+ClaudeCode搭_烟跑跑_介绍网站/image-2.png){: w="700" h="400" .shadow }
_感知→思考→行动→反馈_
{% else %}
![感知→思考→行动→反馈](/assets/img/2025-11-18-用GLM+ClaudeCode搭_烟跑跑_介绍网站/image-2.png){: w="700" h="400" .shadow }
_感知→思考→行动→反馈_
{% endif %}

{% if site.cdn %}
![完成搭建网站的目标](/images/2025-11-18-用GLM+ClaudeCode搭_烟跑跑_介绍网站/image-3.png){: w="700" h="400" .shadow }
_完成搭建网站的目标_
{% else %}
![完成搭建网站的目标](/assets/img/2025-11-18-用GLM+ClaudeCode搭_烟跑跑_介绍网站/image-3.png){: w="700" h="400" .shadow }
_完成搭建网站的目标_
{% endif %}

## 3 结果
执行 `sh start.sh` 启动网站，在浏览器中查看效果。
{% if site.cdn %}
![网站效果](/images/2025-11-18-用GLM+ClaudeCode搭_烟跑跑_介绍网站/image-4.png){: w="700" h="400" .shadow }
_网站效果_
{% else %}
![网站效果](/assets/img/2025-11-18-用GLM+ClaudeCode搭_烟跑跑_介绍网站/image-4.png){: w="700" h="400" .shadow }
_网站效果_
{% endif %}

## 4  总结
本文详细记录了在 Windows 系统下使用 GLM+Claude Code 搭建网站的过程：从环境配置、Docker容器启动，到 Claude Code 安装使用，最终成功部署运行。通过自然语言指令驱动 AI 代理完成“感知-思考-行动”的循环，展示了 AI 辅助开发的完整工作流。