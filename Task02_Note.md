#Task2学习
这里记录了我学习 LangChain 第二章（提示词与输出解析）的心路历程。作为一个力学专业的学生，我不仅在折腾代码，更在思考如何让 AI 真正听懂复杂的工程指令。

---

* **核心目标**：掌握提示词工程、少样本学习及输出结构化。
* **主要工具**：LangChain + 智谱 GLM-4 (API) + Pydantic。

---

## 🛠️ 学习过程

### 1. 初次对话：建立“连接感”
最开始只是简单的问答。看着终端里跳出的回复，我知道思路打通了。

基础问答与工作流测试
<img width="1721" height="952" alt="屏幕截图 2025-10-28 210300" src="https://github.com/user-attachments/assets/2f56a518-4872-4460-9c02-a20750b6dd2a" />
> *这张截图记录了我最初运行 `tasktwo_workflow_test.py` 的时刻，成功拿到了 AI 对 LangChain 的定义。*

### 2. 多轮对话与提示词模板
我尝试让 AI 扮演一个“耐心且简洁”的导师。通过提示词模板，我发现可以像给函数传参一样给 AI 传指令。

提示词模板与对话历史<img width="1722" height="941" alt="屏幕截图 2026-04-16 190835" src="https://github.com/user-attachments/assets/44f693b3-0698-4935-ba0c-54618faa92f1" />
> *在这一步，我开始尝试引入 `history` 变量，让 AI 拥有了“记忆”。*

但在尝试更复杂的提示词时，我也遇到了 **模型编码不匹配（400 Error）** 的小插曲：

调试过程中的报错记录<img width="1717" height="950" alt="屏幕截图 2026-04-16 192134" src="https://github.com/user-attachments/assets/3ba58280-12e2-48eb-96a3-563202064b5c" />
> *debug 的过程虽然痛苦，但让我对 API 的调用规范理解得更深了。*

### 3. 少样本学习（Few-Shot）：给 AI 打个样
AI 有时候很笨，但如果你给它几个例子，它会瞬间变聪明。

少样本提示词运行效果<img width="1721" height="953" alt="屏幕截图 2026-04-16 195203" src="https://github.com/user-attachments/assets/99305361-1292-426a-a697-babce80927c1" />
> *看到 AI 能根据我设定的 `easy` 或 `hard` 难度自动切换回复风格，真的很爽！*

### 4. 输出解析：从“废话”到“干货”
这是本章最硬核的部分。我不想听 AI 唠叨，我只想要它把结果整理成 Python 字符串或字典。使用 `StrOutputParser` 后，输出结果变得非常干净。

字符串解析器测试<img width="1716" height="942" alt="屏幕截图 2026-04-16 200904" src="https://github.com/user-attachments/assets/b44b7ffe-cbc2-48e7-bb58-38d866b8eb80" />

---

## 🎓 最终实战：为力学人定制的 AI 助手

最后，我完成了一个综合练习。我增加了一个动态参数 `level`，测试了一下针对 **“力学专业 AI 零基础研究生”** 的建议。

章节综合练习运行结果<img width="1717" height="947" alt="屏幕截图 2026-04-16 203227" src="https://github.com/user-attachments/assets/ae067125-ec36-4bb0-a238-e92f75de1716" />

看到这里，我突然意识到，AI 不仅仅是一个聊天框，它真的可以成为我研究流程中的一个“智能插件”。

---

## 💡 心得小结
1. **不要硬编码**：尽量用 `PromptTemplate` 和 `.env` 配置文件，让代码有弹性。
2. **结构化是灵魂**：如果想把 AI 接进自己的力学计算程序，`PydanticOutputParser` 是必修课。


