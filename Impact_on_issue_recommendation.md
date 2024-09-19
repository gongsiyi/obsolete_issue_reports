When Tan et al. designed CrossFix, they did not consider obsolete issue reports. Given an open bug report, CrossFix can retrieve a list of relevant fixed bug reports with similar stack traces, triggering conditions, or titles. However, the recommended bug reports can be obsolete. Our ICLinker can help CrossFix to idenfify the obsolete recommended bug reports. According to our results, 36% of its recommendations are obsolete and we improve all such recommendations.

|aries|calcite|cassandra|derby|flink|geode|hbase|hive|nutch|
| :----------: | :----------: | :----------:|:----------: | :----------: | :----------: |:----------: | :----------: | :----------: |
|71|44|36|56|43|76|52|51|53|

Table 2. The reduced obsolete issue reports. Each project has 30 open issues, and CrossFix recommends 5 candidates for each open issue. In total, CrossFix recommends 150 candidates for each project. From the 150 candidates from each project, we reduce 71 (aries), 
44(calcite), 36 (cassandra), 56 (derby), 43 (flink), 76 (geode), 52 (hbase), 51 (hive), and 53 (nutch) obsolete issue reports. On average, we remove 36% of obsolete issue reports.


[1] Shin Hwei Tan, Ziqiang Li, and Lu Yan. 2023. CrossFix: Resolution of GitHub issues via similar bugs recommendation. Journal of Software: Evolution and Process (2023), e2554.