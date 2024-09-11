# Understanding the Warning from Obsolete Issue Reports

## Project summary

In software development, programmers use issue trackers to manage maintenance issues and record valuable maintenance details in issue reports. Based on these issue reports, programmers have enhanced code comprehension and researchers have mined knowledge from issue reports to assist various programming tasks. Although issue reports are useful, some of them can be obsolete, in that their corresponding commits are overwritten or rolled back, with the evolution of software. The obsolete issue reports can affect their knowledge, references, and descriptions and have far-reaching impacts on the approaches built on them.

To deepen the understanding of obsolete issue reports, we conducted the first empirical study to analyze obsolete issue reports. We consider that an issue report is obsolete if its revisions are partially or entirely removed in later commits. To measure how an issue report becomes obsolete, we define an obsolete ratio of an issue report as its deleted lines over all its modified lines. In this paper, we build a tool, ICLinker, to inspect the obsolete issue reports and calculate the obsolete ratios. With ICLinker, we analyze 116,106 commits and 72,136 issue reports that are collected from 9 Apache projects. Taking them as our inputs, we explore four research questions, and explore the learned knowledge and the references of obsolete issue reports. Our findings on these research questions enrich the knowledge of obsolete issue reports, and some are even counterintuitive. For example, we find that obsolete issue reports are mixed with other issue reports. As another example, from issue reports, it is feasible to learn more project-specific knowledge than domain knowledge, and obsolete ratios of issue reports significantly affect their embedded knowledge, especially for project-specific knowledge. Furthermore, we analyze how obsolete issue reports affect an issue-recommendation approach. According to our results, we improve this approach by removing 36% of recommendations, which are obsolete.



## Our identified obsolete ratios

We identified the obsolete ratios of the issue reports from nine projects. Their obsolete ratios are as follows: 
[aries](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/aries.txt), [calcite](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/calcite.txt), [cassandra](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/cassandra.txt), [derby](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/derby.txt), [flink](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/flink.txt), [geode](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/geode.txt),  [hbase](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/hbase.txt), [hive](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/hive.txt), and [nutch](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/nutch.txt),.


## The full taxonomy of the knowledge

We manually classified the knowledge learned from resolving the issue report. The full taxonomy is as follows：
[aries](https://github.com/gongsiyi/obsolete_issue_reports/blob/main/aries.txt)
