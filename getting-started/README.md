# Getting Started

To start with the tool first thing you need is a report from another tool. Let's say you want analyze your project with [Gitleaks](https://github.com/zricethezav/gitleaks).

Because it is first time, you need to analyze all commits and it can be thousands of them. You got a report and it is full of findings, and a lof of them a duplicate, because one secret may appear in multiple commits. Here is where Purify can help you.

The logic hierarchy of Purify is simple: 

1. Project \(the root component\) 
2. Units \(the direct child of a project\) 
3. Reports \(belong to a unit\) 
4. Templates \(attached to a report and used to parse issues\) 
5. Issues \(extracted from a report and formatted based on a template\)



