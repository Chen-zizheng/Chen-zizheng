# 陈子政 · Chen Zizheng

**2027 届 · 计算机科学本科（海外）· 求职中**

目标岗位：**后端开发 / 测试开发 / 软件测试 / AI 应用开发**

现居匈牙利（米什科尔茨大学），中文母语，可全程线上面试；**2027 年 7 月可全职到岗**。

---

## 🧩 六个 clone 下来就能跑的项目

<table>
<tr>
<td width="50%" valign="top">

### 🎫 工单管理系统
**Java · Spring Boot 3.2 · MyBatis · H2 · JUnit 5**

建单 / 派单 / 状态流转 / 统计 / 分页筛选 7 个 REST 接口 + 一个网页看板，
3 张表 4 类索引。派单与状态变更走 `version` 乐观锁：

```sql
UPDATE ticket SET ... WHERE id = ? AND version = ? AND status = ?
```

32 线程并发抢派同一张单，实测 1 成功 31 冲突，无重复派单。
列表页固定 3 条 SQL（分页 + 批量查处理人 + count），用 MyBatis 拦截器在测试里
**断言 SQL 条数**防 N+1 回归。18 个接口用例，`mvn test` 全绿。

[→ ticket-service](https://github.com/Chen-zizheng/ticket-service)

</td>
<td width="50%" valign="top">

### 🚚 logpipe · TCP 日志采集器
**C++17 · STL · 多线程 · epoll / WSAPoll · CMake**

同一套源码，Linux 用 epoll、Windows 用 WSAPoll；
按行切分处理粘包 / 半包 / CRLF / 超长行。
有界队列 + 4 线程批量写盘（256 KiB/批）+ 按大小轮转，队列满时丢弃并计数、不阻塞 I/O。

实测（WSL2 Ubuntu，8 连接、96 B/行、持续 10 秒）：**186,560 行/s**、零丢弃；
同一份代码在 Windows 上 **777,461 行/s**。54 条断言覆盖切包与轮转边界，双平台通过。

[→ logpipe](https://github.com/Chen-zizheng/logpipe)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🔍 XSS 污点扫描器
**Python · 自写 JS 词法器 · LLM 兜底 · pytest**

自写 JS 词法器做污点分析：从 `location` / `cookie` / `localStorage` 追到
`innerHTML` / `document.write` / `eval`，输出带行号与传播路径的「已证实」结论；
大模型只负责「疑似」扩召回。纯静态、离线、同输入同输出，可直接当回归基线。

5 套人工标注语料共 119 条，6 个后端（关键词 / 污点 / 混合 / DeepSeek / 污点+模型 / Semgrep）
同台评测。留出集 F1 0.95——**但只有 9 个正样本，McNemar p=1.0，撑不起显著性，
这条我自己写在文档里**。129 个 pytest 用例，模型调用全部 monkeypatch 顶掉，CI 无需联网。

[→ xss-taint-scanner](https://github.com/Chen-zizheng/xss-taint-scanner)

</td>
<td width="50%" valign="top">

### 🎯 JobRadar 校招岗位雷达
**Python · FastAPI · Streamlit · 大模型 API**

抓取校招岗位 → 本地关键词粗筛 → 大模型结构化打分 → Streamlit 可视化筛选。
针对「Token 贵、跑一半就断」两个痛点，做公司粒度增量落盘与断点续跑（已评估部分不重复计费）；
另补 FastAPI 接口层（4 端点、X-API-Key 鉴权、未配密钥 fail-closed 返回 500）与 24 条契约测试。

[→ job-radar](https://github.com/Chen-zizheng/job-radar)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🎴 CardGame · 2D 卡牌 Roguelike
**Unity（团结引擎）· C# · ShaderLab / HLSL**

8 个场景的完整关卡循环：主菜单 → 选角 → 地图 → 篝火 → 战斗 → 奖励 → 商店 → 结算。
玩法逻辑用 C#，卡牌翻转、UI 流光、受击闪烁等表现用自写 Shader 完成。已发布 Windows x64 免安装构建。

[→ CardGame](https://github.com/Chen-zizheng/CardGame)

</td>
<td width="50%" valign="top">

### 🕹️ PixActionGame · 像素横版动作
**Unity · C# · ShaderLab / HLSL**

移动、跳跃、冲刺、攻击的输入响应与动作状态切换，伤害结算与 UI 反馈联动。
着色器代码占全仓 69%（GitHub Languages 统计）。

[→ PixActionGame](https://github.com/Chen-zizheng/PixActionGame)

</td>
</tr>
</table>

---

## 🛠 技术栈

```text
语言        Java · C/C++ · Python · C# · JavaScript · SQL
后端        Spring Boot · MyBatis · FastAPI · H2 · REST / JSON · 乐观锁与并发控制
系统        Linux（epoll、g++、CMake、GDB、shell）· 多线程 · 有界队列 · 批量 I/O
测试        pytest（fixture / monkeypatch）· JUnit 5 + MockMvc · 用例设计（等价类/边界值/场景法）· GitHub Actions
AI 应用     提示词结构化约束 · JSON 容错解析 · 输出校验 · DeepSeek / OpenAI SDK
游戏        Unity（团结引擎）· ShaderLab / HLSL · UGUI · DOTween
工程        Git / GitHub（分支、Issue、Actions）· Docker（基础）· Maven / CMake
```

---

## 📌 关于我

- **2027 年 7 月毕业**，2027.07 可全职到岗；现阶段可全程线上面试。
- 上面的数字都是自己跑出来的；跑不满意的结论我会写进 README 的「已知限制」，而不是删掉。
- 相信开源与 AI 能改变一些事情，也这么用它们。

## 📫 联系

- 邮箱：`chenzizheng2026@163.com`
- 微信：`18133455482`
