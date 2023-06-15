# mission-05 CSS sprite 과제 구현

<br />

> 완성본

<p><img src="./assets/images/스크린샷 2023-06-14 223007.png" /></p>


<br />
<hr />
<br />

## 2. HTML 마크업 구조

- 인기사이트 컨테이너를 하나의 `section`으로 마크업했고
- title부분을 `h2` 레벨 안에 text 및 `a` `span`요소로 마크업에 글자의 스타일링 및 링크기능을 추가했습니다
- div > ol > li요소로 묶어서 마크업했습니다

```html
  <section class="popularSite">
      <h2 class="popularSite__title">
        인기 <span class="accentText">사이트</span>
        <a href="#" class="popularSite__more">더보기</a>
      </h2>
      <div class="listWrapper">
        <ol class="popularSite__list">
          <li class="sprite">
            <a href="#">W3C</a>
          </li>
          <li class="sprite spriteDown">
            <a href="#">Web Standards</a>
          </li>
          <li class="sprite spriteKeep">
            <a href="#">CSS ZenGarden</a>
          </li>
          <li class="sprite">
            <a href="#">MDN</a>
          </li>
        </ol>
      </div>
    </section>
```

<br />
<hr />
<br />

## 3. CSS 스타일링 구현

<br />


```css
.popularSite__title{
    position: relative;
    margin: 12px;
    font-size: 15px;
}

.popularSite__more{
    position: absolute;
    top: 0;
    right:0;
    font-size: 14px;
    font-weight: 400;
}

```
- title를 부모 relative를 부여해, 더보기 텍스트를 우측 상단에 배치했습니다

<br />


### 3.1 oredered list 스타일링

```css
.popularSite__list{
    display: flex;
    flex-flow: column nowrap;
    gap: 8px;
    margin: 0;
    padding-left: 0;
    margin-top: 8px;
    margin-bottom: 12px;
    font-size: 11px; 
}
```

- list를 flex-container로 만들어 각 글자와 글자사이에 `gap`을 `8px` 부여했고
- ol태그 에이전트 스타일은 `margin:0, padding-left:0`으로 제거한후, 
- `margin-bottom`으로 컨테이너와의 간격을 조절했습니다

<br />


### 3.2 bullet-style 스타일링

- 기존 `ol`리스트의 에이전트 스타일을  `list-style:none`으로 제거 후
- `ol`태그 내부의 자식요소인 `li`에 `before` 가상요소 선택자를 만들어
- `body`에 `counter-reset: listNumber;` 속성을 부여해 카운터 생성을 한후
- `before` 가상 요소 선택자에 `counter-increment: listNumber;`를 부여해 카운터 값을 증가시키게 한후,
- content에 생성된 `listNumber`를 삽입해서 1,2,3,4.. 이렇게 증가하도록 만들었습니다
- `list`를 `flex`로 만들어 해당 `list안의 텍스트`와 `before 요소`들의 정렬을 부여했습니다

```css
/* textnode와 가상요소 정렬 맞추기 */
.popularSite__list li {
    display: flex;
    align-items: center;
}

.popularSite__list li::before {
    content: "";
    width: 1rem;
    color: #fff;
    text-align: center;
    height: 1rem;
    border-radius: 5px;
    background: #a3a3a3;
}

.popularSite__list li::before {
    counter-increment: listNumber;
    content: counter(listNumber);
    width: 1rem;
    color: #fff;
    text-align: center;
    height: 1rem;
    border-radius: 5px;
    background: #a3a3a3;
}
```

<br />


### 3.3 sprite 구현

```css
.sprite {
    background: url(./assets/images/rank.png) no-repeat;
    background-position: right 0;
}

.spriteDown{
    background-position: right -2.6rem;
}

.spriteKeep{
    background-position: right -1.25rem;

}
```

- 각 `list`태그에 공통 클래스 `.sprite`를 부여해 `background-image`를 삽입했고
- `background-postion`으로 x축 끝으로가도록 `right` y축을 이동 뒤에 적절한 이미지에 맞췄습니다