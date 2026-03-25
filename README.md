[README.md](https://github.com/user-attachments/files/26248268/README.md)
# 52 Prompt-AI Patterns สำหรับ OpenAI GPT

> อ้างอิงจากไฟล์ **Prompt Pattern Catalog v2** (PDF ที่อัปโหลด)  
> โดย **ชื่อแพตเทิร์นและคำอธิบายตั้งต้น** มาจาก catalog ต้นฉบับ ส่วน **ความหมายภาษาไทย, คำอธิบายเชิงใช้งาน, โครงสร้างแนะนำ, การประยุกต์ใช้กับ OpenAI GPT และ AI LLM Sample** เป็นการขยายความเพื่อให้ใช้งานจริงได้ทันทีบน GitHub

## ไฟล์นี้ประกอบด้วยอะไรบ้าง
ไฟล์ Markdown นี้ออกแบบมาเพื่ออัปโหลดขึ้น GitHub และนำไปใช้ซ้ำได้ทันที  
ในแต่ละแพตเทิร์นจะมี:

- **ชื่อ (Name)**
- **ความหมาย (Meaning)**
- **คำอธิบาย (Description)**
- **โครงสร้างแนะนำ (Suggested Structure)**
- **การประยุกต์ใช้กับ OpenAI GPT**
- **AI LLM Sample**

## หมายเหตุการใช้งาน
- ควรคง **ชื่อแพตเทิร์นภาษาอังกฤษ** ไว้ตามต้นฉบับ เพื่อให้เชื่อมโยงกับเอกสารอ้างอิงด้าน Prompt Engineering ได้ง่าย
- ในตัวอย่างให้แทนค่าช่องว่างอย่าง `[paste text]`, `[task]`, `[goal]` ด้วยข้อมูลจริงของคุณ
- ในงานจริงสามารถผสมหลายแพตเทิร์นเข้าด้วยกัน เช่น **Persona + Template + Validation + JSON Schema**

## Summary Table

| No. | Pattern Name | Category | Best Used For |
|---:|---|---|---|
| 1 | Meta Language Creation Pattern | Meta Prompting | custom shorthand commands |
| 2 | Template Pattern | Output Control | strict output format |
| 3 | Persona Pattern | Interaction | role-based responses |
| 4 | Visualization Generator Pattern | Output Control | diagrams and visual specs |
| 5 | Recipe Pattern | Task Structuring | step-by-step procedures |
| 6 | Output Automater Pattern | Automation | automation scripts or code |
| 7 | Fact Check List Pattern | Validation | verification checklist |
| 8 | Reflection Pattern | Reasoning Improvement | self-review and improvement |
| 9 | Question Refinement Pattern | Meta Prompting | rewriting better questions |
| 10 | Alternative Approaches Pattern | Reasoning | comparing solution options |
| 11 | Cognitive Verifier Pattern | Reasoning | breaking down complex problems |
| 12 | Refusal Breaker Pattern | Safety Recovery | safe redirection after refusal |
| 13 | Flipped Interaction Pattern | Interaction | clarifying before answering |
| 14 | Game Play Pattern | Interaction | game-based learning |
| 15 | Infinite Generation Pattern | Generation Control | large-scale idea generation |
| 16 | Context Manager Pattern | Context Control | controlling usable context |
| 17 | Chain-of-Thought Pattern | Reasoning | stepwise reasoning |
| 18 | Few-Shot Prompting Pattern | Learning by Example | learning from examples |
| 19 | Zero-Shot Prompting Pattern | Baseline Prompting | simple direct prompting |
| 20 | Tree-of-Thought Pattern | Advanced Reasoning | multi-branch reasoning |
| 21 | ReAct Pattern | Agentic Workflow | reason + act workflows |
| 22 | Audience Persona Pattern | Interaction | audience-specific explanation |
| 23 | Ask for Input Pattern | Interaction | collecting missing inputs |
| 24 | Menu Actions Pattern | Command Interface | command-driven assistants |
| 25 | Tail Generation Pattern | Output Control | mandatory closing section |
| 26 | Prompt Compiler Pattern | Prompt Engineering | turning simple prompts into structured prompts |
| 27 | Prompt Debugger Pattern | Prompt Engineering | finding why prompts fail |
| 28 | Prompt Compression Pattern | Prompt Optimization | reducing prompt length |
| 29 | Prompt Safety Filter Pattern | Safety | classifying request safety |
| 30 | Prompt Self-Improvement Pattern | Meta Prompting | iteratively improving prompts |
| 31 | Multi-Expert Panel Pattern | Reasoning | multi-perspective review |
| 32 | Hypothesis Testing Pattern | Reasoning | evaluating competing hypotheses |
| 33 | Prompt Mutation Pattern | Prompt Engineering | creating prompt variations |
| 34 | Knowledge Gap Detector Pattern | Analysis | finding missing requirements |
| 35 | Strategy Planner Pattern | Planning | planning before solving |
| 36 | JSON Schema Pattern | Structured Output | valid machine-readable JSON |
| 37 | Structured Data Pattern | Structured Output | structured extraction tables |
| 38 | Validation Pattern | Output Quality | rule-based output checking |
| 39 | Self-Consistency Pattern | Advanced Reasoning | choosing the most consistent answer |
| 40 | Debate Pattern | Reasoning | balanced pros-vs-cons debate |
| 41 | Multi-Agent Collaboration Pattern | Agentic Workflow | specialized agent teamwork |
| 42 | Planner-Executor Pattern | Agentic Workflow | separate planning from execution |
| 43 | Tool Selection Pattern | Agentic Workflow | choosing the right tool |
| 44 | Goal Decomposition Pattern | Planning | breaking big goals into tasks |
| 45 | Prompt Refactor Pattern | Prompt Engineering | cleaning up existing prompts |
| 46 | Prompt DSL Pattern | Meta Prompting | mini-language prompt syntax |
| 47 | Prompt Pipeline Pattern | Workflow | multi-stage prompt workflows |
| 48 | Conversation Memory Pattern | Context | persistent conversation state |
| 49 | Context Window Reset Pattern | Context | starting fresh with clean context |
| 50 | Dialogue Strategy Pattern | Interaction | consistent conversation behavior |
| 51 | Prompt Benchmark Pattern | Evaluation | testing prompt quality |
| 52 | Prompt Anti-Pattern Detection | Prompt Engineering | detecting weak prompt design |

---

    ## 1. Meta Language Creation Pattern

    **Meaning**  
    สร้างภาษาย่อหรือสัญลักษณ์เฉพาะที่ AI เข้าใจความหมายตามกติกาที่กำหนด

    **Description**  
    เหมาะเมื่อคุณต้องคุยกับโมเดลบ่อย ๆ ในรูปแบบเดิม เช่น การสั่งย่อ สรุป วิเคราะห์ หรือให้คะแนน โดยเปลี่ยนคำสั่งยาวให้เป็นโค้ดสั้นที่ใช้ซ้ำได้

    **Suggested Structure**  
    ```text
    Define symbols/keywords -> Define meaning of each symbol -> Give command string -> Provide input text/data
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้าง command language ส่วนตัว เช่น SUM, EXP, RISK, ACT เพื่อเร่งงานสรุป วิเคราะห์เอกสาร และรีวิวไอเดีย

    **AI LLM Sample**  
    ```text
    You are an assistant that understands this command language:
SUM = summarize in 5 bullets
EXP = explain simply
RISK = list top 3 risks
ACT = recommend next actions

Command: SUM + RISK + ACT
Input: [paste project proposal here]
    ```

---

    ## 2. Template Pattern

    **Meaning**  
    บังคับให้ผลลัพธ์ออกมาตามแม่แบบที่กำหนดไว้ล่วงหน้า

    **Description**  
    เหมาะกับงานที่ต้องการรูปแบบคงที่ เช่น รายงานประจำวัน, meeting notes, PRD, user story, หรือโพสต์โซเชียลที่ต้องมีหัวข้อเหมือนกันทุกครั้ง

    **Suggested Structure**  
    ```text
    Task -> Fixed template -> Field instructions -> Input -> Fill template only
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อให้ผลลัพธ์พร้อมนำไปวางในเอกสาร ระบบงาน หรือฐานข้อมูลได้ทันที โดยลดการแก้ format ภายหลัง

    **AI LLM Sample**  
    ```text
    Create a meeting summary using this exact template:

Project:
Date:
Attendees:
Key Decisions:
Open Issues:
Next Actions:
Owner:

Input notes:
[paste notes here]
    ```

---

    ## 3. Persona Pattern

    **Meaning**  
    กำหนดบทบาทหรืออาชีพให้ AI เพื่อให้สไตล์การตอบและมุมมองตรงงานมากขึ้น

    **Description**  
    ช่วยให้คำตอบมีโฟกัส เช่น ให้ GPT ตอบแบบนักกลยุทธ์ นักวิเคราะห์ข้อมูล Product Manager ครู หรือที่ปรึกษากฎหมาย

    **Suggested Structure**  
    ```text
    Role -> Task -> Context -> Constraints -> Output style
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อจำลองผู้เชี่ยวชาญเฉพาะด้าน และยกระดับคุณภาพคำตอบให้เหมาะกับ business context

    **AI LLM Sample**  
    ```text
    You are a senior product manager.
Task: Review the feature idea below.
Context: We are building a B2B SaaS dashboard.
Constraints: Focus on user value, risks, MVP scope, and success metrics.
Output: 5 concise sections.

Feature idea:
[paste idea here]
    ```

---

    ## 4. Visualization Generator Pattern

    **Meaning**  
    ให้ AI สร้างโค้ด คำอธิบาย หรือ prompt สำหรับแผนภาพและภาพประกอบ

    **Description**  
    เหมาะกับการเปลี่ยนข้อมูลหรือ workflow ให้เป็น diagram, flowchart, mind map, Mermaid, หรือโครงร่างสไลด์ภาพ

    **Suggested Structure**  
    ```text
    Data/topic -> Visualization type -> Layout rules -> Output code/spec
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อให้สร้าง Mermaid, ASCII diagram, wireframe notes หรือโค้ด chart อย่างรวดเร็ว

    **AI LLM Sample**  
    ```text
    Convert the following workflow into Mermaid flowchart code.
Rules:
- Use clear node labels
- Keep the chart readable
- Group approval steps separately

Workflow:
[paste process here]
    ```

---

    ## 5. Recipe Pattern

    **Meaning**  
    ให้ผลลัพธ์เป็นขั้นตอนแบบลำดับ 1-2-3 ที่ทำตามได้จริง

    **Description**  
    เหมาะกับ SOP, how-to, runbook, onboarding, และการสอนงานที่ต้องทำทีละขั้นพร้อมเงื่อนไขหรือวัสดุที่ใช้

    **Suggested Structure**  
    ```text
    Goal -> Inputs/materials -> Ordered steps -> Expected result -> Tips/cautions
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อเปลี่ยนโจทย์กว้าง ๆ ให้กลายเป็นคู่มือปฏิบัติแบบทำตามได้ทันที

    **AI LLM Sample**  
    ```text
    Create a step-by-step SOP for onboarding a new team member.
Include:
- Required inputs
- Ordered steps
- Common mistakes
- Completion checklist

Context:
[team/process details]
    ```

---

    ## 6. Output Automater Pattern

    **Meaning**  
    สั่งให้ AI สร้างสคริปต์หรือโค้ดเพื่อผลิตผลลัพธ์อัตโนมัติ

    **Description**  
    ใช้เมื่อไม่ต้องการเพียงคำตอบ แต่ต้องการสิ่งที่นำไปรันต่อได้ เช่น Python script, SQL, regex, shell command, หรือ template generator

    **Suggested Structure**  
    ```text
    Desired output/file -> Automation method -> Inputs -> Constraints -> Deliver runnable artifact
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้างโค้ดสำหรับแปลงไฟล์, ทำรายงานอัตโนมัติ, สร้าง CSV/JSON, หรือจัดรูปข้อมูลก่อนนำไปใช้

    **AI LLM Sample**  
    ```text
    Generate a Python script that reads a CSV file and produces a Markdown summary report.
Requirements:
- Input file path as argument
- Show top 10 rows
- Compute basic stats
- Save output as report.md
    ```

---

    ## 7. Fact Check List Pattern

    **Meaning**  
    ให้ AI แยก claim หรือข้อเท็จจริงสำคัญที่ควรตรวจสอบก่อนนำไปใช้จริง

    **Description**  
    เหมาะกับคำตอบที่มีข้อมูลหลายส่วน เช่น แผนธุรกิจ สรุปรายงาน ข่าว บทวิเคราะห์ หรือข้อความที่ต้องการความน่าเชื่อถือ

    **Suggested Structure**  
    ```text
    Draft answer -> Extract claims -> Mark what needs verification -> Suggest verification sources
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อช่วยทีมรีวิวคำตอบก่อนเผยแพร่ โดยเฉพาะเอกสารที่อ้างตัวเลข วันที่ กฎหมาย หรือข้อเท็จจริงภายนอก

    **AI LLM Sample**  
    ```text
    Review the answer below and extract all factual claims that should be verified.
For each claim, provide:
1) claim
2) why it needs checking
3) suggested source type

