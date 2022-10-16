# III. 함수

---

## 1. 기본적인 함수 구현

typescrip와 기본적인 구조가 비슷하다.

```
func sum(a int, b int) int {
    return a + b
}
```
위의 예시를 보면 알 수 있듯,
함수의 매개변수 이름 다음에 어떠한 자료형인지 써주고

함수명() 다음에 자료형을 써서 반환값의 자료형을 명시해준다.

---

## 2. 다양한 return 값을 가질 수 있음

본래 대부분의 언어는 함수 하나당 하나의 반환값을 가진다.
그러나 golang은 하나의 함수가 다양한 반환값을 가질 수 있다.

```
package main

import "fmt"

func printStdInfo() (int, string) {

	var stdNum int = 2018
	var name string = "hoon"

	return stdNum, name
}

func main() {
	var stdNum, name = printStdInfo()
	fmt.Printf("안녕하세요. %d학번 %s입니다.", stdNum, name)
}
```

[출력결과]
```
안녕하세요. 2018학번 hoon입니다.
```

---

## 3. 매개변수의 갯수를 동적으로 할당 받는 법

1. 사용법
함수의 매개변수의 타입 앞에 ... 을 추가해준다.

```
func repeateMe(words ...string){
    fmt.Println(words);
}

func main(){
    repeatMe("Jong", "Hoon", "Hi")
}
```

위와 같이 코드를 작성하면 배열의 형태로 출력된다.

```
[Jong Hoon Hi]
```

---

## 4. naked return

1. 함수의 반환 값의 type을 적어두는 곳에
함수의 반환 변수까지 선언할 수 있는 기능

```
func printStdInfo() (stdNum int, name string) {

	stdNum = 2018
	name = "hoon"

	return stdNum, name
}
```

---

## 5. defer
1. 정의
함수가 끝났을 때 추가적으로 어떤 동작을 할 수 있도록 해주는 기능

```
func printStdInfo() (stdNum int, name string) {

	defer fmt.Println("saved!")

	stdNum = 2018
	name = "hoon"

	return stdNum, name
}
```
