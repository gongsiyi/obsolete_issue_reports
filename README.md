# Understanding Obsolete Knowledge Learned from Resolving Issues Reports

## Project summary

In software development, programmers use issue trackers to manage maintenance issues and record valuable maintenance details in issue reports. With the evolution of software, open-source communities accumulate a huge amount of revision histories. In recent decades, mining software repositories have been a hot research topic. From issue reports and their patches, researchers have mined rich knowledge that is useful in assisting various programming tasks, e.g., locating bugs and vulnerabilities. Despite the successful stories, the learned knowledge can be unreliable or become obsolete with the evolution of software. Such knowledge is misleading and harmful. However, to the best of our knowledge, no study has explored this problem, and many research questions are still open. For instance, which knowledge can be learned? How can such knowledge become obsolete or unreliable?

In this paper, we conducted the first empirical study about the unreliable knowledge to answer the above questions. In particular, we analyzed the issue reports and their patches from 9 Apache projects. We manually build a taxonomy of the knowledge learned from fixed issue reports and analyze whether they become obsolete or unreliable for the latest source files. We find that more project-specific knowledge is learned than domain knowledge from issue reports. In some issue reports, the added code lines of their patches are overwritten or rolled back. Based on this observation, we define an obsolete ratio of an issue report as its deleted lines over all its modified lines. We call an issue report obsolete if its added code lines are all deleted from the latest source files. We find that the obsolete ratios are correlated with unreliable knowledge in issue reports, especially for project-specific knowledge. Furthermore, we analyze the distribution of obsolete issue reports and their references in code comments. We find that obsolete issue reports are mixed with other issue reports. Besides deriving findings, we analyze how obsolete issue reports affect an issue recommendation approach. According to our results, 36% of its recommendations are obsolete and we improve all such recommendations.

## Our findings

**RQ1. How many obsolete issue reports are there?**
If a project has a long history, about 40% of its issue reports are obsolete. (Finding 1). Recent issue reports have lower obsolete ratios than old issue reports. (Finding 2).

We identified the obsolete ratios of the issue reports from nine projects. Their obsolete ratios are as follows: 
[aries](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/aries.txt), [calcite](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/calcite.txt), [cassandra](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/cassandra.txt), [derby](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/derby.txt), [flink](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/flink.txt), [geode](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/geode.txt),  [hbase](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/hbase.txt), [hive](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/hive.txt), and [nutch](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/nutch.txt).

**RQ2. What kinds of knowledge can be learned from resolving issue reports?**
Based on whether the knowledge is specific to a project, we classify the knowledge into domain knowledge and project-specific knowledge. In particular, project-specific knowledge is learned for 75% of issue reports. The most frequent project-specific knowledge is about writing documents and algorithms, and the most frequent domain knowledge is about API calls (Finding 3).

<table border="13" >
	<tr >
		<td rowspan="3">K1. Domain Knowledge(99/396, 25%)</td>
		<td>K1.1. API call (49/396, 12.37%)</td>
	</tr>
	<tr >
		<td>K1.2. Compile configuration (41/396, 10.35%)</td>
	</tr>
  <tr >
		<td>K1.3. Others (9/396, 2.27%)</td>
	</tr>
  	<tr >
		<td rowspan="10">K2. Project-specific Knowledge (297/396, 75%)</td>
		<td>K2.1. Document (message) (55/396, 13.89%)</td>
	</tr>
	<tr >
		<td>K2.2. Algorithm (54/396, 13.64%)</td>
	</tr>
  <tr >
		<td>K2.3. Configuration (45/396, 11.36%)</td>
	</tr>
  <tr >
		<td>K2.4. Test (44/396, 11.11%)</td>
	</tr>
  <tr >
		<td>K2.5. Initialization (28/396, 7.07%)</td>
	</tr>
  <tr >
		<td>K2.6. Debug (19/396, 4.80%)</td>
	</tr>
  <tr >
		<td>K2.7. Refactoring (13/396, 3.28%)</td>
	</tr>
  <tr >
		<td>K2.8. Script (11/396, 2.78%)</td>
	</tr>
  <tr >
		<td>K2.9. Annotations (10/396, 2.53%)</td>
	</tr>
  <tr >
		<td>K2.10. Others (18/396, 4.55%)</td>
	</tr>
</table>

Table 1. The full taxonomy of knowledge. $$ratio_{c} = \frac{N_{c}}{N_{all}}$$ where $N_{c}$ is the number of the knowledge in category $C$, and $N_{all}$ is the number of all the knowledge learned from resolving issue reports, i.e., 396.


We manually classified the knowledge learned from resolving the issue report. The details are in：
[RQ1_obsolete_ratio_1.md](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/RQ1_obsolete_ratio_1.md), [RQ1_obsolete_ratio_0.md](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/RQ1_obsolete_ratio_0.md)

**RQ3. Can obsolete issue reports affect their knowledge?**
Obsolete issue reports significantly affect their embedded knowledge (Finding 4). Compared to domain knowledge, project-specific knowledge is more likely to be affected by obsolete issue reports. Among them, the initializations are the most affected knowledge, and its reduction of effectiveness ratio is 0.7128 (Finding 5). The obsolete ratio of an issue report is an indicator of the obsolete knowledge (Finding 6).

|K2.5|K2.1|K2.10|K2.2|K1.3|K2.9|K2.4|K2.3|K2.8|K1.2|K2.6|K1.1 |K2.7|
| :------------- | :------------- | :-------------|:------------- | :------------- | :------------- |:------------- | :------------- | :------------- |:------------- | :------------- | :------------- |:-------------|
|0.7128|0.7082|0.6932|0.675|0.6000|0.5556|0.5427|0.5000|0.4545|0.4187|0.3462|0.1923|0.1667|

Table 2. The effectiveness ratio reduction of knowledge. $$reduction_{e_{c}} = \frac{N_{e_{c_{0}}}}{N_{c_{0}}} - \frac{N_{e_{c_{1}}}}{N_{c_{1}}}$$ where $N_{e_{c_{0}}}$ is the number of fresh issue reports whose knowledge is effective, $N_{c_{0}}$ is the number of total fresh issue reports, $N_{e_{c_{1}}}$ is the number of obsolete issue reports whose knowledge is effective, and $N_{c_{1}}$ is the number of total obsolete issue reports.

**RQ4. How do obsolete issues affect a recent approach?**
We also analyze how obsolete issue reports affect an issue-recommendation approach, called CrossFix [1]. Obsolete issue reports affect the results. In particular, 48.18% of its recommended issues are obsolete, and the obsolete ratio median is 0.4683 (Finding 7).

The details are in： [Impact_on_issue_recommendation.md (https://github.com/gongsiyi/obsolete_issue_reports/blob/main/Impact_on_issue_recommendation.md)




