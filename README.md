# Understanding the Warning from Obsolete Issue Reports

## Research questions

In software development, programmers use issue trackers to manage maintenance issues and record valuable maintenance details in issue reports. With the evolution of software, open-source communities accumulate a huge amount of revision histories. In recent decades, mining software repositories have been a hot research topic. From issue reports and their patches, researchers have mined rich knowledge that is useful in assisting various programming tasks, e.g., locating bugs and vulnerabilities. Despite the successful stories, the learned knowledge can be unreliable or become obsolete with the evolution of software. Such knowledge is misleading and harmful. However, to the best of our knowledge, no study has explored this problem, and many research questions are still open. For instance, which knowledge can be learned? How can such knowledge become obsolete or unreliable?

To answer these questions, we build a tool, ICLinker, that calculates the obsolete ratios for issue reports. ICLinker links commits of a project to issue reports from the issue tracker system. It compares the commits with its corresponding latest source file, and calculates an obsolete ratio for each issue report. The obsolete ratio is calculated as the proportion of its added lines that cannot match the latest source files. With ICLinker, we answer the following research questions:

**RQ1. What kinds of knowledge can be learned from resolving issue reports?**

**RQ2. Can obsolete issue reports affect their knowledge?**

**RQ3. How many obsolete issue reports are there?**

**RQ4. How are obsolete issue reports mentioned in the code comments?**

## General protocol
To explore the knowledge, distribution, and references of obsolete issue reports, as shown in the following figure, our analysis protocol has the following steps:

![analysis_overview](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/analysis_overview.jpg)
Fig1. Analysis overview

*Step 1. Calculating the obsolete ratios of issue reports.* We build a tool, ICLinker, to inspect the obsolete issue reports and calculate the obsolete ratios. ICLinker calculates an obsolete ratio for each issue report. It indicates to what degree an issue report is obsolete. ICLinker calculates the obsolete ratio by comparing the latest source file with the added lines of its commit.

*Step 2. Categorizing the knowledge learned from resolving issue reports.* We collect 396 issue reports with obsolete ratios of 0 and 1 from 9 projects. For each issue report, we manually classify the knowledge learned from resolving the issue report by analyzing its content, the code modifications of corresponding commits, and commit messages.

*Step 3. Investigating whether obsolete issue reports can affect their knowledge.* We then manually check whether the learned knowledge is valid for the latest project. In this step, we analyze all the 396 issue reports. We use statistical hypothesis testing to check whether obsolete issue reports can affect their knowledge.

*Step 4. Discovering the references of obsolete issue reports from code comments.* For each obsolete issue report, we extract its issue number from code comments and analyze to what degree obsolete issue reports are mentioned in the code comments of the latest source files.


## Our findings

**RQ1. The Knowledge.** Based on whether the knowledge is specific to a project, we classify the knowledge into domain knowledge and project-specific knowledge. In particular, project-specific knowledge is learned for 75% of issue reports. The most frequent project-specific knowledge is about writing documents and algorithms, and the most frequent domain knowledge is about API calls (Finding 1).

![image](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/analysis_overview.jpg)
Fig1. Analysis overview

We manually classified the knowledge learned from resolving the issue report. The full taxonomy is as follows：
[RQ1](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/RQ1.xlsx)

**RQ2. The Effectiveness of Knowledge.** Obsolete issue reports significantly affect their embedded knowledge (Finding 2). Compared to domain knowledge, project-specific knowledge is more likely to be affected by obsolete issue reports. Among them, the initializations are the most affected knowledge, and its reduction of effectiveness ratio is 0.7128 (Finding 3).

![fresh_issue_reports](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/fresh_issue_reports.jpg)
Fig2a.The_distribution_of_effective_knowledge_from_fresh_issue_reports
![obsolete_issue_reports](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/obsolete_issue_reports.jpg)
Fig2b.The_distribution_of_effective_knowledge_from_obsolete_issue_reports
![effectiveness_ratio_reduction](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/effectiveness_ratio_reduction.jpg)
Fig3.The effectiveness ratio reduction of knowledge

**RQ3. The Distribution.** Projects with more commits typically have higher obsolete ratios (Finding 4). Recent issue reports have lower obsolete ratios than old issue reports. Despite the trends, obsolete issue reports are mixed with other issue reports (Finding 5).

![obsolete_ratios](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/obsolete_ratios_overview.jpg)
Fig4.The ratios grouped by projects

We identified the obsolete ratios of the issue reports from nine projects. Their obsolete ratios are as follows: 
[aries](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/aries.txt), [calcite](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/calcite.txt), [cassandra](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/cassandra.txt), [derby](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/derby.txt), [flink](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/flink.txt), [geode](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/geode.txt),  [hbase](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/hbase.txt), [hive](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/hive.txt), and [nutch](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/nutch.txt).

**RQ4. Reference in Code Comment.** The obsolete ratio medians of issue references in code comments are around 0.5, and obsolete references are mixed with other references (Finding 6).

![comment](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/comment.jpg)
Fig5.The references in comments