Answer:
[paste draft here]
    ```

---

    ## 8. Reflection Pattern

    **Meaning**  
    ให้ AI ทบทวนและวิจารณ์คำตอบของตัวเองก่อนส่งเวอร์ชันที่ดีขึ้น

    **Description**  
    เหมาะกับงานที่ต้องการความรอบคอบ เช่น การเขียนข้อเสนอ การวิเคราะห์ทางเลือก หรือการตอบคำถามซับซ้อน

    **Suggested Structure**  
    ```text
    Draft -> Self-critique -> Identify weaknesses -> Improved answer
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อยกระดับคุณภาพรอบสองโดยไม่ต้องเขียน prompt ใหม่ทั้งหมด

    **AI LLM Sample**  
    ```text
    Answer the question below.
Then reflect on your answer for gaps, assumptions, and weak points.
Finally provide an improved version.

Question:
[paste question here]
    ```

---

    ## 9. Question Refinement Pattern

    **Meaning**  
    ให้ AI ช่วยปรับคำถามเดิมให้ชัดเจน แม่นยำ และตอบได้ดีกว่าเดิม

    **Description**  
    มีประโยชน์เมื่อโจทย์ยังคลุมเครือ กว้างเกินไป หรือไม่มีบริบทพอ ทำให้ได้คำตอบคุณภาพต่ำ

    **Suggested Structure**  
    ```text
    Original question -> Weakness analysis -> Improved question(s) -> Rationale
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อยกระดับ prompt ของผู้ใช้ก่อนลงมือทำงานจริง โดยเฉพาะงานเชิงวิเคราะห์หรือวิชาชีพ

    **AI LLM Sample**  
    ```text
    Improve this user question so an AI can answer it better.
