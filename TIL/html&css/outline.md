# 아웃라인

html5에서는 정보 구조를 명확히할 수 있도록 아웃라인 알고리즘이라는 개념이 도입됐다. 아웃라인 알고리즘은 웹 페이지의 정보 구조를 판별할 수 이는 개념으로 책의 목차와 비슷하다. 아웃라인을 구성하는 요소에는 헤딩콘텐츠, 섹셔닝 콘텐츠 등이 있다.

## 암묵적인 레이아웃

암묵적인 레이아웃은 섹셔닝 콘텐츠가 없는 경우 헤딩콘텐츠의 상하관계만을 가지고 정보 구조가 나뉘게 된다. 아무리 div 태그로 감싼다고 하더라도 헤딩콘텐츠의 순서를 기준으로 아웃라인이 생성된다.

```html
<h1>헤딩1</h1>
<div>
  <h1>헤딩1</h1>
</div>
<h1>헤딩1</h1>
<h2>헤딩2</h2>
<h3>헤딩3</h3>
```

이 구조는 다음과 같은 아웃라인 구조를 가지게 된다.

```
1.헤딩1
2.헤딩1
3.헤딩1
└─ 1.헤딩2
   └─ 1.헤딩3
```

## 명시적인 레이아웃

html5부터는 `section`, `article`, `aside`, `nav` 라는 섹셔닝 콘텐츠를 지원하는데, 이를 지정하면 상위 아웃라인으로부터 종속되는 하위 아웃라인이 자동으로 생성된다. 예를 들어 상위 부모 엘리먼트에 h3태그의 제목이 있다고 가정하고, 하위 section 엘리먼트에서 h1를 선언하면 h1이 상위 h3의 종속된 레이아웃이 된다. 예를 들면

```html
<h1>헤딩1</h1>
<section>
  <h1>헤딩1</h1>
  <section>
    <h1>헤딩1</h1>
  </section>
</section>
<h2>헤딩2</h2>
<h3>헤딩3</h3>
```

다음 html 구조는 아래와 같은 아웃라인 모습을 지닌다.

```
1.헤딩1
└─ 1.헤딩1
   └─ 1.헤딩1
└─ 2.헤딩2
   └─ 1.헤딩3
```

`section`이라는 섹셔닝 콘텐츠를 통해 아무리 같은 h1 요소라고 해도 계층이 종속되면서 독립된 아웃라인을 가집니다.