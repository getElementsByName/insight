## Reference Doc
- [Functor and monad examples in plain Java](https://www.nurkiewicz.com/2016/06/functor-and-monad-examples-in-plain-java.html)
  - [kor](https://gist.github.com/jooyunghan/e14f426839454063d98454581b204452)

## insight
### functor
- map 함수의 존재: input과 output타입이 같음

### monad
- functor의 속성
- flatmap 함수의 존재: 인자 함수의 타입이 Monad<R> 타입인 경우 최종적으로 Monad<R> 타입을 변환 (flattening) 
  - flatmap((T) -> Monad<R> | R) -> Monad<R>

### javascript 에서 적용된 요소
#### map
- `Array<T>.prototype.map()` 의 리턴타입이 Array<R>
- `Promise<T>.prototype.then()` 의 리턴타입이 Promise<R>

#### monad
- `Promise<T>.prototype.then() -> Promise<R>` 인자 함수의 리턴타입이 Promise<R>인 경우 R값으로 변환되어 최종적으로 Promise<R>

#### flatmap의 응용
- `Promise.all(Promise<any>[])` 
  - 모나드의 리스트(인자)를 리스트의 모나드(Promise.all 결과) 로
  - 모나드의 리스트을 하나의 리스트의 모나드로 만들기 때문에 모든 모나드의 리스트 요소의 값을 참조(Promise.all에서는 인자의 모든 Promise의 비동기처리가 완료되어야 함)