Provide:
- issues in the current wording
- 3 improved versions
- best final version

Question:
[paste original question]
    ```

---

    ## 10. Alternative Approaches Pattern

    **Meaning**  
    ให้ AI เสนอหลายแนวทางแก้ปัญหาพร้อมเปรียบเทียบข้อดีข้อเสีย

    **Description**  
    เหมาะกับงานตัดสินใจ เช่น เลือกเครื่องมือ เลือกกลยุทธ์ เลือกโครงสร้างทีม หรือเลือกรูปแบบการสื่อสาร

    **Suggested Structure**  
    ```text
    Problem -> Option A/B/C -> Pros/cons -> Trade-offs -> Recommendation
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อช่วยตัดสินใจอย่างมีกรอบ ไม่ยึดติดกับคำตอบเดียว

    **AI LLM Sample**  
    ```text
    Given the problem below, propose 3 different approaches.
For each approach include:
- summary
- pros
- cons
- when to use
Then recommend the best one.

Problem:
[paste problem]
    ```

---

    ## 11. Cognitive Verifier Pattern

    **Meaning**  
    แตกคำถามใหญ่เป็นคำถามย่อยก่อน แล้วค่อยรวมเป็นคำตอบสุดท้าย

    **Description**  
    ช่วยลดการข้ามขั้นและทำให้ reasoning มีระบบขึ้น เหมาะกับโจทย์หลายเงื่อนไขหรือหลายประเด็น

    **Suggested Structure**  
    ```text
    Main question -> Sub-questions -> Answer each -> Synthesize final answer
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT ในงานวิเคราะห์เคส ธุรกิจ วิจัย หรือปัญหาที่ต้องแยกองค์ประกอบก่อนตัดสินใจ

    **AI LLM Sample**  
    ```text
    Solve the problem by first breaking it into smaller questions.
Show:
1) sub-questions
2) short answers to each
3) final synthesis

Problem:
[paste problem]
    ```

---

    ## 12. Refusal Breaker Pattern

    **Meaning**  
    ถ้าคำขอเดิมตอบไม่ได้ ให้ AI อธิบายข้อจำกัดและเสนอทางเลือกที่ตอบได้อย่างปลอดภัย

    **Description**  
    เหมาะกับงานที่มีข้อจำกัดด้านนโยบาย กฎหมาย ความปลอดภัย หรือข้อมูลไม่เพียงพอ แต่ยังต้องการช่วยผู้ใช้ต่อในกรอบที่เหมาะสม

    **Suggested Structure**  
    ```text
    Unsafe/unanswerable request -> Brief refusal reason -> Safe alternative query -> Helpful redirect
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อรักษาประสบการณ์ผู้ใช้ให้ดี แม้ต้องปฏิเสธบางส่วน

    **AI LLM Sample**  
    ```text
    If the request cannot be answered directly, do not stop at refusal.
Explain the limitation briefly and provide:
- a safer alternative
- a reformulated question
- a helpful next step

Request:
[paste request]
    ```

---

    ## 13. Flipped Interaction Pattern

    **Meaning**  
    ให้ AI เป็นฝ่ายถามกลับก่อน เพื่อเก็บข้อมูลที่จำเป็นแล้วค่อยตอบ

    **Description**  
    เหมาะกับงานที่คุณภาพขึ้นกับบริบท เช่น การเขียนอีเมล แผนงาน ข้อเสนอ หรือคำแนะนำเฉพาะบุคคล

    **Suggested Structure**  
    ```text
    Identify missing info -> Ask targeted questions -> Wait/assume -> Perform task
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อให้ผลลัพธ์ตรงความต้องการมากขึ้น โดยเฉพาะเมื่ออินพุตเริ่มต้นยังไม่ครบ

    **AI LLM Sample**  
    ```text
    Before answering, ask up to 5 targeted clarifying questions that would most improve the result.
After the questions, provide a draft answer based on reasonable assumptions.

Task:
[paste task]
    ```

---

    ## 14. Game Play Pattern

    **Meaning**  
    เปลี่ยนงานเรียนรู้หรือสำรวจข้อมูลให้เป็นรูปแบบเกม

    **Description**  
    ช่วยเพิ่ม engagement ในการเรียน การฝึกภาษา การทบทวนความรู้ หรือ workshop

    **Suggested Structure**  
    ```text
    Learning goal -> Rules -> Scoring/progress -> Turns -> Feedback
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้าง quiz, role-based challenge, flashcard game, หรือ simulation ที่สนุกขึ้น

    **AI LLM Sample**  
    ```text
    Turn the topic below into a quiz game.
Include:
- 10 questions
- score tracking
- increasing difficulty
- brief explanations after each answer

Topic:
[paste topic]
    ```

