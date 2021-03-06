---
published: true
title:  "[TIL] 재귀함수"
excerpt: "[자료구조/알고리즘] 기초 - 재귀"

categories:
  - TIL
tags:
  - [Algorithm, 자료구조, 재귀함수, Recursion, TIL]

toc: true
toc_sticky: true
 
date: 2021-08-24 19:03:00
last_modified_at: 2022-03-21 19:04:00
---

## 들어가기 전에
섹션 2에 들어오고 처음으로 배우는 자료구조와 알고리즘 파트!  
여전히 내가 섹션 1을 무사히 마치고 섹션2에 왔다는 것에 안심 반, 걱정 반인 마음이다.  
일부러 재수강하는 분들도 있다는데 내가 와도 되는 걸까 싶은 마음...  
그래도... 저번에도 말했듯 정신 빠짝 차려서 내가 통과될 만하니까 온 거라는 자신감을 갖고 나아가자!  


# [자료구조/알고리즘] 기초 - 재귀  
## 재귀 소개  
어떤 문제가 있다고 가정해 보자. 이 문제를 동일한 구조의 더 작은 문제로 나눌 수 있고(쪼개기), 이 작은 문제를 해결함으로써 전체 문제를 해결하는 방법을 재귀(recursion)라고 한다.  
재귀를 사용한 코드는 대부분 더욱 간결하고, 이해하기 쉽다. 그 밖에도 재귀는 알고리즘 문제의 많은 부분을 차지한다.  

## Achievement Goals  
**Lesson - 재귀 함수**  
* 재귀의 의미에 대해서 이해하고, 자바스크립트에서 재귀 호출을 할 수 있다.  
* 재귀를 언제 사용해야 하는지 알고 있다.  
* 재귀적 사고 연습을 통해 재귀 함수를 base case와 recursive case로 나눠서 작성할 수 있다.  
* 자료 구조 중 Tree 구조에 재귀 함수를 사용하는 이유를 이해할 수 있다.  
  * 실생활에 사용되는 유용한 Tree 구조를 알고 있다.  
  * 깊이를 알 수 없는 Tree 구조에 재귀 함수를 활용하여 모두 순회(traverse)할 수 있다.  

<br>

## 재귀의 이해 - 다르게 생각하기  
이번 유닛엔 조금 특별한 문제 해결 방법을 배우게 된다. 이번 유닛의 학습목표는 재귀를 학습하고 연습하면서 하나의 문제를 해결하기 위해 다양한 방식으로 생각하는 능력을 기르는 것이다.  

이 새로운 문제 해결 방법을 학습하기 전에, 다음의 간단한 문제를 해결해 볼 것이다.  

> 문제.  
> 자연수로 이루어진 리스트(배열)를 입력받고, 리스트의 합을 리턴하는 함수 `arrSum` 을 작성하세요.  
> 바로 정답을 확인하지 말고, 직접 코드를 작성하세요.  


**내가 푼 코드**
```js
function arrSum(arr) {
  let sum = 0;
  for (let i = 0; i < arr.length; i++) {
      sum += arr[i];
  }

  return sum;
}
```

### 정답  
* 자연수로 이루어진 리스트(배열)의 합을 구하는 알고리즘  
  a. 보조 변수 sum을 0으로 초기화한다.  
  b. 순차적으로 리스트(배열)의 구성요소에 접근하면서 sum에 더한다.  
* 코드
```js
function arrSum(arr) {
  let sum = 0;
  for (let i = 0; i < arr.length; i++) {
    sum += arr[i];
  }
  return sum;
}
```
<center>[코드] 자연수로 이루어진 리스트(배열)의 합을 구하는 arrSum</center>
<br>

이번에는 이 문제를 다른 각도에서 생각해 보겠다.  
자연수로 이루어진 리스트(배열) `[10, 3, 6, 2]`의 합을 구한다고 가정하자.  
1. 전체 리스트 `[10, 3, 6, 2]`의 합을 구하는 건 잠시 잊어버리자. 대신에 `[3, 6, 2]`의 합을 구하는 방법을 생각해 본다.  
  * `[10, 3, 6, 2]`보다는 `[3, 6, 2]`의 길이가 더 짧아서, 비교적 쉽게 풀릴 것 같다. 리스트 `[3, 6, 2]`의 합을 구하는 방법을 알아냈다면, 이 값에 `10`을 더해 주어진 문제인 리스트 `[10, 3, 6, 2]`의 합을 구할 수 있다.  
