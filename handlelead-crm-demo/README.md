# 门五金海外客户开发系统 Demo

这是一个中文为主的海外 B2B 客户开发 CRM 原型，用于 **304 不锈钢门窗把手** 工厂开发海外采购商。

## 当前 Demo 功能

- 中文数据看板首页
- 今日新增客户统计
- 待审核客户统计
- 已批准待发送统计
- 累计已发送统计
- 客户回复率展示
- 客户阶段漏斗
- 国家/地区分布
- 今日客户明细表
- 待处理任务提醒
- 开发邮件模板预览
- 客户回复分类示例
- 自动化运行日志

## 业务流程

1. 每天自动寻找 20 个新的海外潜在客户。
2. 系统检查历史客户和 Gmail 已发送记录，避免重复开发。
3. 新客户进入“待审核”状态。
4. 用户审核后，将客户状态改为“已批准”。
5. 系统只向“已批准”的客户逐封发送邮件。
6. 发送后状态改为“已发送”。
7. 系统定期检查 Gmail 收件箱。
8. 如果客户回复，系统分类为：需要目录、需要报价、需要样品、感兴趣、不感兴趣、不再联系。

## 产品定位

**China factory supplying 304 stainless steel door & window handles, OEM supported, door-to-door / DDP delivery available.**

## 联系信息

Jack  
Email: jack0010114@gmail.com  
WhatsApp: +86 15019858395

## 下一步开发建议

第一阶段建议先做 MVP：

- 前端页面：React / Next.js
- 数据库：Supabase 或 SQLite
- 邮箱：Gmail API
- 自动任务：Cron / GitHub Actions / Vercel Cron
- AI：用于客户匹配、邮件生成、回复分类