---

    ## 15. Infinite Generation Pattern

    **Meaning**  
    ให้ AI สร้างผลลัพธ์ต่อเนื่องตามกฎ จนกว่าจะถูกสั่งให้หยุด

    **Description**  
    เหมาะกับ brainstorming, idea list, name generation, content prompts, และงานที่ต้องการปริมาณมาก

    **Suggested Structure**  
    ```text
    Generation rule -> Continue iterating -> Stop condition/user stop
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อระดมไอเดียจำนวนมากอย่างต่อเนื่องโดยคงธีมหรือเงื่อนไขเดิม

    **AI LLM Sample**  
    ```text
    Generate startup ideas in batches of 10.
Rules:
- no duplicates
- each idea must include problem, target user, and monetization
Continue until I say STOP.
    ```

---

    ## 16. Context Manager Pattern

    **Meaning**  
    กำหนดให้ AI ใช้หรือไม่ใช้บริบทบางส่วนอย่างชัดเจน

    **Description**  
    สำคัญเมื่อมีข้อมูลหลายชุด และบางชุดอาจรบกวนคำตอบ เช่น ต้องใช้เฉพาะ brief ล่าสุด หรือไม่ให้อ้างข้อมูลเก่า

    **Suggested Structure**  
    ```text
    Allowed context -> Excluded context -> Priority rules -> Task
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อคุม scope ของคำตอบ ลดการปนเปื้อนจากข้อมูลคนละรอบหรือคนละเอกสาร

    **AI LLM Sample**  
    ```text
    Use only the information in Section A and Section B below.
Ignore any prior assumptions or outside knowledge unless explicitly requested.

Task:
[paste task]

Section A:
...
Section B:
...
    ```

---

    ## 17. Chain-of-Thought Pattern

    **Meaning**  
    กระตุ้นให้ AI คิดเป็นลำดับขั้นก่อนสรุปคำตอบ

    **Description**  
    เหมาะกับโจทย์ตรรกะ คณิตศาสตร์ วางแผน และงานที่ต้องระวังการข้ามเหตุผล แต่ในงานใช้งานจริงมักควรขอเพียงสรุปเหตุผลแบบย่อ

    **Suggested Structure**  
    ```text
    Question -> Stepwise reasoning -> Final answer
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อเพิ่มความแม่นยำของงาน reasoning โดยขอเหตุผลสรุปที่ตรวจสอบได้

    **AI LLM Sample**  
    ```text
    Solve the problem carefully step by step, but present only a concise reasoning summary and the final answer.

Problem:
[paste problem]
    ```

---

    ## 18. Few-Shot Prompting Pattern

    **Meaning**  
    ให้ตัวอย่างก่อนเพื่อสอนรูปแบบที่ต้องการ

    **Description**  
    เหมาะมากเมื่อ output ต้องมีสไตล์หรือรูปแบบเฉพาะ เช่น labeling, rewriting, classification, tone matching

    **Suggested Structure**  
    ```text
    Instruction -> Examples -> New input -> Output in same pattern
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสอน format หรือ quality bar โดยไม่ต้องอธิบายยาว

    **AI LLM Sample**  
    ```text
    Classify each message as Positive, Neutral, or Negative.
Examples:
Text: "Great job on the release!" -> Positive
Text: "The update is okay, nothing special." -> Neutral
Text: "This is frustrating and slow." -> Negative

Now classify:
[paste new texts]
    ```

---

    ## 19. Zero-Shot Prompting Pattern

    **Meaning**  
    ให้เพียงคำสั่งโดยไม่ยกตัวอย่าง

    **Description**  
    เหมาะกับงานทั่วไปที่โจทย์ชัดเจนอยู่แล้ว และไม่จำเป็นต้องใช้ตัวอย่างช่วยกำกับ

    **Suggested Structure**  
    ```text
    Instruction -> Context -> Constraints -> Output
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT สำหรับงานสรุป เขียนใหม่ แปล จัดหมวด หรือช่วยคิดเบื้องต้นอย่างรวดเร็ว

    **AI LLM Sample**  
    ```text
    Summarize the following article into 5 bullet points for business executives.
Keep it concise and action-oriented.

Article:
[paste text]
    ```

---

    ## 20. Tree-of-Thought Pattern

    **Meaning**  
    ให้ AI พิจารณาหลายเส้นทางความคิด แล้วประเมินว่าเส้นทางไหนดีที่สุด

    **Description**  
    เหมาะกับปัญหาที่มีหลายทางเลือกและต้องเปรียบเทียบเชิงลึก เช่น กลยุทธ์ ธุรกิจ การออกแบบ solution

    **Suggested Structure**  
    ```text
    Problem -> Generate branches -> Evaluate branches -> Select best path -> Final answer
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เมื่อต้องการสำรวจทางเลือกหลายแบบก่อนตัดสินใจ ไม่ใช่กระโดดไปคำตอบเดียว

    **AI LLM Sample**  
    ```text
    Consider multiple solution paths for the problem below.
Compare the strongest options, discard weak ones, and return the best final recommendation with concise rationale.

Problem:
[paste problem]
    ```

---

    ## 21. ReAct Pattern

    **Meaning**  
    ผสานการคิดกับการลงมือทำ เช่น เลือกใช้เครื่องมือ ค้นข้อมูล หรือเรียก action ก่อนตอบ

    **Description**  
    เหมาะกับงานที่ต้องสลับระหว่าง reasoning และ action เช่น วิเคราะห์ข้อมูล, เรียก API, หรือค้นเอกสาร

    **Suggested Structure**  
    ```text
    Reason -> Act -> Observe -> Continue -> Final answer
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT agents หรือระบบที่เชื่อมเครื่องมือ เพื่อแก้โจทย์ที่ต้องอาศัยข้อมูลภายนอกหรือหลายขั้นตอน

    **AI LLM Sample**  
    ```text
    For the task below, think about what action is needed, choose the best action, evaluate the result, and then continue until you can answer confidently.
Return the final answer plus a short action log.

Task:
[paste task]
    ```

---

    ## 22. Audience Persona Pattern

    **Meaning**  
    กำหนดกลุ่มเป้าหมายของคำตอบให้ชัด เช่น ผู้บริหาร เด็ก ม.ปลาย ลูกค้า หรือผู้เริ่มต้น

    **Description**  
    ช่วยให้ระดับภาษา ความลึก และตัวอย่างตรงกับคนอ่านมากขึ้น

    **Suggested Structure**  
    ```text
    Topic -> Target audience -> Knowledge level -> Tone -> Output
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อรีแพ็กข้อความเดียวกันให้เหมาะกับหลายกลุ่ม เช่น แปลงจาก technical เป็น executive summary

    **AI LLM Sample**  
    ```text
    Explain the topic below for a non-technical executive.
Use plain language, business implications, and no jargon.

Topic:
[paste topic]
    ```

