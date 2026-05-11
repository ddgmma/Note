安装好 Node.js 后，最高频的命令就这几个（记住就够用了）：

## 🚀 最高频命令（必会）

| 命令 | 作用 | 使用频率 |
|------|------|----------|
| `node -v` | 查看 Node.js 版本 | ⭐⭐⭐⭐⭐ |
| `npm -v` | 查看 npm 版本 | ⭐⭐⭐⭐⭐ |
| `node 文件名.js` | 运行一个 JS 文件 | ⭐⭐⭐⭐⭐ |
| `npm init -y` | 快速初始化项目（生成 package.json） | ⭐⭐⭐⭐⭐ |
| `npm install 包名` | 安装第三方包（简写：`npm i 包名`） | ⭐⭐⭐⭐⭐ |
| `npm install` | 根据 package.json 安装所有依赖 | ⭐⭐⭐⭐ |
| `npm uninstall 包名` | 卸载包 | ⭐⭐⭐ |
| `npm run 脚本名` | 运行 package.json 里定义的脚本 | ⭐⭐⭐⭐ |

## 💡 日常使用场景示例

```bash
# 1. 确认是否装好了
node -v        # 输出 v20.x.x 之类的

# 2. 跑一个 JS 文件
node app.js

# 3. 新建项目
mkdir my-project
cd my-project
npm init -y    # 瞬间生成 package.json

# 4. 装依赖（装 express 为例）
npm i express

# 5. 装开发依赖
npm i -D nodemon   # -D 表示 devDependencies

# 6. 运行项目（前提 package.json 里配了 start 脚本）
npm start          # 等价于 npm run start
npm run dev        # 常用开发模式
```

**总结：** 平时 90% 的时间就在用 `node`、`npm i`、`npm run` 这三个命令。记这几个就够了。