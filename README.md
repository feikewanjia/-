# 数智练静态官网演示版

这是“数智练”网站的静态官网演示版本，适合直接部署到 Vercel 给客户预览产品界面和核心交互。

当前版本不接入 OpenAI API，不需要后端接口，不需要数据库，也不需要配置 `OPENAI_API_KEY`。页面中的“AI生成专项训练”按钮只会在浏览器前端生成 mock 预览内容，用于演示产品效果。

## 本地运行

```bash
npm install
npm run dev
```

然后打开：

```text
http://localhost:3000
```

## 构建静态文件

```bash
npm run build
```

构建完成后，静态文件会输出到 `dist/` 目录。Vercel 会发布这个目录。

## 部署到 Vercel

1. 将本项目上传到 GitHub、GitLab 或 Bitbucket。
2. 在 Vercel 新建项目并选择该仓库。
3. Vercel 会读取 `vercel.json`：
   - Build Command: `npm run build`
   - Output Directory: `dist`
4. 不需要添加任何环境变量。
5. 点击 Deploy 即可完成静态官网部署。

也可以使用 Vercel CLI：

```bash
npm run build
vercel --prod
```

## 当前 mock 功能

- 教材版本、年级、资料类型、知识点、输出形式选择。
- 点击“AI生成专项训练”后，右侧生成模拟专项训练资料。
- “重新生成”会基于当前表单再次生成 mock 预览。
- “打印资料”可以打印当前预览内容。
- 图片资料模式当前也是演示入口，不调用真实图片生成接口。

## 后续扩展真实 AI 生成功能

后续如果要接入真实 AI 生成，建议新增独立后端接口或 Vercel Serverless Function，例如：

- 新增 `/api/generate-material` 或 `/api/generate-image`。
- 在服务端读取 `OPENAI_API_KEY`。
- 前端提交表单参数到服务端接口。
- 服务端调用 OpenAI API 后返回结构化资料或图片结果。
- 前端继续复用当前右侧预览区域展示真实生成内容。

在接入真实服务前，请不要把 API Key 写入前端页面或静态文件中。
