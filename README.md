<div align="center">

# 陈子政 · Chen Zizheng

**Java · C / C++ · Python**

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

同一份源码，Linux 走 epoll、Windows 走 WSAPoll；按行切分，处理粘包、半包、CRLF 和超长行。有界队列接 4 个写盘线程，256 KiB 一批。

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

8 个场景的关卡循环：主菜单、选角、地图、篝火、战斗、奖励、商店、失败结算。玩法逻辑用 C#，卡牌翻转、UI 流光、标题呼吸、受击闪色由 DOTween 与 Image.color 插值驱动，没有写 shader。

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
</table>

---

## 技术栈

| | |
| :-- | :-- |
| **语言** | `Java` `C/C++` `Python` `C#` `JavaScript` `SQL` |
| **后端** | `Spring Boot` `MyBatis` `FastAPI` `H2` `REST / JSON` `乐观锁` |
| **系统** | `Linux / epoll` `多线程` `有界队列` `批量 I/O` `CMake` `GDB` |
| **测试** | `pytest` `JUnit 5 + MockMvc` `等价类 / 边界值 / 场景法` `GitHub Actions` |
| **AI** | `提示词结构化约束` `JSON 降级解析` `输出校验` `DeepSeek / OpenAI SDK` |
| **游戏** | `Unity（团结引擎）` `ShaderLab / HLSL` `UGUI` `DOTween` |
| **工程** | `Git / GitHub` `Maven` `CMake` `Docker（了解）` |

---

<div align="center">

**联系方式** · chenzizheng2026@163.com · 微信 18133455482

</div>
