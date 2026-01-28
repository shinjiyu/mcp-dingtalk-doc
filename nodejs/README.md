# 钉钉文档 MCP 服务器

钉钉文档解析 MCP 服务器，让 AI 助手（Cursor/Claude）直接读取钉钉文档内容。

## 安装（可选）

**方式 1：全局安装（推荐）**
```bash
npm install -g mcp-dingtalk-doc
```

**方式 2：使用 npx（无需安装）**
无需安装，直接使用 `npx` 命令即可，首次使用会自动下载。

## 配置

编辑 Cursor 配置文件：

**Windows**: `%APPDATA%\Cursor\mcp.json`  
**Mac**: `~/Library/Application Support/Cursor/mcp.json`  
**Linux**: `~/.cursor/mcp.json`

### 如果已全局安装：
```json
{
  "mcpServers": {
    "dingtalk-doc": {
      "command": "mcp-dingtalk-doc"
    }
  }
}
```

### 如果使用 npx（无需安装）：

**Mac/Linux（推荐）：**
```json
{
  "mcpServers": {
    "dingtalk-doc": {
      "command": "npx",
      "args": ["-y", "mcp-dingtalk-doc"]
    }
  }
}
```

**Windows（npx 可能有问题，推荐使用全局安装）：**

如果一定要用 npx，可以尝试：
```json
{
  "mcpServers": {
    "dingtalk-doc": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "mcp-dingtalk-doc"]
    }
  }
}
```

> ⚠️ **Windows 用户注意**：
> - Windows 下 `npx` 在 MCP 配置中可能无法正常工作（Cursor 的已知问题）
> - **强烈推荐 Windows 用户使用全局安装方式**（更可靠）
> - 如果必须使用 npx，可以尝试 `cmd /c npx -y` 的方式，但可能仍有问题

## 使用

在 Cursor 中对 AI 说：

```
请帮我解析这个钉钉文档：
https://alidocs.dingtalk.com/i/nodes/xxx
```

## 自动登录

- **未登录时会自动弹窗让您登录**：当检测到需要登录时，会自动打开浏览器窗口
- **登录后关闭弹窗继续**：完成登录后，关闭浏览器窗口即可，程序会自动保存 Cookie 并继续执行

## 可用工具

### parse_document
解析文档并生成 HTML 文件

### get_html
快速获取 HTML 内容（不保存文件）
