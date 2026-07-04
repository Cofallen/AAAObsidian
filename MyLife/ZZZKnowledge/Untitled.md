# 高数

```dataview
TABLE WITHOUT ID
topic AS "知识点",
chapter AS "章节",
status AS "状态",
file.link AS "来源"

FROM "MyLife/Daily"

FLATTEN file.lists AS L

WHERE L.course

SORT chapter ASC
SORT topic ASC
```
