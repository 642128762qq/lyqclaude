# 法律知识库

## 简介
本文档用于沉淀琪琪在合同审核过程中学习到的审查技巧、提炼的关键词以及核实过的新法规。
每次审核结束后，相关学习成果将追加写入本文档。
琪琪在每次审核前会先读取本文档，不断精进合同审核能力。

---

## 合同分类与典型合同类型（民法典）

### 典型合同类型
- 买卖合同（第九章）
- 供用电、水、气、热力合同（第十章）
- 赠与合同（第十一章）
- 借款合同（第十二章）
- 保证合同（第十三章）
- 租赁合同（第十四章）
- 融资租赁合同（第十五章）
- 保理合同（第十六章）
- 承揽合同（第十七章）
- 建设工程合同（第十八章）
- 运输合同（第十九章）
- 技术合同（第二十章）
- 保管合同（第二十一章）
- 仓储合同（第二十二章）
- 委托合同（第二十三章）
- 物业服务合同（第二十四章）
- 行纪合同（第二十五章）
- 中介合同（第二十六章）
- 合伙合同（第二十七章）

### 非典型合同
- 需根据核心权利义务特征进行识别
- 提炼核心关键词进行分析

---

## 沉淀学习记录

### 2026-05-17 项目设计合同（承揽合同）审核

**合同类型**：承揽合同（产品设计）- 《民法典》第十一章

**关键词提炼**：
- 产品设计合同、项目制、知识产权归属、违约金标准、管辖权约定

**审查技巧学习**：
1. 知识产权归属条款：注意"除署名权外"等限制性表述，应确保委托方完整取得全部IP权利
2. 违约金条款：每日1%明显过高，应参照每日万分之五，上限20%
3. 管辖权条款：涉及境外主体时，"甲方所在地"表述模糊，应明确约定具体法院
4. 定作人协助义务：需规范甲方提供资料的时限和通知机制

**核实的新法规**：
- 《民法典》第585条（违约金过高可申请减少）
- 《民法典》第787条（承揽合同知识产权归属）
- 《民法典》第780条（定作人协助义务）
- 《民事诉讼法》第35条（协议管辖）
- 《电子签名法》第3条（电子签名效力）

**风险分布规律**：
- 高危：知识产权归属、违约金畸高、管辖权模糊、甲方责任失控
- 中危：交付物定义不清、税费未明确、违约金标准不统一
- 低危：电子签名效力

---

### 审核输出规范（基于测试优化）

**输出格式核心要求**：
1. 每项风险必须包含三部分：原条款引用 → 具体修改建议 → 法律依据
2. 修改建议必须具体到可采用的措辞，不能只写风险提示
3. 法律依据必须引用具体条文，不能只写"违反法律规定"

**飞书发送规范**：
1. 先获取最新 token，再发送消息
2. 长消息可分多条发送（每条不超过2000字）
3. 发送后验证返回的 content 字段包含正确中文

---

### 2026-05-17 联网学习：承揽合同起草审查要点（法天使）

**学习来源**：搜狗微信搜索 - 《以三观分析法，梳理「承揽合同」起草审查的15个要点》

**核心学习要点**：
1. **承揽与建设工程合同大不相同**：建设工程受《建筑法》调整，适用专门法规；一般承揽合同参照《民法典》合同编规定
2. **涉外承揽可约定外国法律**：非涉外承揽必须适用中国法律，不能约定境外法院仲裁
3. **定牌加工/OEM属于混合型合同**：以承揽合同为主，含商标许可因素，需综合处理
4. **知识产权归"需要重复利用"的一方**：一般归定作人所有
5. **承揽人需具备相应资质**：无资质可能导致合同无效（严重影响公共利益时）
6. **留置权是法定权利**：合同中可约定"排除留置权"，但实务中作用有限
7. **定金模式vs违约金模式**：定金模式下损失大于定金可要求赔偿全部损失

**新增法规核实**：
- 《民法典》第1193条：定作人对选任有过错的，承担相应责任
- 《合同编》第505条：超越经营范围不影响合同效力
- 《医疗器械生产监督管理办法》：部分承揽涉及备案程序

---

### 2026-05-17 测试经验总结

**本次测试验证成功的功能**：
1. ✅ Word文档(.docx)读取 - 使用unzip命令提取文本内容
2. ✅ 合同结构化分析 - 识别条款、提炼风险点
3. ✅ 搜狗微信联网检索 - 通过Playwright访问weixin.sogou.com
4. ✅ 飞书消息推送 - Node.js发送中文内容
5. ✅ 知识库沉淀 - 审核后将学习成果写入legal_knowledge_base.md

**本次测试发现的问题及解决方案**：

| 问题 | 原因 | 解决方案 |
|---|---|---|
| 飞书发送失败（code=99991663） | Token过期 | 每次发送前必须获取新token |
| 飞书发送失败（code=230002） | 机器人不在群中 | 将应用机器人添加到群聊 |
| 中文乱码 | 使用curl发送 | 改用Node.js的https模块发送 |
| 长消息发送失败 | 消息过长 | 分多条发送，每条不超过2000字 |
| docx文件无法读取 | 直接读取二进制 | 使用unzip -p提取XML再解析 |

**飞书推送关键代码模式**：
```javascript
const https = require('https');
// 1. 获取token
const getToken = () => new Promise((resolve, reject) => {
  const req = https.request({
    hostname: 'open.feishu.cn',
    path: '/open-apis/auth/v3/tenant_access_token/internal',
    method: 'POST',
    headers: {'Content-Type': 'application/json'}
  }, res => {
    let body = '';
    res.on('data', chunk => body += chunk);
    res.on('end', () => resolve(JSON.parse(body).tenant_access_token));
  });
  req.write(JSON.stringify({app_id: 'cli_xxx', app_secret: 'vhx'}));
  req.end();
});

// 2. 发送消息
const sendMsg = (token, text) => new Promise((resolve, reject) => {
  const data = JSON.stringify({
    receive_id: 'oc_xxx',
    msg_type: 'text',
    content: JSON.stringify({text: text})
  });
  const req = https.request({
    hostname: 'open.feishu.cn',
    path: '/open-apis/im/v1/messages?receive_id_type=chat_id',
    method: 'POST',
    headers: {
      'Authorization': 'Bearer ' + token,
      'Content-Type': 'application/json; charset=utf-8',
      'Content-Length': Buffer.byteLength(data)
    }
  }, res => {
    let body = '';
    res.on('data', chunk => body += chunk);
    res.on('end', () => {
      const json = JSON.parse(body);
      if (json.code === 0) resolve('发送成功');
      else reject('失败: code=' + json.code);
    });
  });
  req.write(data);
  req.end();
});

// 3. 使用
getToken().then(token => sendMsg(token, '消息内容'));
```

**Playwright MCP使用要点**：
- 导航：`mcp__playwright__browser_navigate({url: '...'})`
- 截图：`mcp__playwright__browser_take_screenshot({type: 'png'})`
- 快照：`mcp__playwright__browser_snapshot({depth: 3})`
- 评估JS：`mcp__playwright__browser_evaluate({function: '() => { ... }'})`
- 关闭：`mcp__playwright__browser_close()`

**审查报告输出标准格式**：
```
【引用原合同条款】
[条款编号]：[原文内容]

【具体的修改建议】
修改为："[新条款内容]"

【事实与法律依据】
[法规名称]第X条：[具体规定] - [适用说明]
---
风险等级：🔴高危
```