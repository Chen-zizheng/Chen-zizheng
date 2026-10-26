# 陈子政 · Chen Zizheng

**2027 届 · 计算机科学本科（海外） · 求职中**

目标岗位：**测试开发 / 自动化测试 / AI 应用开发 / 游戏客户端（Unity）**

我习惯用「公开、可克隆、文档齐全、能跑起来」的仓库交付作品——
作品的价值只有被人真正打开过才算兑现。

---

## 🧪 三个方向，三套可验证的代码

<table>
<tr>
<td width="50%" valign="top">

### 🔍 AI 辅助 Web 漏洞扫描器
**Python · BeautifulSoup · LLM · pytest · GitHub Actions**

解析 HTML 提取表单 / 内联事件 / 危险函数等 4 类风险特征，
交给大模型输出 XSS、SQL 注入的结构化判定，落盘 JSON + Markdown 报告。

**16 个 pytest 用例**覆盖特征提取与模型输出解析；
模型调用用 stub 替换，CI 无需联网、不耗额度。

[→ ai-web-vuln-scanner](https://github.com/Chen-zizheng/ai-web-vuln-scanner)

</td>
<td width="50%" valign="top">

### 🎯 JobRadar 校招岗位雷达
**Python · Streamlit · LLM**

抓取校招岗位 → 本地关键词粗筛 → 大模型结构化打分 → Streamlit 可视化筛选。
针对「Token 贵、跑一半就断」两个痛点，做了公司粒度增量评估与逐条即时落盘。

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
测试        pytest · 用例设计（等价类/边界值/场景法）· GitHub Actions
AI 应用     提示词结构化约束 · JSON 容错解析 · DeepSeek / OpenAI SDK
游戏        Unity(团结引擎) · ShaderLab / HLSL · UGUI · DOTween
工程        Git / GitHub · Linux · Docker（基础）
```

---

## 📌 关于我

- **2027 年 7 月毕业**，可 2027.07 全职到岗；现阶段可远程实习、可全程线上面试。
- 现居匈牙利（米什科尔茨大学），中文母语，英文可读技术文档与官方 API 文档。
- 无实习经历，所以把时间花在「把项目做到能被检验」上：
  每个仓库都有 README、运行截图、已知局限，以及「这里还没测」的坦白。

## 📫 联系

- 邮箱：`chen.zizheng@student.uni-miskolc.hu`
- GitHub：[github.com/Chen-zizheng](https://github.com/Chen-zizheng)
