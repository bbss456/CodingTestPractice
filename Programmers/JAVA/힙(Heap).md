# 힙(Heap)
>[더 맵게](https://school.programmers.co.kr/learn/courses/30/lessons/42626) 
###
나의 풀이
```
import java.util.*;
class Solution {
    public int solution(int[] scoville, int K) {
              PriorityQueue<Integer> queue = new PriorityQueue<>();

        for(int i = 0; i < scoville.length; i++) {
            queue.add(scoville[i]);
        }

        int answer = 0;
        while(queue.size() > 1 && queue.peek() < K){
            if(queue.size() <= 1 || queue.peek() > K) {
                break;
            }
            int weakHot = queue.poll();
            int secondWeakHot = queue.poll();

            int mixHot = weakHot + (secondWeakHot * 2);
            queue.add(mixHot);
            answer++;
        }

        if(queue.size() <= 1 && queue.peek() < K)
            answer = -1;

        return answer;
    }
}
```