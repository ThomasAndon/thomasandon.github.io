---
title: 2023_MARCH v1.0.0
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
code_clipboard: true
highlight_theme: darkula
headingLevel: 2
generator: "@tarslib/widdershins v4.0.17"

---

# 2023_MARCH

> v1.0.0

Base URLs:

# 中心（多元信息综合处理与辅助决策平台）/元

## POST 管理员登录

POST /cc/login

返回的data里有token，以后的操作记得放置在Authorization头里，格式："Bearer"+空格+token字符串

> Body 请求参数

```json
{
  "loginId": "string",
  "pw": "string"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» loginId|body|string| 是 |id|
|» pw|body|string| 是 |密码|

> 返回示例

> 200 Response

```json
{
  "code": 0,
  "msg": "string",
  "data": {
    "token": "string"
  }
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||200为成功， 400+ 为失败，msg内为失败的错误信息|
|» msg|string|true|none||返回码大于等于400以上会显示错误信息，可以展示给用户|
|» data|object|true|none||数据体，可以为一个大括号，也可以为一个数组|
|»» token|string|true|none|一个jwt，以后都要放在头里面访问|none|

# 中心（多元信息综合处理与辅助决策平台）/人员交互

## GET 查看所有人员状态

GET /cc/all_member_stat

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|Authorization|header|string| 否 |管理员token要带上|

> 返回示例

> 200 Response

```json
{
  "code": 0,
  "msg": "string",
  "data": [
    {
      "memberName": "string",
      "memberLoaction": "string",
      "memberLastUpdateTime": "string"
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» code|integer|true|none||200为成功， 400+ 为失败，msg内为失败的错误信息|
|» msg|string|true|none||返回码大于等于400以上会显示错误信息，可以展示给用户|
|» data|[[人员状态](#schema%e4%ba%ba%e5%91%98%e7%8a%b6%e6%80%81)]|true|none||数据体，可以为一个大括号，也可以为一个数组|

## GET 获取单个人员状态

GET /cc/member_stats

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|memberid|query|string| 是 |none|

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

# 中心（多元信息综合处理与辅助决策平台）/节点信息交互

## GET 获取节点包括传感器状态（SEE院拟定中）

GET /cc/node_with_sensors_stats

- 每个节点内有2个传感器，每个传感器能够定时监测光、声信号。
- 至于传感器如何传回数据，是否通过节点，SEE拟定中。

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

## POST 修改设备配置

POST /cc/device_setting

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

# 车辆信息/SLAM/PCD/ROS (BUAA)

## POST 车辆轨迹信息

POST /hero/trail

- 轨迹文件，待BUAA提供示例（是否和SLAM一起打包传输）

> Body 请求参数

```yaml
string

```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|string(binary)| 否 |none|

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

## POST SLAM数据回传

POST /hero/slam

- PCD点云文件上传（帧数据增量上传，上位机拼接）
- 具体文件格式、拼接方式待BUAA提供示例

> Body 请求参数

```yaml
string

```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|string(binary)| 否 |none|

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

# 节点（合并）/传感器信息

## POST 上传传感器数据

POST /sensor/update

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

# 人员终端

## POST 人员终端心跳数据

POST /pterm/heartbeat

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

# 数据模型

<h2 id="tocS_人员状态">人员状态</h2>

<a id="schema人员状态"></a>
<a id="schema_人员状态"></a>
<a id="tocS人员状态"></a>
<a id="tocs人员状态"></a>

```json
{
  "memberName": "string",
  "memberLoaction": "string",
  "memberLastUpdateTime": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|memberName|string|true|none||none|
|memberLoaction|string|true|none||none|
|memberLastUpdateTime|string|true|none||人员上次状态更新的时间|

<h2 id="tocS_CommonResp">CommonResp</h2>

<a id="schemacommonresp"></a>
<a id="schema_CommonResp"></a>
<a id="tocScommonresp"></a>
<a id="tocscommonresp"></a>

```json
{
  "code": 0,
  "msg": "string",
  "data": "string"
}

```

通用返回模型

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|code|integer|true|none||200为成功， 400+ 为失败，msg内为失败的错误信息|
|msg|string|true|none||返回码大于等于400以上会显示错误信息，可以展示给用户|
|data|string|true|none||none|