2. 리스트 `[3, 6, 2]`의 합을 구하는 게 조금 버겁다. 대신에 `[6, 2]`의 합을 구하는 방법을 생각해 보자.  
  * 1과 같은 이유로 `[3, 6, 2]`보다는 `[6, 2]`의 길이가 더 짧다. `[6, 2]`의 합을 구하는 방법을 알아냈다면, 이 값에 `3`을 더해 리스트 `[3, 6, 2]`의 합을 구할 수 있다.  
  * `arrSum([3, 6, 2]) = 3 + arrSum([6, 2])`  
3. 같은 이유로 `[6, 2]` 대신 `[2]`의 합을 구하는 방법을 생각해 보자. `[2]`의 합에 `6`을 더해 `[6, 2]`의 합을 구할 수 있다.  
4. `[2]`의 합을 구하는 건 매우 간단합니다. `2`다.  
<br>
이 과정을 아래의 간단한 코드로 표현할 수 있다.  

```js
arrSum([10, 3, 6, 2]) = 10 + arrSum([3, 6, 2]);
arrSum([3, 6, 2]) = 3 + arrSum([6, 2]);
arrSum([6, 2]) = 6 + arrSum([2]);
arrSum([2]) = 2 + arrSum([]);
arrSum([]) = 0;
```
<br>

## 문제를 쪼개어 생각하는 방법  
이처럼 어떤 문제를 해결할 때, 동일한 구조의 더 작은 문제를 해결함으로써 주어진 문제를 해결하는 방법을 **재귀(recursion)**라고 한다.  
재귀의 과정을 위에서 다뤘던 `arrSum`에 적용하면, 다음과 같다.  

1\. 기존의 문제에서 출발하여 더 작은 경우를 생각한다.  
  ```js
  arrSum([10, 3, 6, 2]) = 10 + arrSum([3, 6, 2]);
  ```  
  <center>[코드] arrSum에 적용할 문제를 더 작게 쪼갠다.</center>
<br>
2\. 같은 방식으로, 문제가 더는 작아지지 않을 때까지 더 작은 경우를 생각한다.  
  ```js
  arrSum([3, 6, 2]) = 3 + arrSum([6, 2]);  
  arrSum([6, 2]) = 6 + arrSum([2]);  
  arrSum([2]) = 2 + arrSum([]);  
  ```
  <center>[코드] arrSum에 적용할 문제를 가장 작은 단위까지 쪼갠다.</center>  
<br>
3\. 문제가 간단해져서 바로 풀 수 있게 되는 순간부터 앞서 생성한 문제를 차근차근 해결한다.  

```js
arrSum([]) = 0; // <-- 문제가 더는 작아지지 않는 순간
// 가장 작은 경우의 해결책을 적용한다.
arrSum([2]) = 2 + arrSum([]) = 2;
arrSum([6, 2]) = 6 + arrSum([2]) = 6 + 2 = 8;
arrSum([3, 6, 2]) = 3 + arrSum([6, 2]) = 3 + 8 = 11;
arrSum([10, 3, 6, 2]) = 10 + arrSum([3, 6, 2]) = 10 + 11 = 21;
```
<center>[코드] 가장 작은 단위부터 arrSum을 적용하여 문제를 푼다.</center>
<br>
다음과 같이, `arrSum`을 보다 엄밀하게(formally) 정의할 수 있다.  

```js
/*
 * 1. arr이 빈 배열인 경우 = 0
 * 2. 그 외의 경우 = arr[0] + arrSum(arr2)
 *   (arr2는 arr의 첫 요소를 제외한 나머지 배열)
 */
arrSum(arr);
```
<center>[코드] 함수 arrSum의 엄밀한 정의</center>
<br>
만약 함수 `arrSum`을 JavaScript 코드로 구현할 경우 (코플릿 과제 중 하나!), 함수 `arrSum`은 (인자가 빈 배열이 아닌 경우) 실행 과정 중에 자기 자신을 호출한다! 이러한 호출 방식을 **재귀 호출**이라고 한다.  

