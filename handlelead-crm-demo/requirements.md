# HandleLead CRM 开发需求文档

## 项目目标

开发一个中文为主的海外 B2B 客户开发管理系统，用于 304 不锈钢门窗把手工厂开发海外采购商。

用户每天只需要：

1. 打开系统查看今日客户名单。
2. 审核客户是否合适。
3. 点击批准。
4. 系统逐封发送邮件。
5. 系统检查 Gmail 是否有客户回复。
6. 系统把客户回复分类并生成跟进任务。

## 产品定位

- 产品：304 不锈钢门窗把手
- 服务：OEM、ODM、定制尺寸、表面处理、Logo、包装
- 物流：可根据目的地国家安排 door-to-door / DDP 到门物流
- 目标客户：门五金分销商、建筑五金供应商、门窗厂家、建材进口商、工程承包商、B2B 采购商

## 用户信息

- 姓名：Jack
- Email：jack0010114@gmail.com
- WhatsApp：+86 15019858395

## 核心页面

### 1. 数据总览 Dashboard

需要展示：

- 今日新增客户
- 待审核客户
- 已批准待发送
- 今日已发送
- 累计已发送
- 累计客户回复
- 回复率
- 待跟进客户
- 客户阶段漏斗
- 国家/地区分布
- 今日自动化日志

### 2. 今日客户名单

字段：

- 公司名称
- 国家/地区
- 网站
- 邮箱
- WhatsApp
- 客户类型
- 匹配原因
- 来源链接
- 匹配度评分
- 状态
- 下一步动作

### 3. 审核与发送

用户可以执行：

- 批准客户
- 拒绝客户
- 标记不再联系
- 编辑邮件内容
- 发送已批准邮件

发送规则：

- 只发送状态为“已批准”的客户
- 一封一封发送，不群发
- 每封之间有间隔，例如 90 秒
- 发送成功后状态改为“已发送”
- 记录发送时间
- 不允许同一邮箱重复发送

### 4. 客户回复

系统从 Gmail 检查客户回复，并分类：

- 需要目录
- 需要报价
- 需要样品
- 感兴趣
- 不感兴趣
- 找错人
- 不再联系

每条回复需要：

- 回复时间
- 回复摘要
- 客户意图
- 下一步建议
- 是否需要人工处理

### 5. 客户数据库

保存所有历史客户，避免重复开发。

## 客户状态

- 待审核
- 已批准
- 已发送
- 已回复
- 需要目录
- 需要报价
- 需要样品
- 感兴趣
- 不感兴趣
- 找错人
- 不再联系

## 数据表字段建议

```text
date
company_name
country
website
email
whatsapp
customer_type
reason_for_fit
source_url
match_score
email_subject
email_body
status
sent_time
reply_status
reply_time
reply_summary
next_action
notes
```

## 邮件模板

Subject: OEM 304 Stainless Steel Door & Window Handles

```text
Dear Purchasing Team,

We are a China factory supplying 304 stainless steel door and window handles, including pull handles, entrance handles, and related architectural hardware for residential, commercial, and project use.

We support OEM customization for size, finish, logo, and packaging. We can also arrange door-to-door logistics delivery / DDP shipping support when available, depending on the destination country.

May I send you our catalog and price list for your review?

Best regards,
Jack
Email: jack0010114@gmail.com
WhatsApp: +86 15019858395
```

## 技术建议

第一版 MVP：

- 前端：Next.js / React
- 数据库：SQLite 或 Supabase
- 邮箱：Gmail API
- 定时任务：Cron / GitHub Actions / Vercel Cron
- AI：用于客户匹配、开发信生成、客户回复分类

## 安全规则

- 不做完全盲发
- 必须由用户审核客户后才允许发送
- 不重复发送同一邮箱
- 不发送给不再联系客户
- 如果客户明确拒绝或要求停止联系，加入黑名单
- 不群发，不把多个客户放同一个收件人栏
