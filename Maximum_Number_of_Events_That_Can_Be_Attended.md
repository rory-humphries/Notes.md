---
title: Maximum Number of Events That Can Be Attended
---

[LeetCode]: https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/description/

# Problem

> You are given an [array](Array.md) of `events` where `events[i] = [startDayi, endDayi]`. Every event `i` starts at `startDayi` and ends at `endDayi`.
>
> You can attend an event `i` at any day `d` where `startTimei <= d <= endTimei`. You can only attend one event at any time `d`.
>
> Return _the maximum number of events you can attend_.

- [LeetCode]

# Algorithm

| Complexity |               |
| ---------- | ------------- |
| Time       | $O(N\log{N})$ |
| Space      | $O(N)$        |

Where $N$ is the number of events.

## Intuition

```
1   2   3   4   5
|-------|
    |-----------|
    |---|
		|---|
		|-------|
```

The above example represents an example such that `events=[[1,3],[2,5],[2,3],[3,4],[3,5]]`. It is possible to attend 5 events in this case, but we must be careful of the days we attend them on. For example, if we were to  event `1` and `2` on day `2` and `3` respectively, we could not attend event `3`.

The idea behind the algorithm is to loop through every day we can attend an event.

A min [priority queue](Priority_Queue.md) holds all possible events which can be attended on a given day `k`. The queue order is determined from the last day of the events. The top of the queue is the event we visit on day `k`.

## Pseudo Code

```pseudo
function: maxEvents
	Input:  
		events, array of arrays where each element holds the start and 
			end days of every event, in that order.
    Output: 
	    integer, max events that can be attended.
    
	sort events accoring to first entry of every element

	// loop variables
	cur_event ← 0 // index of current event being considered
	day ← 1 // current day being considered 
	count ← 0 // return value
	
	pq ← a new minimum priority queue 
	// pq holds current event last day
	
	n ← length(events)

	while pq is not empty or cur_event < n do
		// remove any events already finished
		while pq is not empty and top(pq) < day do
			pop(pq)
		end while
		// add events starting today
		while cur_event < n and events[cur_event][0] = day do
			push(pq, events[cur_event][1])
			cur_event++
		end while
		// current event is attended
		if pq is not empty and top(pq) >= day then
			count+=1
			pop(pq)
		end if
		day+=1
	end while
```

## Implementation

A `C++` implementation:

```cpp
bool sortbyfirst(const vector<int> &a, const vector<int> &b) {
	return (a[0] < b[0]);
}

int maxEvents(vector<vector<int>>& events) {
	int n = events.size();
	std::sort(events.begin(), events.end(), sortbysec);
	// min queue
	std::priority_queue<int, std::vector<int>, std::greater<int>> pq;

	int count = 0;
	int day = 1;
	int ev = 0;

	while (ev < n || pq.size() > 0) {
		// remove any events already finished
		while(pq.size() && pq.top() < day) {
			pq.pop();
		}
		// add events starting today
		while (ev < n && events[ev][0] == day) {
			pq.push(events[ev][1]);
			ev++;
		}
		// current event is attended
		if(pq.size() && pq.top() >= day) {
			count++;
			pq.pop();
		}
		day++;
	}
	return count;
}
```
