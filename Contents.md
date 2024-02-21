---
tags:
  - "#contents"
  - "#root"
aliases:
  - Root
---
![[Pasted image 20240220232318.png]]

```dataview
TABLE
FROM #note
WHERE index != null AND index != "-1"
SORT index ASC
```

```dataview
TABLE
FROM #answer
WHERE index != null AND index != "-1"
SORT index ASC
```
