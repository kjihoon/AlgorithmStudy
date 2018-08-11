## (Day01)Recursion1

#### 자기 자신을 호출하는 함수 (재귀 함수)

```java
public static void main(String[] args) {
		hello(6);
	}
	public static void hello(int k) {
		System.out.println("hello");
		hello(k-1);
}
```

hello
hello
hello
...

`stackover flow error` 발생!



#### 최소 하나의 recursion에서 빠져나가는 코드가 필요함

- Base case로 수렴해야함

``` java
public static void main(String[] args) {
		hello(3);
	}
	public static void hello(int k) {
		if (k==0) { //base case
			return;
		}else {
			System.out.println("hello");
			hello(k-1);
		}
}
```

hello
hello
hello

- recursion을 이용한 summation

```java
public static void main(String[] args) {
		int sum = func(10);
		System.out.println(sum);
	}
public static int func(int k) {
		if (k==0) { //base case
			return 0;
		}else {
			return k+func(k-1);
		}
}

// return 10+func(9)
// return (10+9)+func(8)
// return (10+9+8)+func(7)
// return ....
// return 10+9+8....+1+0
// 55
```

- recursion을 이용한 factorial

```java
public static void main(String[] args) {
		int fact = factorial(5);
		System.out.println(fact);
}
public static int factorial(int k) {
		if (k==0) {
			return 1;
		}else {
			return factorial(k-1)*k;
		}
}
//120
```

- power

```java
public static int power(int k,int x) {
		if (k==0) {
			return 1;
		}else {
			return x*power(k-1,x);
		}
}
```

- fibonacci

```java
public static int fibonacci(int k) {
		if (k<2) {
			return k;
		}else {
			return fibonacci(k-1)+fibonacci(k-2);
		}
}
```

- 최대공약수

```java
//최대공약수
public static int gcd(int m,int n) {
		if (m<n) { //swap m and n
			int tmp=m;
			m=n;
			n=tmp;
		}
		if (m%n==0)
			return n;
		else
			return gcd(n,m%n);
}

//나누어 떨어질때까지 gcd 재귀호출
```

