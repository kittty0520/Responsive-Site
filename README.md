# webstoryboy - responsive site (by 웹스토리보이)

## 🎯목적

HTML의 기본요소들과 시멘틱 태그를 쓰는 방법, 반응형 사이트를 만들어 보는 연습을 하기 위해 클론코딩했습니다!😀

<br/>

## 📖순서

1. Header 영역 -반응형
2. 전체 메뉴
3. 컨텐츠 레이아웃, 컨텐츠 타이틀
4. 메뉴, 메뉴 반응형
5. 게시판 한줄 효과, 두줄 효과
6. 블로그 영역 고해상도 이미지
7. 이미지 슬라이드
8. 라이트 박스 -lightGallery plugin
9. 필터 이벤트
10. 비디오
11. Side 컨텐츠
12. Footer 영역
13. 접기/펼치기 스크립트
14. 사이드 이펙트 - hover effect

<br/>

## 📝배운점

<br/>

- HTML요소

<br/>

- CSS요소

  <br/>

  - box-shadow 속성을 inset으로 설정하여 mouseover시 배경색이 변하는 hover effect를 준다.

  <br/>

  - 한줄 효과

    ```css
    .클래스이름 {
    	overflow: hidden;
    	text-overflow: ellipsis;
    	white-space: nowrap;
    }
    ```

  <br/>

  - 두줄 효과

    ```css
     {
    	overflow: hidden;
    	text-overflow: ellipsis;
    	display: -webkit-box;
    	-webkit-box-orient: vertical;
    	-webkit-line-clamp: 2;
    }
    ```

  <br/>

  - 디스플레이 해상도에 따른 이미지 표현
    <br/>

    - img의 sreset 속성

      ```html
      <img
      	src="img/blog3_@1.jpg"
      	srcset="img/blog3_@1.jpg 1x, img/blog3_@2.jpg 2x, img/blog3_@3.jpg 3x"
      	alt="이미지"
      	width="100%"
      />
      ```

      <br/>

    - 미디어 쿼리를 사용하여 해상도에 따라 배경 이미지 경로를 바꿈

      ```css
      .blog2 .img_retina {
      	background-image: url('../img/blog4_@1.jpg');
      	background-size: cover;
      }
      @media only screen and (-webkit-min-device-pixel-ratio: 2),
      	only screen and (min-device-pixel-ratio: 2),
      	only screen and (min-resolution: 2dppx) {
      	.blog2 .img_retina {
      		background-image: url('../img/blog3_@2.jpg');
      	}
      }
      @media only screen and (-webkit-min-device-pixel-ratio: 3),
      	only screen and (min-device-pixel-ratio: 3),
      	only screen and (min-resolution: 3dppx) {
      	.blog2 .img_retina {
      		background-image: url('../img/blog3*@3.jpg');
      	}
      }
      ```

    <br/>

    - CSS Filter 속성을 이용하여 배경 이미지에 효과를 줌

      <br/>

    - 카드 뒤집기 (3D CSS 속성)
      <br/>

      - perspective: 요소에 원근감을 부여 (600px)

      <br/>

      - transform-style: preserve-3D => 요소를 3D 공간에 배치
        <br/>

      - backface-visivility: 요소의 뒷면이 사용자를 향할 때 보여야 하는지 지정 (hidden)
        <br/>

      - transform: rotateY() 속성을 이용하여 뒤집는 움직임을 구현 (0 => 180deg, -180deg => 0)

  <br/>

- JavaScript(jQuery)
  <br/>

  - 이미지 공유하기
    <br/>

    - facebook : http://www.facebook.com/sharer.php?u={페이지 링크}&t={페이지제목}
      <br/>

    - 페이스북 아이콘을 클릭했을 때

      ```javascript
      $('.facebook').click(function (e) {
      	e.preventDefault();
      	window.open(
      		'https://www.facebook.com/sharer/sharer.php?u=' +
      			encodeURIComponent(document.URL) +
      			'&t=' +
      			encodeURIComponent(document.title),
      		'facebooksharedialog',
      		'menubar=no, toolbar=no, resizable=yes, scrollbars=yes, height=300, width=600'
      	);
      });
      ```

      <br/>

    - encodeURIComponent() : 문자열을 인코딩하여 URI로 데이터를 전송

  <br/>

  - 접기/펼치기
    <br/>

    ```javascript
    $('.btn').click(function (e) {
    	e.preventDefault();
    	$('.nav').slideToggle();
    	$('.btn').toggleClass('open');

    	if ($('.btn').hasClass('open')) {
    		//open이 있을 때
    		$('.btn').find('i').attr('class', 'fa fa-angle-up');
    	} else {
    		//open이 없을 때
    		$('.btn').find('i').attr('class', 'fa fa-angle-down');
    	}
    });
    ```

<br/>
