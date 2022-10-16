# V. 조건문

---

## 1. if문

흔히 볼 수 있는 if else 구조이나, 조건 검사 자리에 괄호가 사라짐.

```
func canIDrink(age int) bool {
    if age < 18 {
        return false
    }
    else {
        return true
    }
}
```

독특한 점이라면, go에서는 조건을 쓰기 전 새로운 변수를 선언할 수 있음.

```
func canIDrink(age int) bool {
    if koreanAge := age + 2; koreanAge < 18 {
        return false
    }
    else {
        return true
    }
}
```

이때 선언한 변수는 if문을 벗어나면 사라진다.

---

## 2. switch문

if else가 자주 쓰이는 걸 방지하기 위해 남아있는 문법

```
func canIDrink(age int) bool {
    switch age {
        case 10:
        return false

        case 18:
        return true
    }
    return false
}
```

특이하게 특정 조건을 만족하는 걸로 분기하게 만들수도 있다.

```
func canIDrink(age int) bool {
    switch {
        case age < 18:
        return false

        case age == 18:
        return true

        case age > 50:
        return false
    }
    return false
}
```