---
layout : single
title : "Greedy Algorithm Questions"
date : 2020-04-23
categories : Algorithm College
use_math : true
---



# [그리디 알고리즘] 체육복 문제

안녕하세요! 그리디 알고리즘을 완전 정복하기 위해 '프로그래머스'라는 문제은행 사이트에서 가져온 그리디 알고리즘 문제인 '체육복' 문제를 풀어 보도록 하겠습니다!



## 문제 설명



### 문제

점심시간에 도둑이 들어, 일부 학생이 체육복을 도난당했습니다. 다행히 여벌 체육복이 있는 학생이 이들에게 체육복을 빌려주려 합니다. 학생들의 번호는 체격 순으로 매겨져 있어, 바로 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있습니다. 예를 들어, 4번 학생은 3번 학생이나 5번 학생에게만 체육복을 빌려줄 수 있습니다. 체육복이 없으면 수업을 들을 수 없기 때문에 체육복을 적절히 빌려 최대한 많은 학생이 체육수업을 들어야 합니다.

전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수를 작성해주세요.



### 제한사항

- 전체 학생의 수는 2명 이상 30명 이하입니다.
- 체육복을 도난당한 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌의 체육복을 가져온 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌 체육복이 있는 학생만 다른 학생에게 체육복을 빌려줄 수 있습니다.
- 여벌 체육복을 가져온 학생이 체육복을 도난당했을 수 있습니다. 이때 이 학생은 체육복을 하나만 도난당했다고 가정하며, 남은 체육복이 하나이기에 다른 학생에게는 체육복을 빌려줄 수 없습니다.



### 입출력 예

|  n   |  lost  |  reserve  | return |
| :--: | :----: | :-------: | :----: |
|  5   | [2, 4] | [1, 3, 5] |   5    |
|  5   | [2, 4] |    [3]    |   4    |
|  3   |  [3]   |    [1]    |   2    |



### 입출력 예 설명

예제 #1
1번 학생이 2번 학생에게 체육복을 빌려주고, 3번 학생이나 5번 학생이 4번 학생에게 체육복을 빌려주면 학생 5명이 체육수업을 들을 수 있습니다.

예제 #2
3번 학생이 2번 학생이나 4번 학생에게 체육복을 빌려주면 학생 4명이 체육수업을 들을 수 있습니다.



출처 : https://programmers.co.kr/learn/courses/30/lessons/42862



## 접근법 및 첫번째 소스코드

그리디 알고리즘의 핵심은 현재 상황에서 가장 최적의 해를 따라가는 것이고 뒤를 돌아보지 않는다는 것입니다. 

따라서 결과적으로 최적의 해가 나오지 않을 수 있지만 처리 속도는 월등히 빠릅니다.



여기서 포인트는 번호가 체격순으로 되어 있어서 여벌을 가진 사람의 앞번호 or 뒷번호에게만 체육복을 빌려 줄 수 있다는 것입니다. 

그렇다면 여벌을 가진 사람의 배열을 입력받아 순차적으로 도난당한 사람과의 번호를 비교하여 번호 차이가 1이면 빌려주는 형식으로 소스코드를 짜면 되지 않을까요?

일단 최댓값 answer는 학생 수 n에 lost.length를 빼주면 될 것입니다. 최소 도난당하지 않은 학생들은 체육수업을 들을 수 있기 때문이죠.

그리고 제한사항에서 나왔듯이 여벌 체육복을 가져온 학생이 도난을 당한 경우도 포함을 시켜줘야 합니다. 그 얘기는 여벌을 가지고 있는 사람의 배열 reserve와 도난당한 사람의 배열 lost에 같은 번호가 있을 가능성도 생각해 줘야한다는 것입니다. 그래서 먼저 reserve와 lost에 같은 숫자가 있는지, 있다면 각 배열에 음수를 집어넣어 아예 배제해버리는 방법을 생각 할 수 있습니다. 