## 재귀는 언제 사용하는 게 좋을까?  
재귀는 다음과 같은 상황에서 매우 적합하다.  
1. 주어진 문제를 비슷한 구조의 더 작은 문제로 나눌 수 있는 경우  
2. 중첩된 반복문이 많거나 반복문의 중첩 횟수(number of loops)를 예측하기 어려운 경우  

```js
for (let i = 0; i < n; i++) {
    for (let j = 0; j < n; j++) {
        for (let k = 0; k < n; k++) {
            for (let l = 0; l < n; l++) {
                for (let m = 0; m < n; m++) {
                    for (let n = 0; n < n; n++) {
                        for (let o = 0; o < n; o++) {
                            for (let p = 0; p < n; p++) {
                                // do something
                                someFunc(i, j, k, l, m, n, o, p);
                           }
                        }
                    }
                }
            }
        }
    }
 }
```
<br>

모든 재귀 함수는 반복문(while문 또는 for문)으로 표현할 수 있다.  
그러나 재귀를 적용할 수 있는 대부분의 경우, 재귀를 적용한 코드가 더욱 간결하고 이해하기 쉽다.  

재귀의 개념과 코플릿을 다 풀었다면 다음의 키워드를 구글링하고 TIL을 작성해 보자.  
(재귀 함수로 작성한 경우와 그렇지 않은 경우로 비교해 보기.)  
* 재귀 함수와 메모리 사용량 간의 관계 (javascript recursion memory leak)  
* 꼬리 재귀 (tail recursion in js)  
* 하노이의 탑 재귀 (js tower of hanoi in recursion)  
* 조합 재귀 함수 (js combination in recursion)  

이 밖에도, 재귀는 알고리즘 문제의 많은 부분을 차지한다.
기업의 입사 시험(코딩 테스트, 알고리즘 테스트 등)이나 직무면접에서 활용할 수 있기 때문에, 기초를 확실하게 다져두는 게 바람직하다. << 중요!!


## 재귀적 사고 연습하기  
재귀는 자전거를 타는 것과 비슷하다.  
자전거 타는 법을 처음 배울 때, 다른 사람이 타는 것을 옆에서 지켜보면 꽤 쉬워 보인다. 그러나 막상 내가 타려고 하면, 생각보다 잘 안됩니다.  
자전거를 잘 타는 방법은 계속 시도하고 연습하는 수밖에 없다. 재귀 역시 마찬가지다.  
자연스러워질 때까지 연습해야 한다. 이번 파트에서 재귀적 사고를 더욱 쉽게 할 수 있는 가이드를 나열하고자 한다. 이 가이드를 따라 코플릿이나 다른 곳의 재귀 파트 코딩 문제를 지속해서 풀다 보면, 재귀적으로 생각하는 방법을 익히고 재귀를 더욱더 쉽게 활용할 수 있을 것이다.  

개인적으로 '이건 반복행동으로 풀 텐데 스마트한 방법으로 풀 수 있을 것 같다' 싶으면 재귀를 생각해 보면 좋을 거 같다.  

### Guide : 재귀적으로 사고하기  

**1. 재귀 함수의 입력값과 출력값 정의하기**  
재귀 함수를 통해 풀고자 하는 문제, 즉 도달하고자 하는 목표를 정의하는 데 도움이 된다.  
재귀적으로 사고하는 데에 가장 먼저 해야 할 일은 문제를 가장 추상적으로 또는, 가장 단순하게 정의하는 것이다.  
함수 arrSum의 경우 `number` 타입을 요소로 갖는 배열을 입력으로 받고, `number` 타입을 리턴한다. 이를 좀 더 간단하게 표기하면 다음과 같다.  
* `arrSum: [number] => number`  
<br>

