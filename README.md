# PLawbench

# Introduction
PLawBench is a rubric-based benchmark designed to evaluate the performance of large language models (LLMs) in legal practice. It includes three legal tasks: legal consultation, case analysis, and legal document drafting, covering a wide range of real-world legal domains such as personal affairs, marriage and family law, intellectual property, and criminal litigation. The benchmark aims to evaluate LLMs’ practical capabilities in handling practical legal tasks.

![Image text](https://github.com/alexssss-vc/PLawbench/blob/main/Images/over%20review.png)

Overall framework of PLawBench illustrates a four-step pipeline:collecting multi-source legal data,expert annotation into three task types,LLM-based inference on these tasks,and rubric-based evaluation of the LLM outputs by a judge model.

1. In the public legal consultation task, we draw on situations commonly encountered by lawyers to simulate the interaction between clients and lawyers. This task tests whether the model can correctly understand users’ legal needs, thereby identifying and eliciting key facts that remain undisclosed by the parties.
   
2. In the case analysis task, each case is structured into four parts: conclusion, legal facts, reasoning, and legal provisions, with dedicated rubrics designed for each. For selected questions, we further specify particular legal reasoning paths to assess the model’s ability to conduct structured and sound legal reasoning in real-world cases.
   
3. In the legal document drafting task,  models are required to generate legal documents, such as complaints and statements of defense, based on provided scenarios. This task aims to evaluate the models' proficiency in professional legal writing.

A contrasting example:rubric-based approach(Evaluation B)can identify situations that appear accurate on the surface but are actually flawed in the reasoning process,while rubric-free approach (Evaluation A)cannot do this, potentially exposing users to significiant legal risks in practice.

![image text](https://github.com/alexssss-vc/PLawbench/blob/main/Images/Figure2.png)


Dataset Description:

You can check Example Questions.json to see 3 examples of our benchmark (they have been translated into English).

And we also open source some questions of our benchmark:

Task1:Public Legal Consultation.json consists of legal consultation questions. We have open-sourced a total of 18 questions, including the consultation scenarios and scoring rubrics.

Task2:Practical Case Analysis.jsonl consists of case analysis questions. We have open-sourced a total of 250 questions, including the questions, reference answers, scoring rubrics, and score sheets. 

Task3:Legal Document Generation defendant.json and Task3:Legal Document Generation plaintiff.json are legal writing tasks for drafting statements of defense and complaints, respectively. We have open-sourced a total of 12 questions in total, including the writing scenarios and scoring rubrics.

# Experiment Results
The ranking below presents the models' scores. In addition,we design a set of Sophisticated Cases:

![Image text](https://github.com/alexssss-vc/PLawbench/blob/main/Images/Figure3.png)

Two legal reasoning modes:Clear-out Cases judged directly by matching key point (top), and Sophisticated Cases evaluated through step-by-step legal reasoning over intermediate questions (bottom).
This Figure shows Performance Drop in reasoning tasks under sequential constraints.

![Image text](https://github.com/alexssss-vc/PLawbench/blob/main/Images/Table-5.png)

# Contributions
Our work makes three main contributions:

1.More realistic simulation of legal practice:We faithfully simulate real-world legal practice scenarios, with all tasks adapted from authentic cases. The benchmark organizes legal tasks into three hierarchical levels—public legal consultation, practical case analysis, and legal document generation—reflecting the full workflow of legal practi- tioners and enabling a comprehensive evaluation of LLM performance across diverse legal tasks. 

In real legal practice, user queries are often vague, logically inconsistent, emotionally charged, or even intentionally incomplete. While preserving the core logic of real cases, we deliberately amplify these cognitively challenging elements—such as ambiguous descriptions, omitted key facts, and misleading details—to assess whether LLMs can effectively operate under realistic legal consultation conditions.

2.Fine-Grained Reasoning Steps:Beyond evaluating final outcomes, our benchmark explicitly incorporates fine-grained legal reasoning steps into task design and evaluation. This allows us to examine whether LLMs can perform multi-stage legal reasoning, including issue identification, fact clarification, legal analysis, and conclusion validation,rather than relying on shallow pattern matching or surface-level reasoning.

3.Task-Specific Rubrics:Our evaluation framework adopts personalized, task-specific rubrics annotated by legal experts, moving beyond purely outcome-based or form-based metrics to assess substantive legal reasoning and decision-making processes.For each type of legal task, legal experts first define a rubric framework tailored to the task’s reasoning requirements. Subsequently, they annotate case-specific rubrics for each individual legal scenario. This two-stage annotation process ensures that evaluation criteria are both principled and context-sensitive, enabling a more fine-grained,comprehensive, and realistic assessment of LLM performance in legal practice settings.

# Ranking
|Models                               |Overall|Task1:Public Legal Consultation|Task2:Practical Case Analysis|Conclusion|Facts|Reasoning|Statute|Task3:Legal Document Generation|Defendant|Plaintiff|
|:------------------------------------|:----------:|:-----------------------------:|:---------------------------:|:--------:|:---:|:-------:|:-----:|:-----------------------------:|:-------:|:------:|
| GPT5.2-1211-global                  |68.13|79.57|66.37|69.93|88.26|60.38|48.59|63.42|68.58|58.25|
| GPT5-0807-global                    |65.87|83.67|63.93|66.91|87.32|61.99|35.75|57.24|66.50|47.98|
| gemini3.0-pro-preview               |65.16|65.27|64.99|71.75|78.73|64.64|45.98|65.36|65.30|65.41|
| claude-sonnet-4-5-20250929          |64.20|67.26|67.37|67.53|88.41|62.95|48.44|56.54|58.80|54.28|
| Qwen3-max-20250923                  |64.10|75.76|67.17|67.52|90.97|62.75|45.10|53.38|57.43|49.33|
| Gemini2.5-Pro-0617                  |62.54|71.28|63.82|69.59|78.29|63.94|43.49|54.57|58.25|50.88|
| kimi-k2-0711-preview                |60.64|67.27|62.16|65.55|81.96|58.56|43.28|53.68|60.71|46.65|
| DeepSeek-V3.2 -exp-inner            |58.43|70.01|63.93|63.99|86.49|59.23|43.95|41.54|48.74|34.33|
| Qwen3-235b-a22b-thinking-2507       |55.74|60.64|64.84|64.83|89.23|59.97|43.49|37.32|44.37|30.26|
| GPT-4o-0806                         |39.26|47.10|42.00|54.83|67.90|34.90|16.15|29.47|33.88|25.05|

Overall performance(%)of evaluated models across three primary tasks. Task 2 Average denotes the aggregate scoring rate derived from the specific rubrics of all four sub-dimensions. The overall score is calculated as a weighted mean of Tasks 1,2,and 3 (with weights 2:5:3, reflecting the number of questions in each task).

# Leader Board

![Image text](https://github.com/alexssss-vc/PLawbench/blob/main/Leaderboard.png)
