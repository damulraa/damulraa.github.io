---
title:  "Python Coding Convention"
excerpt: "Python Coding 표준 관련 miscellanies"

categories:
  - Blog
tags:
  - [Python, Development, Coding]
last_modified_at: 2019-09-15T05:30:00-08:00
---

### Coding Guide
* Local 변수에는 앞에 _ 를 붙이지 않는다.( function 내부에서만 사용하는 로컬변수 leading underscore )
* len(abc) != 0 -> abc
> ###### For sequences, (strings, lists, tuples), use the fact that empty sequences are false.
>
>Yes: if not seq:
>if seq:
>
>No: if len(seq):
>if not len(seq):

* 리스트 초기화 : list() -> []
* I am in <span style="font-family:Papyrus; font-size:2em; color:red">LOVE!</span>
* for loop에 enumerate 사용하여 count = count + 1 제거
  * ```python for idx, value in enumerate([1,2,3,4,5], 1) ```
  * ```python for tuple_item in enumerate([1,2,3,4,5])```
* 문자열 + 보다는 string{}.{}'.format( , ,...) 형식 그리고, zfill(2) 보다는 {:02}로 formatting