---

    ## 23. Ask for Input Pattern

    **Meaning**  
    ให้ AI ขอข้อมูลที่ขาดก่อนเริ่มทำงาน

    **Description**  
    เหมาะกับงานที่ต้องมีตัวแปรจากผู้ใช้ เช่น ชื่อแบรนด์ กลุ่มเป้าหมาย งบประมาณ เป้าหมาย หรือไฟล์อินพุต

    **Suggested Structure**  
    ```text
    State missing inputs -> Ask user -> Wait for input -> Execute task
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้าง workflow แบบเก็บ requirement ก่อนทำงานจริง

    **AI LLM Sample**  
    ```text
    To complete this task well, first ask me for the missing inputs you need.
Do not produce the final output until the required inputs are collected.

Task:
[paste task]
    ```

---

    ## 24. Menu Actions Pattern

    **Meaning**  
    กำหนดชุดคำสั่งหรือเมนูที่เรียก action ต่าง ๆ ได้อย่างชัดเจน

    **Description**  
    เหมาะกับการสร้าง AI assistant ที่มีคำสั่งประจำ เช่น /summarize /draft /improve /translate

    **Suggested Structure**  
    ```text
    Define menu/commands -> Map each command to action -> Handle user selection
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อทำให้ assistant ใช้งานง่ายและคงรูปแบบ interaction เดิมทุกครั้ง

    **AI LLM Sample**  
    ```text
    You are a writing assistant with these commands:
 /outline = create outline
 /draft = write first draft
 /improve = improve clarity
 /shorten = compress text

When I send a command, perform only that action on the provided text.
    ```

---

    ## 25. Tail Generation Pattern

    **Meaning**  
    กำหนดให้ AI ต่อท้ายข้อความหรือ section บางอย่างเสมอ

    **Description**  
    ใช้ได้ดีเมื่อผลลัพธ์ทุกชิ้นต้องมี footer, CTA, disclaimer, next steps, หรือ checklist ปิดท้าย

    **Suggested Structure**  
    ```text
    Main task -> Mandatory tail section -> Tail rules
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อทำให้ผลลัพธ์ทุกครั้งมีส่วนมาตรฐานท้ายข้อความโดยอัตโนมัติ

    **AI LLM Sample**  
    ```text
    Write the answer normally, but always end with this exact section:

Next Step:
- One practical next action
- One key risk to watch

Question:
[paste question]
    ```

---

    ## 26. Prompt Compiler Pattern

    **Meaning**  
    แปลง prompt ธรรมดาให้กลายเป็น prompt ที่มีโครงสร้างดีขึ้น

    **Description**  
    ช่วยยกระดับคำสั่งสั้น ๆ ให้มี role, task, context, constraints, output format ครบขึ้น

    **Suggested Structure**  
    ```text
    Simple prompt -> Expand into structured prompt -> Preserve core intent
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อเป็น prompt architect ที่ช่วยรีไรต์คำสั่งให้พร้อมใช้งานจริง

    **AI LLM Sample**  
    ```text
    Convert the simple request below into a high-quality structured prompt.
Include:
- role
- task
- context
- constraints
- input variables
- output format
- quality criteria

Simple request:
[paste request]
    ```

---

    ## 27. Prompt Debugger Pattern

    **Meaning**  
    วิเคราะห์ว่าทำไม prompt เดิมให้ผลลัพธ์ไม่ดี แล้วเสนอวิธีแก้

    **Description**  
    เหมาะกับการปรับปรุง prompt ที่คลุมเครือ กว้างเกินไป หรือมี format ไม่ชัด

    **Suggested Structure**  
    ```text
    Original prompt -> Failure symptoms -> Root causes -> Fixed prompt
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อ audit และซ่อม prompt ก่อนนำไปใช้ในงานหรือระบบ production

    **AI LLM Sample**  
    ```text
    Analyze the following prompt and explain why it may fail.
Then provide:
- specific issues
- likely bad outputs
- an improved prompt

Prompt:
[paste failing prompt]
    ```

---

    ## 28. Prompt Compression Pattern

    **Meaning**  
    ย่อ prompt ให้สั้นลงแต่ยังคงเจตนาเดิม

    **Description**  
    มีประโยชน์เมื่ออยากลด token cost, ทำ prompt library ให้กระชับ, หรือเตรียมใช้ในระบบที่มีข้อจำกัดเรื่องความยาว

    **Suggested Structure**  
    ```text
    Original prompt -> Preserve intent -> Remove redundancy -> Shorter prompt
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้าง prompt เวอร์ชัน lean สำหรับ production หรือ automation

    **AI LLM Sample**  
    ```text
    Compress the prompt below into a shorter version while preserving intent, constraints, and output format.
Return:
1) compressed prompt
2) what was removed
3) any risk of loss

Prompt:
[paste long prompt]
    ```

---

    ## 29. Prompt Safety Filter Pattern

    **Meaning**  
    ให้ AI ประเมินความปลอดภัยของคำขอก่อนตอบ

    **Description**  
    ช่วยคัดกรองคำขอเสี่ยงหรือไม่เหมาะสม และกำหนดว่าจะตอบได้แค่ไหนหรือควร redirect อย่างไร

    **Suggested Structure**  
    ```text
    Classify risk -> Decide allow/block/restrict -> Safe response
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT หรือแชตบอตองค์กรเพื่อเพิ่มชั้นความปลอดภัยก่อนให้คำตอบ

    **AI LLM Sample**  
    ```text
    Before answering, classify the request as:
- safe
- sensitive
- disallowed

Then:
- answer normally if safe
- answer with caution if sensitive
- refuse briefly and redirect if disallowed

Request:
[paste request]
    ```

---

    ## 30. Prompt Self-Improvement Pattern

    **Meaning**  
    ให้ AI ประเมินและปรับปรุง prompt หลังใช้งาน เพื่อให้รอบต่อไปดีขึ้น

    **Description**  
    เหมาะกับการทำ prompt iteration อย่างต่อเนื่อง โดยใช้ผลลัพธ์จริงมาช่วยปรับ

    **Suggested Structure**  
    ```text
    Run prompt -> Evaluate result -> Identify weaknesses -> Improve prompt
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้างวงจรพัฒนาคุณภาพ prompt แบบ continuous improvement

    **AI LLM Sample**  
    ```text
    Given the original prompt and its output, improve the prompt for the next iteration.
Return:
- what worked
- what failed
- improved prompt
- why it is better

Original prompt:
...
Output:
...
    ```

