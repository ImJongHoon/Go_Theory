# VII. Array, Slice, Maps, Struct

---

## 1. Go에서의 Array

C언어처럼 배열의 크기와 자료형을 모두 명시해야한다.

```
func main(){
    names:= [5]string{"Im", "Jong", "Hoon"}

    fmt.Println(names);
}
```

또 go역시 배열의 index는 0부터 시작한다.

---

## 2. Slice
배열의 크기에 제한 없이 요소를 추가하고 싶을 때 사용.
즉, 동적 배열을 따로 지원해준다.

그저 위 배열 선언에서 크기를 명시해주지 않으면 된다.

```
func main(){
    names:= []string{"Im", "Jong", "Hoon"}

    fmt.Println(names);
}
```

위처럼 이미 선언한 배열에 요소를 추가하기 위해서는
append() 함수를 사용한다. 두개의 인자를 필요로하는데
첫번째 인장는 slice 명, 두번째 인자는 끝이 추가하고 싶은 값이다.

```
append(names, "Hi");
```

---

## 3. Map
Python이나 JavaScript의 object와 유사한 자료형이다.
key 와 value를 선언하는 구조이다.

[] 안의 자료형이 vlaue의 자료형이고 ] 다음에 나오는 자료형이 value의 자료형이다.

```
func main(){
    name := map[string]string{"lastName": "Im", "firstName": "JongHoon"}
}
```

value에 다양한 자료형을 넣어주고 싶다면 Struct를 사용한다.

for문을 사용하는 예시

```
func main(){
    name := map[string]string{"lastName": "Im", "firstName": "JongHoon"}
    for key, value := range name{
        fmt.Println(key,value);
    }
}
```
반복문을 돌면서 알아서 key와 value를 차례대로 출력해준다.

---

## 4. Struct

구조체는 다른 언어의 object와 유사하면서도 map보다 자유로운 자료형이다.

구조체 정의 / 사용 두 부분으로 나눠진다.

사용은 class, 객체와 유사하게 사용한다.

```
//정의
type person struct {
    name string
    age int
    favFood []string
}
```

```
//사용
func main(){
    favFood := []string("ramen", "coffee");
    hoon := person{name:"JongHoon", age: 18, favFood: favFood}

    hoon.age
}
```

struct가 자주 사용되는 만큼 관련 method역시 잘 알아둬야 함.

struct를 받는 function을 선언할 수 있는데, 이는 해당 struct의 method라는 것과 유사한 의미이다.


```
type person struct {
    name string
    age int
}

func (p person) sayHello(){// 함수명 앞에 () 치고 변수명, 어떤 struct인지 위에 선언한 struct명 순으로 적는다.
    fmt.Println("Hello! my name is %s and I'm %d", p.name, p.age)
}
```
이 함수는 main 같은 곳에서 사용 시 struct가 선언되어 있었어야 함.

```
func main(){
    hoon := person{"hoon", 99}
    hoon.sayHello()//이와 같이 메소드처럼 사용한다.
}
```

go에는 class나 object가 없다. struct가 그와 유사한 개념이므로 잘 알아두자.

+추가
객체 지향 언어에서 변수는 외부에서 접근하지 못하게 하고 해당 변수를 바꿔줄 수 있는 함수만 만드는 것처럼,
go에서도 위와 같이 설계한다.

외부에서 import가 되지 않도록 변수의 맨 앞은 소문자로(=private)로 적은 후

```
func (s struct) change(){

}
```
를 사용한다.

++포인터와 struct의 관계
```
hoon := person.Person{}
//이런 식으로 struct를 담으면 단순히 값의 복사이다.
//메소드를 선언할 때 포인터를 사용해서 선언해야 main에서 그 변화까지 담을 수 있음.
```

예시는 아래와 같다

```
func (p *Person) SetDetails(name string, age int) {//p에 *Person 자료형 선언. 즉 Person의 주소형 타입이 됨
    p.name = name
    p.age = age
}
```
