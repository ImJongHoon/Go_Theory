# I. go 프로젝트 만들기

---

## 1. 프로젝트 생성

go 프로젝트의 경우 go.mod 파일을 읽어서 모듈등을 추적한다. package.json과 유사함.

`mkdir go_project`
`cd go_project`

그리고 온라인 저장소와 연동? 한다.

`go mod init github.com/ImJongHoon/go_coin`

이후 main.go를 중심으로 프로젝트를 작성한다.
C언어처럼 컴파일러는 패키지 이름이 main.go인 파일을 우선적으로 compile 한다.

---

## 2. package선언하기

go 파일에서는

`package main`

으로 현재 package 이름을 입력해준다.

또 파일을 컴파일할때

`func main(){}`

을 가장 먼저 찾는다.

무릇 프로그래머라면 해봐야 할 hellow word 찍기

```
package main

import "fmt"

func main() {
	fmt.Println("Hello World!")
}

```

자신이 무슨 페키지인지 입력하는

`package main`

이 아니라, 자신이 무슨 패키지를 사용하는지는 import로 넣어준다.

c언어에서 #include 처럼

`import "name"`

으로 사용한다.

+++
추가적으로 go에서는 패키지에서 export한 함수는 첫 글자를 대문자로 만드는 암묵적인 룰이 있다.

`fmt.Println()`

에서 P가 대문자인 이유도 그와 같다.

이런 식으로 외부에서 사용하지 않는 private 함수인 경우 함수의 맨 앞글자는 소문자가 된다.

---

## 3. Variable
