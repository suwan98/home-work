# CSS Grid Mission

<br />

## 완성본

<p><img src='./assets/images/스크린샷 2023-06-13 004427.png'><p>


<br />

<p><img src='./assets/images/스크린샷 2023-06-13 163626.png'><p>

### HTML 마크업

큰 하나의 섹션을 news로 보고
내부를 `top,bottom`으로 `div`를 사용해 나눴고

상단 내부에 새소식과 더보기 및 더보기이미지를 `div` 요소로 래핑했으며

하단 내부에 리뉴얼 이미지 및 이미지타이틀 그리고 형제 요소로 단락의 제목과 단락을 subTitle로 `markup`했습니다

### CSS 스타일링

<br />

> 상단 부분 스타일링

전체 컨테이너에 가시성을 위해 `margin : 50px`을 임의로 부여했으며 <br />
상단부분(topWrapper)에는 `border-bottom, border-image, border-image,slice`를 이용해서 피그마 시안과 같은 `border`를 디자인했으며 

<br />


paddig-bottom으로 하단 부분과의 여백을 부여했습니다
그리고 플러스버튼 이미지와 더보기 텍스트를 하나의 a링크로 마크업해 flex를 부여해 버튼이미지와 텍스트가 가운데정렬되도록 하였고,  topWrapper를 부모로 position absoulte, top : 0, right : 0 을 부여해 상단 우측에 위치하게 만들었습니다

<br />


> 하단 부분 그리드 스타일링

<br />

```css
    grid-template-columns: repeat(6, 1fr);
    grid-template-areas:
     "news-image news-image news-sub news-sub news-sub ."
     "news-image news-image news-sub news-sub news-sub ."
     "news-image news-image news-desc news-desc news-desc news-desc"
     "news-image news-image news-desc news-desc news-desc news-desc"
```

<br />

하단 큰 부분을 `6개의 columns`로 봤고 `row는 aut`o로 지정해 그리드레이아웃을 진행했습니다


<br />


```css
.news__subTitle--new {
    font-weight: 700;
    display: inline-block;
    padding-bottom: 4px;
}
```
기존 `span`태그를 `inline-block`으로 만들어 `subTitle`과의 상단의 여백을 부여했습니다.