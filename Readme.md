# 天气预报网页前端实训项目
## 一、项目简介
本项目是单页天气预报应用，基于HTML5、CSS3、ES6 JavaScript开发，调用和风天气免费API实现城市天气查询，包含基础必做功能与两项加分拓展功能，适配移动端、桌面端响应式布局。

## 二、核心使用技术栈
1. HTML5：header/main/section 语义化标签搭建页面结构，规范文档层级
2. CSS3：Flex弹性布局 + 横向滚动Grid布局，媒体查询实现响应式适配
3. JavaScript ES6+：箭头函数、async/await异步请求、解构赋值、模板字符串
4. Fetch API：发送GET网络请求，调用第三方天气接口获取实时、预报数据
5. Web原生API：
   - Geolocation 定位API：获取设备经纬度，反向解析城市（加分功能4）
   - localStorage 本地存储API：持久保存用户搜索城市（加分功能5）
6. 第三方数据源：和风天气Web API，提供城市编码、实时气温、5日预报数据

## 三、功能实现说明 & 对应核心代码片段
### 功能1：城市搜索模块（必做）
功能描述：输入框接收城市名称，支持点击按钮、回车键两种查询方式；做非空输入校验，空白禁止请求。
核心代码逻辑：
```js
// 回车监听
cityInput.addEventListener('keydown', (e) => {
    if (e.key === 'Enter') handleSearch();
})
// 点击按钮查询
searchBtn.addEventListener('click', handleSearch);
// 输入校验
function handleSearch() {
    let cityVal = cityInput.value.trim();
    if (!cityVal) {
        alert("请输入有效城市名称，不能为空！");
        return;
    }
    localStorage.setItem("searchCity", cityVal);
    loadWeatherData(cityVal);
}
