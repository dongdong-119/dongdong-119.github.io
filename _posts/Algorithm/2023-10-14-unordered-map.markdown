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
|중복허용||X||X|
|기반||레드블랙트리||hash table기반 hash comtainer(해싱 가능)|
|메모리||보다 적게 든다||.|
|탐색시 시간복잡도||O(logN) - binary search||O(1) - hashing|
|문자열 길이가 길고 데이터가 크지 않을 때||보다 유리||길이에 그대로 반응하기 때문에 상대적으로 불리|

