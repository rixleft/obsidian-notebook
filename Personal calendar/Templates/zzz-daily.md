<%*
let today = tp.date.now("YYYY-MM-DD");
let inputDate = await tp.system.prompt("输入示例："+today,today);
titleName = window.moment(inputDate, "YYYY-MM-DD",true).format("YYYY-MM-DD_ddd");

before_date = window.moment(inputDate, "YYYY-MM-DD",true).add(-1,"days").format("YYYY-MM-DD_ddd");

after_date = window.moment(inputDate, "YYYY-MM-DD",true).add(1,"days").format("YYYY-MM-DD_ddd");

let createTime = tp.file.creation_date();
let modificationDate = tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss");
-%>

---
create time : <% createTime %>
modification date: <% modificationDate %>

---

<< [[<% before_date %>]] | [[<% after_date %>]] >>

<% tp.web.daily_quote() %>
<% tp.web.random_picture("200x200", "landscape,water") %>

#### Business of today
-  ==Content==
	- [ ] Mood:
	- [ ] Weather:
	- [ ] Review and reflection:
	- [ ] Uncompleted transaction:
	- [ ] Tag:
	- [ ] Idea:
- Work
	- 
- Summary
	- [[会议检查清单]]
	- [[Workbench]]
	
#### 阅读笔记 & 会议纪要
通常记录一些需要技术阅读的内容

#### 间歇日记

<%*
await tp.file.move("/Personal calender/Daily/" + titleName)
tp.file.cursor()
-%>