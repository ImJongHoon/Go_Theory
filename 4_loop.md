# IV. loop문

---
## 1. for문
golang은 반복문이 for문을 제외하고서는 어떤 것도 존재하지 않는다.

1. range 란?
array에 loop를 적용할 수 있도록 해준다.
range + 배열명{}

구조로 사용하는 함수 같은 느낌이다.
첫번째 반환 값으로는 index, 두번째 반환값으로 배열 내부의 값을 주는 함수.

```
for index, content := range array{
    //반복하면서 실행할 구문
}
```

예시

```
func addAll(numbers ...int) int {
    total := 0;
    for _, number := range numbers{ //index를 사용하지 않기 때문에 _로 넣어준다.
        total += number
    }
}
```

이외에는

```
for 초기화문; 조건문; 후처리{
    
}
```