---

    ## 31. Multi-Expert Panel Pattern

    **Meaning**  
    จำลองมุมมองจากผู้เชี่ยวชาญหลายสายก่อนสรุปคำตอบรวม

    **Description**  
    เหมาะกับโจทย์ที่ต้องมองหลายมิติ เช่น ธุรกิจ เทคโนโลยี UX ความเสี่ยง กฎหมาย หรือการเงิน

    **Suggested Structure**  
    ```text
    Expert A view -> Expert B view -> Expert C view -> Moderator synthesis
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อให้เห็น trade-off ข้ามสายงานโดยไม่ต้องถามหลายรอบ

    **AI LLM Sample**  
    ```text
    Simulate a panel of 3 experts:
- product manager
- engineer
- compliance lead

Have each expert review the proposal below, then provide a moderator summary with final recommendation.

Proposal:
[paste proposal]
    ```

---

    ## 32. Hypothesis Testing Pattern

    **Meaning**  
    สร้างสมมติฐานหลายข้อแล้วประเมินว่าอันไหนน่าเป็นไปได้ที่สุด

    **Description**  
    ใช้ได้ดีในงานวิเคราะห์สาเหตุ ปัญหายอดขายลด ระบบผิดพลาด หรือพฤติกรรมลูกค้าที่เปลี่ยนไป

    **Suggested Structure**  
    ```text
    Hypotheses -> Evidence for/against -> Evaluation -> Most likely conclusion
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อทำ root-cause analysis หรือ scenario analysis อย่างมีระบบ

    **AI LLM Sample**  
    ```text
    Analyze the issue below by generating 3-5 hypotheses.
For each hypothesis provide:
- supporting evidence
- contradicting evidence
- confidence level
Then rank the hypotheses.

Issue:
[paste issue]
    ```

---

    ## 33. Prompt Mutation Pattern

    **Meaning**  
    สร้าง prompt หลายเวอร์ชันจากแกนหลักเดียวกันด้วยกลยุทธ์ที่ต่างกัน

    **Description**  
    เหมาะกับการทดลอง style, tone, detail level, หรือวิธีสั่งงานหลายแบบเพื่อหาเวอร์ชันที่ดีที่สุด

    **Suggested Structure**  
    ```text
    Base prompt -> Mutation strategy -> Variant A/B/C -> Comparison
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อทำ A/B testing ของ prompt และขยาย prompt library อย่างเป็นระบบ

    **AI LLM Sample**  
    ```text
    Create 5 improved variants of the base prompt below.
Each variant should optimize for a different goal:
- clarity
- brevity
- expert depth
- beginner friendliness
- strict format

Base prompt:
[paste prompt]
    ```

---

    ## 34. Knowledge Gap Detector Pattern

    **Meaning**  
    ตรวจหาข้อมูลที่ยังขาดและอาจทำให้คำตอบไม่แม่นหรือไม่ครบ

    **Description**  
    เหมาะกับงานที่ต้องอาศัย requirement ชัดเจน เช่น เขียน proposal, ออกแบบระบบ, ประเมินแผน, หรือวิเคราะห์ข้อมูล

    **Suggested Structure**  
    ```text
    Task -> Known information -> Missing information -> Assumptions -> Impact
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อทำ requirement check ก่อนเริ่มงานจริง

    **AI LLM Sample**  
    ```text
    Review the task below and identify missing information that is required for a high-quality answer.
Return:
- known facts
- missing data
- assumptions if proceeding now
- questions to ask next

Task:
[paste task]
    ```

---

    ## 35. Strategy Planner Pattern

    **Meaning**  
    วางแผนก่อนลงมือ โดยจัดลำดับขั้นตอน ทรัพยากร และลำดับการตัดสินใจ

    **Description**  
    เหมาะกับโครงการ งานหลายเฟส หรือปัญหาที่ต้องการ roadmap ชัดเจน

    **Suggested Structure**  
    ```text
    Goal -> Plan -> Dependencies -> Timeline/order -> Success criteria
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อทำ strategic plan, execution roadmap, หรือ rollout plan

    **AI LLM Sample**  
    ```text
    Create a strategic action plan for the goal below.
Include:
- phases
- dependencies
- risks
- owners
- success criteria

Goal:
[paste goal]
    ```

---

    ## 36. JSON Schema Pattern

    **Meaning**  
    บังคับให้ผลลัพธ์เป็น JSON ที่ตรง schema แบบเข้มงวด

    **Description**  
    สำคัญมากเมื่อผลลัพธ์ต้องส่งต่อระบบ โปรแกรม หรือ workflow อัตโนมัติ

    **Suggested Structure**  
    ```text
    Task -> JSON schema -> Field constraints -> Output valid JSON only
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้าง structured response ที่ parse ได้แน่นอน เช่น extraction, tagging, classification

    **AI LLM Sample**  
    ```text
    Extract the information below into valid JSON that matches this schema exactly:

{
  "company": "string",
  "industry": "string",
  "risks": ["string"],
  "next_actions": ["string"]
}

Text:
[paste text here]
    ```

---

    ## 37. Structured Data Pattern

    **Meaning**  
    จัดผลลัพธ์ให้อยู่ในรูปแบบข้อมูลที่เครื่องอ่านต่อได้ง่าย

    **Description**  
    ยืดหยุ่นกว่า JSON Schema และเหมาะกับตาราง, CSV-like output, field list, หรือ record set

    **Suggested Structure**  
    ```text
    Task -> Required fields -> Output rows/records -> Formatting rules
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อเตรียมข้อมูลสำหรับ spreadsheet, database, ETL, หรือ dashboards

    **AI LLM Sample**  
    ```text
    Extract the following information into a markdown table with columns:
Name | Role | Team | Priority | Next Action

Source text:
[paste text]
    ```

---

    ## 38. Validation Pattern

    **Meaning**  
    ให้ AI ตรวจงานที่สร้างเสร็จแล้วกับกติกาหรือเงื่อนไขก่อนส่งคืน

    **Description**  
    เหมาะกับงานที่มีข้อกำหนดชัด เช่น จำนวนคำ format หัวข้อ ห้ามใช้ jargon หรือห้ามตกหล่น field

    **Suggested Structure**  
    ```text
    Draft output -> Validation rules -> Pass/fail -> Fix issues -> Final output
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้าง self-check layer เพิ่มความสม่ำเสมอของ output

    **AI LLM Sample**  
    ```text
    Create the output, then validate it against these rules:
- under 200 words
- plain language
- include exactly 3 bullet points
- end with one recommendation

If any rule is broken, fix it before returning the final answer.

Task:
[paste task]
    ```

