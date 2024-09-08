---
week: <% tp.date.now('ww',0, tp.file.title, 'YYYY-MM-DD') %>
tags: daily
---

<% tp.web.daily_quote() %>

# <% tp.date.now("dddd, MMMM Do YYYY", 0, tp.file.title, "YYYY-MM-DD") %>

[[ <% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %> |⬅️ Yesterday]] | [[<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>|➡️ Tomorrow]] | [[<% tp.date.now("YYYY-[w]WW", 0, tp.file.title, "YYYY-MM-DD") %>|📖 Weekly]] | [[<% tp.date.now("YYYY-MM", 0, tp.file.title, "YYYY-MM-DD") %>|📅 Monthly]]

```button
name Add to Log
type command
action QuickAdd: Capture to daily note
color default
```
^button-rjgc

## Daily Log


## [[Tasks Dashboard |Tasks]]

> [!overdue]+ Due before <% tp.file.title %>
> **Due before:** <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>
> ```tasks
> due before <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>
> not done
> hide due date
> hide recurrence rule
> group by function task.tags.map( (tag) => tag.split('/')[1] ? tag.split('/').slice(0, 2).join('/') : '')
> ```

> [!due-today]+ Due <% tp.file.title %>
> ```tasks
> due <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>
> not done
> hide due date
> hide recurrence rule
> group by function task.tags.map( (tag) => tag.split('/')[1] ? tag.split('/').slice(0, 2).join('/') : '')

> [!coming-soon]- Due soon after <% tp.file.title %>
> ```tasks
> due after <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>
> due before <% tp.date.now("YYYY-MM-DD", 4, tp.file.title, "YYYY-MM-DD") %>
> not done
> hide due date
> hide recurrence rule
> group by due
> group by function task.tags.map( (tag) => tag.split('/')[1] ? tag.split('/').slice(0, 2).join('/') : '')
> ```

> [!success]- Completed <% tp.file.title %>
> ```tasks
> done <% tp.date.now("YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>
> short mode
> ```

## 5 Minute Journal

### 🌞
**3 things I am grateful for...**
1. 

**What will I do to make today great?**
- 

**Daily affirmations**


### 🌚
**What were the highlights from your day?**
1. 

**How could I have made today even better?**


## Today's Notes

> [!example]- Created Today
> ```dataview
> table without id
> file.link as Note,
> file.folder as Folder,
> file.ctime as "Created"
> FROM ""
> where file.ctime >= date(<%tp.file.title%>) AND file.ctime <= date(<%moment(tp.file.title,'YYYY-MM-DD').add(1, 'd').format("YYYY-MM-DD")%>) AND file.path != this.file.path
> sort file.ctime desc
> ```

> [!example]- Modified Today
> ```dataview
> table without id
> file.link as Note,
> file.folder as Folder,
> file.mtime as "Last Modified"
> FROM ""
> where file.mtime >= date(<%tp.file.title%>) AND file.mtime <= date(<%moment(tp.file.title,'YYYY-MM-DD').add(1, 'd').format("YYYY-MM-DD")%>) AND file.path != this.file.path
> sort file.mtime desc
> ```

