<div align="center">

# 陈子政 · Chen Zizheng

**Java · C / C++ · Python · SQL**

2027 届 · 米什科尔茨大学 计算机科学 本科

</div>

---

## 项目

<table>
<tr>
<td width="50%" valign="top">

### 🎫 工单管理系统

`Java 17` · `Spring Boot 3.2` · `MyBatis` · `H2` · `JUnit 5`

建单、派单、状态流转、统计、分页筛选 7 个 REST 接口，加一个不需要构建的网页看板，3 张表、4 类索引。

派单和状态变更共用一个 `version` 字段，一次 UPDATE 同时校验。32 个线程抢派同一张单，1 个成功、31 个收到 409；代价是状态变更会让并发派单失败，客户端要重试一次。

<sub>[→ ticket-service](https://github.com/Chen-zizheng/ticket-service)</sub>

</td>
<td width="50%" valign="top">

### 🚚 logpipe · TCP 日志采集器

`C++17` · `epoll / WSAPoll` · `多线程` · `CMake`

Linux 走 epoll、Windows 走 WSAPoll，两套反应堆共用一份按行切分的解析逻辑：粘包、半包、CRLF、超长行都在这里处理。有界队列接 4 个写盘线程，256 KiB 一批。

WSL2 上 2,172,960 行、186,560 行/s、零丢弃，同一份代码在 Windows 上 777,461 行/s。每批 flush 让 Linux 掉 3.6%，换来 `tail -f` 实时可见。

<sub>[→ logpipe](https://github.com/Chen-zizheng/logpipe)</sub>

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🔍 XSS 污点扫描器

`Python` · `自写 JS 词法器` · `LLM 兜底` · `pytest`

从 `location` / `cookie` / `localStorage` 追到 `innerHTML` / `document.write` / `eval`，输出带行号和传播路径的结论。大模型只判「疑似」、用来补召回，因为同一个输入它两次运行能差出 0.12 F1。

留出集 F1 0.95，但只有 9 个正样本，McNemar p=1.0——这个数撑不起「显著」，文档里写的就是不算数。129 个 pytest 用例，行覆盖 81%。

<sub>[→ xss-taint-scanner](https://github.com/Chen-zizheng/xss-taint-scanner)</sub>

</td>
<td width="50%" valign="top">

### 🎯 JobRadar · 校招岗位雷达

`Python` · `FastAPI` · `Streamlit` · `DeepSeek`

抓取岗位 → 本地关键词粗筛 → 模型按简历打分 → Streamlit 上筛。评估按公司粒度落盘，中断后重跑跳过已评估的公司，不重复花 Token。

分页越界返回 200 加空列表，不是 404，因为「这个条件下没有岗位」不算错误。接口层 4 个端点、X-API-Key 鉴权、没配密钥时 fail-closed 返回 500。

<sub>[→ job-radar](https://github.com/Chen-zizheng/job-radar)</sub>

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🎴 CardGame · 2D 卡牌 Roguelike

`Unity（团结引擎）` · `C#` · `ShaderLab / HLSL`

8 个场景的关卡循环：主菜单、选角、地图、篝火、战斗、奖励、商店、失败结算。玩法逻辑用 C#，卡牌翻转、UI 流光、标题呼吸、受击闪色由 DOTween 与 Image.color 插值驱动，工程里的 shader 只有 TextMesh Pro 包自带的那些。

<sub>[→ CardGame](https://github.com/Chen-zizheng/CardGame) · [Windows x64 包](https://github.com/Chen-zizheng/CardGame/releases)</sub>

</td>
<td width="50%" valign="top">

### 🕹️ PixActionGame · 像素横版动作

`Unity` · `C#` · `ShaderLab / HLSL`

移动、跳跃、冲刺、攻击的输入响应与动作状态切换，伤害结算与 UI 反馈联动。16 个 C# 脚本共 1,269 行，另有一个 71 行的受击闪红 shader。

仓库里其余 17 个 shader 是 TextMesh Pro 包自带的，占全仓 shader 行数 97%。

<sub>[→ PixActionGame](https://github.com/Chen-zizheng/PixActionGame)</sub>

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 📊 电商销售 BI 仓库

`MySQL 8.4` · `pandas` · `SQLAlchemy` · `FastAPI` · `SVG 看板`

6 张源表建成 1 事实 6 维：30 家门店、2,000 个 SKU、300,006 单、750,530 行明细。12 条质量规则跑 11.3 秒，7 条脏数据按 R1–R7 各拦 1 条，源仓对账 300,006 单零差异。

增量装载按 `updated_at` 水位线。MySQL 的 DATETIME 默认只到秒，同一秒写入的行跟水位线撞平被漏掉，改成 `DATETIME(6)` 才不丢。看板 6 个 KPI 加 8 个面板，行级权限按接口传入的身份过滤。

<sub>[→ ecom-bi-warehouse](https://github.com/Chen-zizheng/ecom-bi-warehouse)</sub>

</td>
<td width="50%" valign="top">

### 📈 用户漏斗与留存

`MySQL 8.4` · `pandas` · `matplotlib` · `FastAPI`

60,000 名用户、390,954 条埋点、147,161 个会话：浏览到支付留下 5.9%，加购那一步只剩 25.6%；微信加购到支付 30.6%，联盟 13.7%。

漏斗按会话聚合，不按人——按人会把「今天看、明天买」并成一次转化。cohort 留存 D1 34.3%、D7 15.7%、D30 5.2%，首末两头不满整周的 cohort 剔掉。12 张图拼成 6 页 A4 HTML，打印直接出 PDF。

<sub>[→ user-funnel-retention](https://github.com/Chen-zizheng/user-funnel-retention)</sub>

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🧪 canfault · CAN 故障注入与模糊测试

`Python` · `python-can` · `vcan` · `pytest`

6 类故障注入（丢帧、重复、DLC 篡改、信号越界、负载拉高、时序漂移）都是纯函数，同一份 384 帧种子能复现每一类；被测 ECU 也自己写，崩溃才追得下去。

vcan0 上 20 秒发 57,860 帧、2,893 帧/s，12,877 次崩溃去重成 12 个缺陷——去重键把报文里的数字抹平，同一条 DLC 规则才不会被报成十几种。

<sub>[→ canfault](https://github.com/Chen-zizheng/canfault)</sub>

</td>
<td width="50%" valign="top">

### 🚦 pytest-gate · 用例分级 / 重跑 / 门禁

`Python` · `pytest` · `pytester`

150 行插件：`--level` 分级、`--gate-reruns` 在 protocol 层整轮重跑、`--gate-report` 出机器可读汇总、`--gate-max-fail` 超阈值用退出码 2。

在 canfault 上冒烟 22 条 0.22 秒、全量 26 条 3.46 秒，慢的 4 条吃掉 94% 的时间。

<sub>[→ pytest-gate](https://github.com/Chen-zizheng/pytest-gate)</sub>

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🤖 robotlink · 机器人联调与故障注入

`Python` · `TCP 帧协议` · `状态机` · `故障注入`

16 字节头加 CRC16 的帧协议，流式解析器吃半包和粘包；本体是 BOOT/SELF_TEST/IDLE/RUNNING/ESTOP/FAULT 状态机，急停插在所有状态检查之前，seq 重复包直接回 dup、不二次启动任务。

客户端超时用同一个 seq 重发。中间那个 TCP 代理能丢包、重复、乱序、按 MTU 切片、到点断连。五种链路各 20 轮，95 轮一次通过，5 次超时全部按 query 收尾回到 IDLE；30 秒长稳 RSS 涨 0.11 MB、线程停在 7。20 条 pytest。

<sub>[→ robotlink](https://github.com/Chen-zizheng/robotlink)</sub>

</td>
<td width="50%" valign="top"></td>
</tr>
</table>

---

## 技术栈

| | |
| :-- | :-- |
| **语言** | `Java` `C/C++` `Python` `C#` `JavaScript` `SQL` |
| **后端** | `Spring Boot` `MyBatis` `FastAPI` `H2` `REST / JSON` `乐观锁` |
| **数据** | `MySQL 星型建模` `窗口函数 / CTE` `updated_at 增量装载` `12 条质量规则` `pandas` `matplotlib` |
| **系统** | `Linux / epoll` `多线程` `有界队列` `批量 I/O` `CAN / vcan` `CMake` `GDB` |
| **测试** | `pytest` `写 pytest 插件` `JUnit 5 + MockMvc` `等价类 / 边界值 / 场景法` `GitHub Actions` `丢包 / 重复注入` |
| **AI** | `提示词结构化约束` `JSON 降级解析` `输出校验` `DeepSeek / OpenAI SDK` |
| **游戏** | `Unity（团结引擎）` `ShaderLab / HLSL` `UGUI` `DOTween` |
| **工程** | `Git / GitHub` `Maven` `CMake` `Docker（了解）` |

---

<div align="center">

**联系方式** · chenzizheng2026@163.com · 微信 18133455482

</div>
