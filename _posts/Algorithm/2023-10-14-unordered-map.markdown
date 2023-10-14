---
title: [C++] map과 unordered_map
layout: post
categories: algorithm
tags: map unordered_map
date:2000-00-00
#related_posts:
# - _posts/Back-end/<post_name.md>
---

c++에서 Map은 map과 unordered_map 을 주로 사용합니다*. 두 자료구조 모두 Key:Value 형태로 저장되지만, 데이터가 저장될 때 자동정렬여부와 탐색속도 등에서 차이가 발생합니다. 아래에 표로 간단히 정리해두었습니다


## map과 unordered_map의 비교
|항목|map|unordered_map|
|:---:||:---:||:---:|
|정렬||오름차순 자동정렬||정렬x|