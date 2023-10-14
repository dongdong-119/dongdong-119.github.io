---
title: "[C++] map과 unordered_map"
layout: post
categories: algorithm
tags: map unordered_map
date: 2023-10-14 09:00:00 +09:00
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


## unordered_map의 정렬
1. key로 정렬

  사실 map을 쓰면 key 기준 오름차순으로 자동정렬 해주기 때문에 굳이 unordered_map을 사용해야할까 싶습니다. 하지만 데이터가 많아지면 map은 해싱을 사용하는 unordered_map보다 데이터 탐색시 시간이 오래 걸리기 때문에 map대신에 unordered_map을 사용하고, key값으로 정렬하는 방식을 고려해볼 만합니다. 사실, 기본적으로 map은 binary search로 데이터를 탐색하기 때문에 일반적으로 모든 데이터를 훝는 방식보다는 성능이 좋지만, 혹시라도 unordered_map을 key로 정렬하는 해야할 일이 생긴다면, 다음의, <value로 정렬하는 방법>을 응용해서 사용하면 될 듯합니다. 

2. value로 정렬

  문자열이 여러개 주어지고, 1) 각 문자열이 등장한 빈도수가 높은 순서대로 2) 문자열 기준 사전순으로 unordered_map을 정렬합니다.


```c++

#include <vector>
#include <unordered_map>
#include <algorithms>
#include <iostream>
using namespace std;

// 1. 문자열의 빈도로만 정렬(내림차순) 
bool cmp_1(pair<string, int>& a, pair<string, int>& b) {
	return a.second > b.second;
}

// 2. 문자열의 빈도로 내림차순 정렬하고, 만약 빈도수가 같다면 문자열 기준으로 사전순으로 정렬
bool cmp_2(pair<string, int>& a, pair<string, int>& b) {
	if (a.second == b.second) // 문자열 빈도수가 같다면
		return a.first < b.first; // >> 문자열 기준 사전순으로 정렬

	return a.second > b.second; // 문자열 빈도수 내림차순으로 정렬(기본)
}


int main() {
	unorderd_map<string, int> cnt_map; 
	
	// 데이터 저장 -> key(과일이름) : value(빈도수, 임의로 저장) 
	cnt_map["apple"] = 1;
	cnt_map["pineapple"] = 5;
	cnt_map["banana"] = 5;

	vector<pair<string, int>> vec(cnt_map.begin(), cnt_map.end()); //map -> vector
	sort(vec.begin(), vec.end(), cmp_1(or cmp_2)); // 원하는 정렬 조건 넣어서 정렬
}


// result (vector 요소)
// 1. cmp_1로 정렬
// (("pineapple", 5), ("banana", 5), ("apple", 1));

// 2. cmp_2로 정렬 
// (("banana", 5), ("pineapple", 5), ("apple", 1));
// pineapple이 먼저 입력되었음에도 banana가 사전순으로 빠르기 때문에 앞선다.(cmp_1과의 차이)

```