그리고 같은 번호가 있다면 answer는 하나를 늘려줘야합니다. 왜냐하면 여벌을 가지고 있는 학생이 도난을 당했다면 ? 빌려주진 못하겠지만 그래도 자신은 체육 수업을 들을 수 있으니까 말입니다.

그렇게 해서 소스코드를 짜봤습니다.

```java
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int answer = n - lost.length;
        
        for (int i=0 ; i<lost.length ; i++) {
            for (int j=0 ; j<reserve.length ; j++) {
                if (lost[i] == reserve[j]) {
                    lost[i] = -1; //여벌이 있는 학생 중 도난 당한 학생의 경우!
                    reserve[j] = -1;
                    answer++;
                    break;
                }
            }
        }
            
        for (int i=0 ; i<reserve.length ; i++) { //순차적으로 비교하여 answer 늘리기
            if (reserve[i] < 0)
                continue;
            for (int j=0 ; j<lost.length ; j++) {
                if ((reserve[i] - 1 == lost[j]) || (reserve[i] + 1 == lost[j])) {
                    answer++;
                    lost[j] = -1; //도난당한 학생 빌리는 데 성공했으므로 배제
                    break;
                }
            }
        }
        
        return answer;
    }
}
```



이 소스코드로 '프로그래머스' 사이트에 돌려봤는데 성공 했습니다. 

그런데 여기서 의문점이 생겼습니다. 제가 이중for문을 사용했다는 것입니다. 

그렇다면 시간복잡도가 $$O(n^2)$$ 라는 것인데... 그리디 알고리즘의 이점을 잘 살리지 못했다는 생각이 들었습니다. 제한사항에서 학생 수 n이 30 이하여서 이 코드로 해결해도 간단하겠지만... 만약 엄청나게 큰 수를 넣는다면 이 코드는 효율적이지 못할 것이고 시간이 오래 걸릴 것입니다. 따라서 이중 for문을 사용하지 않고 코드를 작성해봐야겠습니다. 0.69~0.78ms



## 두번째 소스코드, 이중for문 삭제

이중for문으로 비교하지 않기 위해 새로운 학생 배열 s를 만들었습니다. 

학생 배열을 1로 초기화합니다. (모든 학생이 체육복 1개씩 갖고 있다고 가정).

 그리고 for(:)를 이용하여 lost배열의 숫자를 가져와 s배열의 숫자에서 1을 빼고 (도난당한 경우)

reserve배열의 숫자를 가져와 s배열에 숫자를 1 더합니다. (여분을 갖고 온 경우)

이렇게 하면 앞서 코드의 첫번째 이중for문이 사라지게 됩니다!



이렇게 되면 s배열 자기들끼리만 비교하기 때문에 역시 두번째 이중for문도 사라집니다.

최종적으로 s 배열에서 숫자가 1보다 큰 경우를 카운트하여 출력하면 됩니다.



```java
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int answer = 0;
        int[] s = new int[n+1];
        
        for(int i=1 ; i<=n ; i++)
            s[i] = 1; //모두 체육복을 갖고 있는 것으로 초기화
        
        for(int l:lost)
            s[l]--; //도난
        
        for(int r:reserve)
            s[r]++; //여벌
        
        for(int i=1 ; i<=n ; i++) {
            if(s[i] == 0) {
                if(i+1<=n && s[i+1]==2) { //뒷번호가 여벌이 있는 경우
                    s[i+1]--;
                    s[i]++;
                }
                else if(i-1>=1 && s[i-1]==2) { //앞번호가 여벌이 있는 경우
                    s[i-1]--;
                    s[i]++;
                }
            }
        }
        
        for(int i=1 ; i<=n ; i++) { //체육복을 하나 이상 갖고 있으면 수업에 참여하므로
            if(s[i]>=1)
                answer++;
        }
        
        return answer;
    }
}
```



근데, 너무 간단한 코드여서 그런지 실행 시간은 0.68~0.80ms 정도로 두 코드 비슷했습니다. 아마 ns정도 단위까지는 가야 시간이 차이가 나는 것 같습니다.

