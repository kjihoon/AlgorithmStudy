## (Day01)Recursion3

#### 재귀함수의 기본 원칙!

- 최소 하나의 `base case` 반드시 필요
- 모든 case는 결국 `base case`에 수렴해야 함



#### 설계 원칙

- 암시적(implict) 매개변수를 명시적(explict) 매개변수로 바꾸어라.

```java
	//순차 탐색 알고리즘
	int search(int [] data,int n, int target) {
		for (int i=0;i<n;i++) {
			if(data[i]==target) {
				return i;
			}
		}
        return -1;
	}
// 위 함수의 목표는 data[0]에서 data[n-1] 사이에서 target을 검색하는 알고리즘이다.
// 이는 암묵적으로 검색 구간을 0 index에서 n-1 index까지를 보겠다는 암시적 매개변수이다.
// ** n만 적시했다, 시작구간을 적지않고 함수 정의함
```

```java
// 시작점과 끝점을 명시 in recursion
int search_recursion(int [] data,int begin,int end,int target) {
		if (begin>end) {
			return -1;
		}else if (target ==data[begin]) {
			return begin;
		}else {
			return search_recursion(data,begin+1,end,target);
		}
}
```

- 중요한 원칙임!
- 이 함수의 목표는 data[begin]에서 data[end] 사이에서 target을 검색한다.
- 즉. 검색구간에 시작점을 명시적으로 지정한다.

```java
int search_recursion2(int [] data,int begin,int end,int target) { 
		if (begin>end) {
			return -1;
		}else if (target ==data[end]) {
			return end;
		}else {
			return search_recursion(data,begin,end-1,target); //반대로도 가능
		}
}
```



- 최대값 찾기

```java
static int findMax(int data [], int begin,int end) {
		if (begin==end) { //base case는 구간(end-begin)의 길이가 0일때 return
			return data[begin];
		}else {
			return Math.max(data[begin],findMax(data,begin+1,end));
		}
}
```

```java
static int findMax2(int data[], int begin,int end) {
		// 두 구간으로 나누어서 최댓값 찾아서 비교
		if (begin==end) {
			return data[begin];
		}else {
			int middle = (begin+end)/2;
			int max1 = findMax2(data,begin,middle);
			int max2 = findMax2(data,middle,end);
			return Math.max(max1, max2);
		}
	}
```



#### 이진 트리 검색(Binary Search)

- 데이터가 정렬되어있다는 가정하에 데이터를 반으로 짜르고 그 타겟이 포함되지 않은 구간 제외 

```java
static int SearchBinary(int [] arr,int target,int begin,int end) {
		if (begin>end) {
			return -1;
		}else {
			int middle = (begin+end)/2;
			System.out.println(middle);
			if (arr[middle]==target) {
				return 1;
			}else if(arr[middle]>target){
				return SearchBinary(arr,target,begin,middle-1); 
			}else {
				return SearchBinary(arr,target,middle+1,end);
			}
		}
}
```

```java
static int SearchBinary2(String [] arr,String target,int begin,int end) {
		if (begin>end) {
			return -1;
		}else {
			int middle = (begin+end)/2;
			int compResult = target.compareTo(arr[middle]);
			if (compResult==0) {
				return 1;
			}else if(compResult<0){
				return SearchBinary2(arr,target,begin,middle-1); 
			}else {
				return SearchBinary2(arr,target,middle+1,end);
			}
		}
	}
```

### 매개변수를 명시적으로 표현하지 않으면 recursion에서 다음 recursion에 들어갈때 값을 표현하기 어려워진다!!



