# 2022 04 28 

```javascript
function solution(N, stages) {
    const geq = x => 
						stages
            .filter(y=> x <=y)
            .length
    const greaterMap = 
						Array(N+1)
	          .fill(0)
            .map((x,i)=>geq(i+1))
    const failRate = x => 
            greaterMap[x]===0
              ?0
              :(greaterMap[x]-greaterMap[x+1])/greaterMap[x]
    return Array(N)
            .fill(0)
            .map((x,i)=>[i+1,failRate(i)]) // [stage, rate]
            .sort((a,b)=>b[1]-a[1]) // rate 기준으로 정렬
            .map(x=>x[0]) // stage 번호를 가져온다
}
```

프로그래머스 문제를 푸는 과정에서, 위와 같이 작성을 했는데,
같이 스터디를 진행하는 많은 분들이 코드를 읽기 힘들다고 하셨다.

failRate  같은 함수가 특히 그런데, 이 부분에 대해서 

`실패율 = 1 - 성공률` 같은 개념을 조금 더 직관적으로 표현하는 것이 낫지 않았을까 생각이 든다.