**2. 문제를 쪼개고 경우의 수를 나누기**  
주어진 문제를 어떻게 쪼갤 것인지 고민한다.  
문제를 쪼갤 기준을 정하고, 정한 기준에 따라 문제를 더 큰 경우와 작은 경우로 구분할 수 있는지 확인한다.  
일반적으로, 입력값으로 이 기준을 정한다. 이때 중요한 관점은 입력값이나 문제의 순서와 크기. 주어진 입력값 또는 문제 상황을 크기로 구분할 수 있거나, 순서를 명확하게 정할 수 있다면 문제를 구분하는 데 도움이 된다.  
그리고 구분된 문제를 푸는 방식이 순서나 크기에 관계없이 모두 같다면, 문제를 제대로 구분한 것이다.  
* 함수 `arrSum`의 경우 입력값인 리스트(배열)의 크기에 따라, 더 작은 문제로 나눌 수 있다. 그리고 `arrSum([1, 2, 3, 4])`를 구하는 방법과 `arrSum([2, 3, 4])`을 구하는 방법은 동일하므로, 이 구분은 적절하다고 판단할 수 있다.  
이제 문제에서 주어진 입력값에 따라, 경우의 수를 나눈다. 일반적으로 문제를 더 이상 쪼갤 수 없는 경우와 그렇지 않은 경우로 나눈다.
* 함수 `arrSum`은 입력값이 빈 배열인 경우와 그렇지 않은 경우로 나눌 수 있습니다. 각각의 경우는 다른 방식으로 처리해야 합니다.  
* `arrSum: [number] => number`  
  `arrSum([ ])`  
  `arrSum([e1, e2, ... , en])`  
<br>

**3. 단순한 문제 해결하기**  
문제를 여러 경우로 구분한 다음에는, 가장 해결하기 쉬운 문제부터 해결한다.
이를 재귀의 기초(base case)이라고 부른다. 재귀의 기초는 나중에 재귀 함수를 구현할 때, 재귀의 탈출 조건(재귀 호출이 멈추는 조건)을 구성한다.  
* 함수 `arrSum`을 더 이상 쪼갤 수 없는 경우는 입력값이 빈 배열일 경우이고, 이때 `arrSum([])`의 리턴값은 0이다.  
* `arrSum: [number] => number`  
  `arrSum([ ]) = 0`  
  `arrSum([e1, e2, ... , en])`  
<br>

**4. 복잡한 문제 해결하기**  
남아있는 복잡한 경우를 해결한다.  
* 길이가 1 이상인 배열이 함수 `arrSum`에 입력된 경우, 맨 앞의 요소에 대한 결과를 따로 구하고(배열의 맨 앞의 요소이기 때문에 `head`라고 명명.), 나머지 요소를 새로운 입력값으로 갖는 문제로 구분하고, 이를 해결하여 얻은 결과를 `head`에 더한다.  
* `arrSum: [number] => number`  
  `arrSum([ ]) = 0`  
  `arrSum([e1, e2, ... , en]) = e1 + arrSum([e2, ..., en])`  
* 배열을 `head`와 나머지 부분(`tail`)으로 구분하는 방법만 안다면, 함수 arrSum을 재귀적으로 구현할 수 있다.  
<br>

**5. 코드 구현하기**  
```js
function arrSum(arr) {
  //Base Case : 문제를 더 이상 쪼갤 수 없는 경우 (재귀의 기초)
  if (arr의 길이가 0인 경우) {
    return 0;
  }
  /*
  * Recursive Case : 그렇지 않은 경우
  * 문제를 더 이상 쪼갤 수 없는 경우
  * head: 배열의 첫 요소
  * tail: 배열의 첫 요소만 제거된 배열
  */
  return head + arrSum(tail);
}
```
<br>

아래는 일반적인 재귀 함수의 템플릿이다. 재귀 함수 연습에 활용하면 좋다.  
```js
function recursive(input1, input2, ...) {
  // Base Case : 문제를 더 이상 쪼갤 수 없는 경우
  if (문제를 더 이상 쪼갤 수 없을 경우) {
    return 단순한 문제의 해답;
  }
  // recursive Case
  // 그렇지 않은 경우
  return 더 작은 문제로 새롭게 정의된 문제
  // 예1. someValue + recursive(input1Changed, input2Changed, ...)
  // 예2. someValue * recursive(input1Changed, input2Changed, ...)
}
```

<br/>
<br/>