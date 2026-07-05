---
score: 0
tags: daily
created: <% tp.date.now("YYYY-MM-DD HH:mm:ss") %>
---
🔙 [[MyLife/Yearly/<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY") %>|年度展望]] | 📂 [[MyLife/Monthly/<% moment(tp.file.title, "YYYY-MM-DD").format("YYYY-MM") %>|本月月记]] | 📅 [[MyLife/Weekly/<% moment(tp.file.title, "YYYY-MM-DD").format("gggg-[W]ww") %>|本周周记]] | 📝[[总览知识]]

---

> [!review]+ 📖 艾宾浩斯复习
> ```dataview
> LIST rows.L.text
> FROM "MyLife/Daily"
> WHERE
> file.day = date(this.file.day)-dur(1 day)
> OR file.day = date(this.file.day)-dur(2 days)
> OR file.day = date(this.file.day)-dur(3 days)
> OR file.day = date(this.file.day)-dur(7 days)
> OR file.day = date(this.file.day)-dur(14 days)
> OR file.day = date(this.file.day)-dur(30 days)
> FLATTEN file.lists as L
> WHERE contains(meta(L.section).subpath, "今日知识整理")
> GROUP BY file.link
> ```


## 📅 每日计划

- [ ] 

## 💡 灵感

- 

# ✍️ 今日知识整理  
  
- 

## 📝 总结与反思 

- 