# 淘宝热词

API认证需要的APP Code请在阿里云API市场申请: https://market.aliyun.com/apimarket/detail/cmapi022144

## 什么是云市场API MCP服务

阿里云云市场是生态伙伴的交易服务平台，我们致力于为合作伙伴提供覆盖上云、商业化和售卖的全链路服务，帮助客户高效获取、部署和管理优质生态产品。云市场的API服务涵盖以下几个类目：应用开发、身份验证与金融、车辆交通与物流、企业服务、短信与运营商、AI应用与OCR、生活服务。
云市场API依托Higress提供MCP服务，您只需在云市场完成订阅并获取AppCode，通过Higress MCP Server进行配置，即可无缝集成云市场API服务。

## 如何在使用云市场API MCP服务

1. 进入API详情页，订阅该API。您可以优先使用免费试用。
2. 前往云市场用户控制台，使用阿里云账号登陆后查看已订阅API服务的AppCode，并配置到Higress MCP Server的配置中。注意：在阿里云市场订阅API服务后，您将获得AppCode。对于您订阅的所有API服务，此AppCode是相同的，您只需使用这一个AppCode即可访问所有已订阅的API服务。
3. 云市场用户控制台会实时展示已订阅的预付费API服务的可用额度，如您免费试用额度已用完，您可以选择重新订阅。

# MCP服务器配置文档

## 功能简介

`taobao-hot-words`服务器主要服务于电商平台上的商家及运营者，通过提供淘宝站内搜索关键词排名查询的功能来辅助决策。它能够根据用户的实时搜索频率来处理并分析数据，从而让商家能够掌握特定关键词在市场中的表现情况，包括但不限于其排名、分布特征等重要信息。此外，还支持用户指定任意关键词，并返回该词及其相关联度最高的前10个关键词列表，按相关性从高到低排序展示结果。此功能对于优化商品标题、提升搜索可见度等方面具有重要作用。

## 工具简介

### 淘宝热词

**用途**：作为一款专注于淘宝平台内部搜索行为分析的工具，“淘宝热词”能够帮助商家或开发者了解特定词汇在淘宝网上的流行程度与趋势变化。通过分析这些数据，用户可以洞察消费者兴趣点的变化规律，为产品推广策略调整提供依据。

**使用场景**：
- 当需要评估某个新产品名称或者营销活动口号是否足够吸引目标客户群时；
- 在制定SEO（搜索引擎优化）计划之前，希望获取更多关于潜在热门词汇的信息；
- 希望定期监控某些关键业务术语在市场上的表现如何，以便及时作出反应；
- 寻找灵感以创造新的广告标语或改善现有文案的效果。

**参数说明**：
- `key` (必填)：用户想要查询的具体关键词，类型为字符串。

**请求模板**：
- **URL**: `http://tbhot.market.alicloudapi.com/tbhot10`
- **方法**: GET
- **头部信息**:
  - `Authorization`: 使用APP Code进行身份验证。
  - `X-Ca-Nonce`: 用于防止重放攻击的安全令牌，值为随机生成的UUID。

**响应结构**:
- `goodsList`: 包含了与查询关键词相关的商品列表，数组形式存储。
  - `goodsList[]`: 其中每个元素都是一个字符串，代表单个商品条目。
- `key`: 显示最初提交给API的实际查询关键字。
- `status`: 表示请求状态的代码。
- `time`: 记录了API响应的时间戳。

以上即为`taobao-hot-words`服务器的基本介绍及其核心工具“淘宝热词”的详细说明。希望这份指南能为您带来帮助！
