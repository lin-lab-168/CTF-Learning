# XSS 反射型学习笔记

## 日期
2026年4月1日

## 环境
- DVWA (Low难度)
- 浏览器

## 操作步骤

### 1. 基础测试
在 XSS (Reflected) 输入框中输入：```html 
<script>alert(1)</script>
点击 Submit，页面弹出对话框，显示 1

### 2. 另一种测试
再输入：
<img src=x onerror=alert(1)>
同样弹窗

### 原理
输入的 HTML/JS 代码被原样放到页面中，浏览器解析时执行了这段代码。

### 核心收获
XSS 是在浏览器端执行 JS 代码
反射型 XSS 的代码通过 URL 参数或表单提交“反射”回来
<script>alert(1)</script> 是最简单的测试 payload

## 与 SQL 注入对比
SQL 注入：攻击目标是数据库，恶意代码在服务器上执行。我输入的是 `1' or '1'='1' -- `，结果是返回了所有用户数据。
XSS：攻击目标是浏览器（用户），恶意代码在受害者浏览器中执行。我输入的是 `<script>alert(1)</script>`，结果是弹出了一个对话框。
核心区别：SQL 注入打服务器，XSS 打用户。