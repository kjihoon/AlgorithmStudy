## (Day01)Recursion2

##### 수학함수 뿐만 아니라 다른 많은 문제들을 recursion으로 해결할 수 있다!!

```java
	public static void main(String[] args) {
		String str="hi my name is jihoon";
		System.out.println(count(str));
	}
	public static int count(String str) {
		if (str.isEmpty()) {
			return 0;
		}else {
			System.out.println(str);
			return 1+count(str.substring(1)); //substring(n) n번째 char 지우기
		}
	}
```

hi my name is jihoon
i my name is jihoon
 my name is jihoon
...
on
n

20

- 문자열 출력 알고리즘

```java
public static void printString(String str) {
		if (str.isEmpty()) {
			return;
		}else {
			System.out.print(str.charAt(0));
			printString(str.substring(1));
		}
}
```

- 배열 요소 합 알고리즘

```java
public int sum(int n,int [] data) {
		if (n<=0) {
			return 0;
		}else
			return sum(n-1,data)+data[n-1];
}
```



#### 주의

- 모든 recursion은 iterator로 변경가능하다
- 그 역도 성립
- recursion은 복잡한 알고리즘을 단순하고 알기쉽게 표현가능케 함
- 함수 호출에 대한 오버헤드가 있음 (매개변수 전달, activation frame 생성)