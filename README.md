# 陈子政 · Chen Zizheng

2027 届，米什科尔茨大学计算机科学本科（英文授课）。找后端、测试开发、AI 应用开发的岗位，2027 年 7 月能到岗。

下面六个仓库是我自己写的，clone 下来按 README 能跑。文里的数字都是本机跑出来的，测不动的部分写在各自仓库的「已知限制」里。

## 工单管理系统 · Java

Spring Boot 3.2 + MyBatis + H2：建单、派单、状态流转、统计、分页筛选 7 个 REST 接口，加一个不需要构建的网页看板，3 张表、4 类索引。

派单和状态变更共用一个 `version` 字段，一次 UPDATE 同时校验状态和版本。32 个线程抢派同一张单，1 个成功、31 个收到 409；代价是状态变更会让并发派单失败，客户端要重试一次。列表页固定 3 条 SQL，测试里挂 MyBatis 拦截器断言 SQL 条数，N+1 一旦回来用例就红。18 个接口用例，`mvn test` 全绿。

[→ ticket-service](https://github.com/Chen-zizheng/ticket-service)

## logpipe · TCP 日志采集器 · C++17

同一份源码，Linux 走 epoll、Windows 走 WSAPoll；按行切分，处理粘包、半包、CRLF 和超长行。有界队列接 4 个写盘线程，256 KiB 一批，按大小轮转。

WSL2 上 8 条连接、96 B/行、压 10 秒：2,172,960 行 / 201 MiB，186,560 行/s，零丢弃；同一份代码在 Windows 上是 777,461 行/s。每批写完 flush 让 Linux 从 193,469 掉到 186,560（约 3.6%），换来 `tail -f` 实时可见——不 flush 时 app.log 一直是 0 字节。54 条断言覆盖切包和轮转边界。

[→ logpipe](https://github.com/Chen-zizheng/logpipe)

## XSS 污点扫描器 · Python

自写 JS 词法器做污点分析：从 `location` / `cookie` / `localStorage` / `postMessage` 追到 `innerHTML` / `document.write` / `eval`，输出带行号和传播路径的结论。大模型只判「疑似」、用来补召回，因为同一个输入它两次运行能差出 0.12 F1。

5 套人工标注语料 119 条，6 个后端同台评测（关键词 / 污点 / 混合 / DeepSeek / 污点+模型 / Semgrep）。留出集 F1 0.95，但只有 9 个正样本，McNemar p=1.0——这个数撑不起「显著」，文档里写的就是不算数。仓库 129 个 pytest 用例、行覆盖 81%，其中 34 个盯字段契约与解析降级；模型调用全部 monkeypatch 顶掉，CI 不联网。

[→ xss-taint-scanner](https://github.com/Chen-zizheng/xss-taint-scanner)

## JobRadar · 校招岗位雷达 · Python

抓取岗位 → 本地关键词粗筛 → 模型按简历打分 → Streamlit 上按方向、最低分、是否建议投递筛。评估按公司粒度落盘，Ctrl+C 或断网后重跑跳过已评估的公司，不重复花 Token；分页越界返回 200 加空列表，不是 404，因为「这个条件下没有岗位」不算错误。

另补了 FastAPI 接口层：4 个端点、X-API-Key 鉴权、服务端没配密钥时 fail-closed 返回 500，24 条契约测试。今年秋招用它筛过 150 家。

[→ job-radar](https://github.com/Chen-zizheng/job-radar)

## CardGame · 2D 卡牌 Roguelike · Unity

8 个场景的关卡循环：主菜单、选角、地图、篝火、战斗、奖励、商店、失败结算。玩法逻辑用 C#，卡牌翻转、UI 流光、标题呼吸、受击闪烁四个动效用自写 ShaderLab / HLSL。Windows x64 免安装包发在 Releases，README 写清场景入口、引擎版本和已知局限。

[→ CardGame](https://github.com/Chen-zizheng/CardGame)

## PixActionGame · 像素横版动作 · Unity

移动、跳跃、冲刺、攻击的输入响应与动作状态切换，伤害结算与 UI 反馈联动。ShaderLab + HLSL 占全仓代码 69%（GitHub Languages 统计）。

[→ PixActionGame](https://github.com/Chen-zizheng/PixActionGame)

## 技术栈

```text
语言    Java · C/C++ · Python · C# · JavaScript · SQL
后端    Spring Boot · MyBatis · FastAPI · H2 · REST / JSON · 乐观锁
系统    Linux（epoll、g++、CMake、GDB、shell）· 多线程 · 有界队列 · 批量 I/O
测试    pytest（fixture / monkeypatch）· JUnit 5 + MockMvc · 等价类 / 边界值 / 场景法 · GitHub Actions
AI     提示词结构化约束 · JSON 降级解析 · 输出校验 · DeepSeek / OpenAI SDK
游戏    Unity（团结引擎）· ShaderLab / HLSL · UGUI · DOTween
工程    Git / GitHub（分支、Issue、Actions）· Maven / CMake · Docker（了解）
```

## 联系

邮箱 chenzizheng2026@163.com ｜ 微信 18133455482 ｜ [github.com/Chen-zizheng](https://github.com/Chen-zizheng)