---

    ## 39. Self-Consistency Pattern

    **Meaning**  
    ให้ AI ลองหลายแนวคิดหรือหลายคำตอบภายใน แล้วเลือกคำตอบที่สอดคล้องและน่าเชื่อถือที่สุด

    **Description**  
    มีประโยชน์กับโจทย์ reasoning ที่คำตอบอาจสวิงได้จากการสุ่มหรือการตีความ

    **Suggested Structure**  
    ```text
    Generate multiple attempts -> Compare -> Select most consistent answer -> Final output
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อเพิ่มเสถียรภาพของคำตอบในงานวิเคราะห์หรือแก้ปัญหา

    **AI LLM Sample**  
    ```text
    Consider multiple possible answers internally, then return the most consistent final answer with a concise explanation.

Question:
[paste question]
    ```

---

    ## 40. Debate Pattern

    **Meaning**  
    ให้มุมมองสองฝ่ายถกเถียงกันก่อนสรุปผล

    **Description**  
    เหมาะกับโจทย์ที่มีความเห็นต่างหรือ trade-off สูง เช่น buy vs build, remote vs onsite, open vs closed model

    **Suggested Structure**  
    ```text
    Position A -> Position B -> Rebuttals -> Synthesis -> Final conclusion
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อวิเคราะห์เชิงสมดุลและลดอคติจากมุมเดียว

    **AI LLM Sample**  
    ```text
    Debate both sides of the decision below.
Structure:
- side A argument
- side B argument
- rebuttals
- balanced conclusion

Decision:
[paste decision topic]
    ```

---

    ## 41. Multi-Agent Collaboration Pattern

    **Meaning**  
    ให้หลาย agent ที่เชี่ยวชาญต่างกันร่วมกันแก้ปัญหา

    **Description**  
    เหมาะกับงานซับซ้อนที่ต้องใช้หลายบทบาท เช่น researcher, analyst, writer, reviewer

    **Suggested Structure**  
    ```text
    Assign agent roles -> Each agent contributes -> Coordinator merges -> Final answer
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT-based agent systems เพื่อแบ่งงานเป็น modular workflow

    **AI LLM Sample**  
    ```text
    Simulate 4 agents:
1) researcher
2) analyst
3) writer
4) reviewer

Have them collaborate on the task below, then produce one final integrated answer.

Task:
[paste task]
    ```

---

    ## 42. Planner-Executor Pattern

    **Meaning**  
    แยกขั้นวางแผนออกจากขั้นลงมือทำ

    **Description**  
    ช่วยให้โมเดลไม่กระโดดทำทันทีโดยไม่มีแผน และเหมาะกับงานหลายขั้นตอนหรือหลาย deliverables

    **Suggested Structure**  
    ```text
    Planner creates plan -> Executor performs steps -> Review -> Final output
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT agents หรือ prompt ที่ต้องการให้มี planning stage ชัดเจนก่อน execution

    **AI LLM Sample**  
    ```text
    Phase 1: Create a plan for the task.
Phase 2: Execute the plan step by step.
Phase 3: Review whether the result matches the plan.

Task:
[paste task]
    ```

---

    ## 43. Tool Selection Pattern

    **Meaning**  
    ให้ AI เลือกเครื่องมือหรือ API ที่เหมาะสมที่สุดก่อนลงมือ

    **Description**  
    เหมาะกับระบบที่มีหลายเครื่องมือ เช่น search, calculator, code interpreter, database, email, image generator

    **Suggested Structure**  
    ```text
    Task -> Available tools -> Selection criteria -> Choose tool -> Use tool
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT systems ที่เชื่อม tool หลายตัวเพื่อเพิ่มประสิทธิภาพและลดการใช้เครื่องมือผิดประเภท

    **AI LLM Sample**  
    ```text
    You have access to these tools:
- web_search
- calculator
- python
- file_reader

For the task below, first decide which tool is most appropriate and explain why briefly.
Then solve the task using that tool.

Task:
[paste task]
    ```

---

    ## 44. Goal Decomposition Pattern

    **Meaning**  
    แตกเป้าหมายใหญ่ให้เป็นงานย่อยที่ทำได้จริง

    **Description**  
    เหมาะกับเป้าหมายกว้าง เช่น เปิดตัวสินค้าใหม่ สร้างระบบข้อมูล หรือเรียนทักษะใหม่ภายในเวลา محدد

    **Suggested Structure**  
    ```text
    Big goal -> Sub-goals -> Tasks -> Milestones -> Completion criteria
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อเปลี่ยนเป้าหมายคลุมเครือให้กลายเป็น action plan รายส่วน

    **AI LLM Sample**  
    ```text
    Break the goal below into smaller milestones and actionable tasks.
For each task include:
- objective
- owner type
- dependency
- done criteria

Goal:
[paste goal]
    ```

---

    ## 45. Prompt Refactor Pattern

    **Meaning**  
    รีไรต์ prompt ให้ชัด กระชับ และจัดโครงสร้างดีขึ้นโดยยังคงเจตนาเดิม

    **Description**  
    ต่างจาก debugger ที่เน้นหาสาเหตุเสีย Prompt Refactor เน้น rewrite ให้สวยและใช้งานซ้ำได้

    **Suggested Structure**  
    ```text
    Original prompt -> Refactored version -> Key improvements
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อปรับ prompt เก่าให้กลายเป็น standard prompt สำหรับทีม

    **AI LLM Sample**  
    ```text
    Refactor the prompt below to improve clarity, structure, and reusability.
Preserve the original intent.
Return:
- refactored prompt
- key improvements made

Prompt:
[paste prompt]
    ```

---

    ## 46. Prompt DSL Pattern

    **Meaning**  
    สร้างภาษาคำสั่งขนาดย่อที่มี syntax ชัดเจนสำหรับสั่ง AI

    **Description**  
    คล้าย meta language แต่มีรูปแบบ grammar/keywords ที่เป็นระบบมากขึ้น เหมาะกับ prompt libraries หรือ automation

    **Suggested Structure**  
    ```text
    Define mini-language syntax -> Define commands/arguments -> Parse instruction -> Execute
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อสร้าง prompt interface มาตรฐาน เช่น TASK:, TONE:, FORMAT:, LIMIT:

    **AI LLM Sample**  
    ```text
    Interpret the following DSL:

TASK:<task>
AUDIENCE:<audience>
TONE:<tone>
FORMAT:<format>
LIMIT:<constraints>

Now execute:
TASK: summarize the report
AUDIENCE: executives
TONE: concise
FORMAT: bullet points
LIMIT: max 120 words
    ```

