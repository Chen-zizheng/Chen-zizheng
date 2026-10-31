# 陈子政 · Chen Zizheng

**2027 届 · 计算机科学本科（海外） · 求职中**

目标岗位：**测试开发 / 自动化测试 / AI 应用开发 / 游戏客户端（Unity）**

我习惯用「公开、可克隆、文档齐全、能跑起来」的仓库交付作品——
作品的价值只有被人真正打开过才算兑现。

---

## 🧪 四个能打开就能跑的作品

<table>
<tr>
<td width="50%" valign="top">

### 🔍 XSS 污点扫描器
**Python · 自写 JS 词法器 · LLM 兜底 · pytest · GitHub Actions**

自写 JS 词法器做污点分析：从 `location` / `cookie` / `localStorage` / `postMessage`
追到 `innerHTML` / `document.write` / `eval`，输出带行号与传播路径的「已证实」结论；
大模型只负责「疑似」，扩召回。纯静态、离线、同输入同输出，可直接当回归基线。

5 套人工标注语料共 119 条，**留出集在代码冻结之后才写**；6 个后端（关键词 / 污点 /
混合 / DeepSeek / 污点+模型 / Semgrep）同台评测。留出集 F1 0.95——**但只有 9 个正样本，
McNemar p=1.0，撑不起显著性，这条我自己写在文档里。**

**129 个 pytest 用例**（7.9s）、行覆盖 81%；模型调用全部 monkeypatch 顶掉，
CI 无需联网、不耗额度。PyInstaller 打成 14.3 MB 免安装包。

[→ xss-taint-scanner](https://github.com/Chen-zizheng/xss-taint-scanner)

</td>
<td width="50%" valign="top">

### 🎯 JobRadar 校招岗位雷达
**Python · Streamlit · LLM**

抓取校招岗位 → 本地关键词粗筛 → 大模型结构化打分 → Streamlit 可视化筛选。
针对「Token 贵、跑一半就断」两个痛点，做了公司粒度增量落盘与断点续跑不重复计费；
另补 FastAPI 接口层（4 端点）与 24 条契约测试。

被用来把 150 家海投变成有依据的筛选。

[→ job-radar](https://github.com/Chen-zizheng/job-radar)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🎴 CardGame · 2D 卡牌 Roguelike
**Unity（团结引擎）· C# · ShaderLab / HLSL**

8 个场景的完整关卡循环：主菜单 → 选角色 → 地图 → 战斗 → 奖励 → 篝火/商店。
玩法逻辑用 C#，卡牌翻转、UI 流光、受击闪烁等表现用自写 Shader 完成。

[→ CardGame](https://github.com/Chen-zizheng/CardGame)

</td>
<td width="50%" valign="top">

### 🕹️ PixActionGame · 像素横版动作
**Unity · C# · ShaderLab / HLSL**

移动、跳跃、冲刺、攻击的输入响应与动作状态切换，
伤害结算与 UI 反馈联动。着色器代码占全仓 69%（GitHub Languages 统计）。

[→ PixActionGame](https://github.com/Chen-zizheng/PixActionGame)

</td>
</tr>
</table>

---

## 🛠 技术栈

```text
语言        Python · C# · JavaScript · SQL
测试        pytest · 用例设计（等价类/边界值/场景法）· 覆盖率 · 对照评测 · GitHub Actions
静态分析    JS 词法分析 · 污点传播 · HTML/模板边界识别（JSX / Svelte / Angular）
AI 应用     提示词结构化约束 · JSON 容错解析 · 输出校验与重写 · DeepSeek / OpenAI SDK
游戏        Unity(团结引擎) · ShaderLab / HLSL · UGUI · DOTween
工程        Git / GitHub · Linux · Docker（基础）
```

---

## 📌 关于我

- **2027 年 7 月毕业**，可 2027.07 全职到岗；现阶段可远程实习、可全程线上面试。
- 现居匈牙利（米什科尔茨大学），中文母语，英文可读技术文档与官方 API 文档。
- 每个仓库都有 README、运行截图、已知局限，以及「这里还没测」的坦白——
  宁可先写下边界，也不想让人跑起来才发现。

## 📫 联系

- 邮箱：`chen.zizheng@student.uni-miskolc.hu`
- GitHub：[github.com/Chen-zizheng](https://github.com/Chen-zizheng)