---

    ## 47. Prompt Pipeline Pattern

    **Meaning**  
    เชื่อมหลาย prompt เป็นขั้นตอนต่อเนื่อง โดย output ของขั้นก่อนหน้าเป็น input ของขั้นถัดไป

    **Description**  
    เหมาะกับงานหลาย stage เช่น research -> outline -> draft -> refine -> format

    **Suggested Structure**  
    ```text
    Stage 1 -> Stage 2 -> Stage 3 -> Final output
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT workflow เพื่อแบ่งงานซับซ้อนเป็นส่วนย่อยที่ควบคุมคุณภาพได้ง่ายกว่า

    **AI LLM Sample**  
    ```text
    Process the task in 4 stages:
1) extract key points
2) build outline
3) write draft
4) refine for clarity

Return the output stage by stage.

Task:
[paste task]
    ```

---

    ## 48. Conversation Memory Pattern

    **Meaning**  
    ให้ AI เก็บข้อมูลสำคัญจากบทสนทนาไว้ใช้ต่อในรอบถัดไป

    **Description**  
    เหมาะกับ assistant ที่ต้องจำ preference, project state, tone, หรือข้อจำกัดที่ผู้ใช้บอกไว้แล้ว

    **Suggested Structure**  
    ```text
    Capture persistent facts -> Update memory -> Reuse in next turns
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT assistants เพื่อรักษาความต่อเนื่องของประสบการณ์ผู้ใช้

    **AI LLM Sample**  
    ```text
    Maintain a memory of the following persistent user preferences:
- prefers Thai explanations
- wants concise outputs
- works in HR and learning design

Use these preferences in future responses unless I override them.
    ```

---

    ## 49. Context Window Reset Pattern

    **Meaning**  
    รีเซ็ตบริบทเก่าแล้วโหลดเฉพาะข้อมูลที่เกี่ยวข้อง เพื่อป้องกันการปนกันของงานคนละเรื่อง

    **Description**  
    มีประโยชน์เมื่อเปลี่ยนหัวข้อใหญ่ หรือมีข้อมูลก่อนหน้าที่ไม่ควรนำมาปนกับงานใหม่

    **Suggested Structure**  
    ```text
    Discard old context -> Keep only selected facts -> Start fresh task
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อเริ่มงานใหม่อย่างสะอาด ลด hallucination จากบริบทที่ค้างอยู่

    **AI LLM Sample**  
    ```text
    Reset all prior working assumptions except the following:
- output language: Thai
- format preference: Markdown

Start a fresh task using only the new brief below:
[paste new brief]
    ```

---

    ## 50. Dialogue Strategy Pattern

    **Meaning**  
    กำหนดโทน วิธีถามกลับ และสไตล์การสนทนาให้คงที่

    **Description**  
    เหมาะกับ chatbot, coach, tutor, advisor, หรือ assistant ที่ต้องการบุคลิกการสนทนาชัดเจน

    **Suggested Structure**  
    ```text
    Tone -> Interaction rules -> Question style -> Response style
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อออกแบบ conversational behavior เช่น สุภาพ กระชับ โค้ชแบบถามนำ หรือที่ปรึกษาเชิงธุรกิจ

    **AI LLM Sample**  
    ```text
    Adopt this dialogue strategy:
- tone: professional and warm
- ask at most 2 clarifying questions
- prefer concise answers
- always end with one recommended next step

Now respond to:
[paste user request]
    ```

---

    ## 51. Prompt Benchmark Pattern

    **Meaning**  
    เปรียบเทียบ prompt หลายแบบด้วยเกณฑ์วัดที่กำหนด

    **Description**  
    เหมาะกับงานพัฒนา prompt สำหรับทีมหรือระบบ ที่ต้องพิสูจน์ว่าเวอร์ชันไหนดีที่สุดจริง

    **Suggested Structure**  
    ```text
    Prompt variants -> Test cases -> Metrics -> Comparison -> Winner
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อออกแบบการทดลอง prompt อย่างเป็นระบบก่อน deploy

    **AI LLM Sample**  
    ```text
    Benchmark the 3 prompts below against these criteria:
- clarity
- completeness
- format compliance
- token efficiency

Use the same test case for all prompts and provide a comparison table plus winner.

Prompts:
...
Test case:
...
    ```

---

    ## 52. Prompt Anti-Pattern Detection

    **Meaning**  
    ตรวจจับข้อผิดพลาดในการออกแบบ prompt ที่พบบ่อย

    **Description**  
    เช่น คำสั่งกว้างเกินไป ข้อจำกัดไม่ชัด format ไม่ชัด มีหลายเป้าหมายปะปน หรือใช้คำกำกวม

    **Suggested Structure**  
    ```text
    Prompt -> Detect anti-patterns -> Explain impact -> Rewrite better version
    ```

    **How to Apply with OpenAI GPT**  
    ใช้กับ GPT เพื่อ audit prompt library และลดข้อผิดพลาดที่ทำให้ output ไม่นิ่ง

    **AI LLM Sample**  
    ```text
    Review the prompt below and detect common anti-patterns such as ambiguity, conflicting instructions, missing output format, and weak constraints.
Then rewrite it into a stronger version.

Prompt:
[paste prompt]
    ```

---
## รูปแบบการผสานแพตเทิร์นที่แนะนำ

### 1) สำหรับงานใช้งานประจำวัน
**Persona + Context Manager + Template + Validation**

### 2) สำหรับงานวิเคราะห์ธุรกิจ
**Cognitive Verifier + Alternative Approaches + Fact Check List**

### 3) สำหรับงาน automation
**Planner-Executor + Tool Selection + JSON Schema + Prompt Pipeline**

### 4) สำหรับงาน Prompt Engineering
**Prompt Compiler + Prompt Debugger + Prompt Refactor + Prompt Benchmark**

### 5) สำหรับระบบ agentic workflow
**ReAct + Multi-Agent Collaboration + Conversation Memory + Context Window Reset**

## แนวทางการใช้บน GitHub
- ใช้ไฟล์นี้เป็น **reference catalog**
- ภายหลังสามารถแยกเป็นหลายไฟล์ได้ หากต้องการให้ 1 pattern ต่อ 1 ไฟล์
- นำ sample prompts ไปต่อยอดเป็น internal prompt library ได้
- เพิ่ม section “tested examples” ของทีมคุณใต้แต่ละ pattern ได้ภายหลัง

## ชื่อไฟล์ที่แนะนำสำหรับ repository
- `README.md`
- `prompt-ai-52-patterns-gpt.md`
- `prompt-pattern-catalog-gpt-th.md`
