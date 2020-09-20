# Week3 Class
#### B976082 박순범

# What is Alpha and Color?


## **1. Alpha?**

**Alpha값**은 색상의 투명도를뜻하며, 보통 색공간을 뜻하는 RGB(Red, Green, Blue)에 Alpha값을 추가해 RGBA로 쓰인다. 그렇기에 RGBA의 알파는 투명도를 추가로 지정할 수 있게 한 것이며, **0.0(투명)~1.0(불투명)** 사이의 값을 가지게 된다.

![Image](https://upload.wikimedia.org/wikipedia/commons/0/0b/RGBA_comp.png)
불투명, 투명 부분이 포함된 RGBA 이미지의 예. 체커보드 배경에 합성된 모습이다.

![Image](https://framework7.io/i/docs/color-picker-alpha-slider.png)

추가로, HSLA 색상은 hsla(색조, 채도, 명도, 투명도)의 형태로, 위에서 설명한 HSL 색상 값에 알파채널을 확장한 것으로 투명도를 추가로 지정할 수 있게 한 것이며, 0.0(투명)~1.0(불투명) 사이의 값을 가지게 된다.


## **2. Color?**

### + **RGB**

**RGB**는 색을 혼합하면 명도가 올라가는 가산 혼합 방식으로 색을 표현하기에 빛의 삼원색이라 하고, RGB 가산혼합의 삼원색은 **빨강(Red)**, **녹색(Green)**, **파랑(Blue)**을 뜻한다. RGBA은 RGB와 동일하며, **알파(Alpha)**라는 투과도를 덧붙인 것이다. RGB 색 공간은 삼원색에 해당하는 세 가지 채널의 밝기를 기준으로 색을 지정한다. RGB 색 공간은 웹 색상 표현의 기본 원리이다.

![Image](https://mblogthumb-phinf.pstatic.net/20160608_66/luminous2007_1465380054470LF36h_JPEG/%C1%A6%B8%F1_%BE%F8%C0%BD.jpg?type=w3)


### + **CMYK**

**CMYK**은 인쇄과정에서 쓰이는 감산 혼합 방식으로 색의 삼원색이라 불리며 흰 바탕에 네 가지 잉크의 조합으로 색을 나타내는 것을 말한다. 색을 혼합하면 밝아지는 RGB와 달리 색을 혼합하면 명도가 낮아지기에 감산 혼합이라고 한다. CMYK는 인쇄에 쓰이는 4가지 색은 **청록색(Cyan)**, **자홍색(Magenta)**, **노랑(Yellow)**, **검정(Black)**을 뜻한다.

![Image](https://mblogthumb-phinf.pstatic.net/20160608_172/luminous2007_1465380028565hFwj8_JPEG/%C1%A6%B8%F1_%BE%F8%C0%BD.jpg?type=w3)


### + **HSV**

**HSV** 색 공간은 **색상(Hue)**, **채도(Saturation)**, **명도(value)**를 기준으로 색을 구성하는 방식이다. 감산 혼합이나 가산 혼합보다 색상의 지정이 직관적이기 때문에 시각 예술에서 자주 쓰인다.

![Image](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/HSV_cone.jpg/200px-HSV_cone.jpg)
HSV색공간 모형
 
 
+ **색상(Hue)**
  
  색상값 H는 가시광선 스펙트럼을 고리모양으로 배치한 색상환에서 가장 파장이 긴 빨강을 0°로 하였을 때 상대적인 배치 각도를 의미한다. 때문에 H 값은 0°~360°의 범위를 갖고 360°와 0°는 같은 색상 빨강을 가리킨다.
  
	
+ **채도(Saturation)**
  
  채도값 S는 특정한 색상의 가장 진한 상태를 100%로 하였을 때 진함의 정도를 나타낸다. 채도값 0%는 같은 명도의 무채색을 나타낸다.
  
	
+ **명도(Value)**
  
  명도값 V는 흰색, 빨간색 등을 100%, 검은색을 0%로 하였을 때 밝은 정도를 나타낸다.


### + **색상값**

CSS의 색상값은 적색, 녹색, 청색의 혼합의 결과로 16진수를 이용한 표기법(**HEX**)과, **RGB 표기법**, **HSL 표기법**, 색상 이름을 직접 입력하는 방식들을 지원한다.


+ **16진수**
  
16진수 색상은 **#RRGGBB**와 같은 형태로 RR(적색), GG(녹색), BB(청색)을 진수로 나타내며, 0~FF사이의 값을 가지게 된다(대소문자 구분하지 않음).

![Image](https://img1.daumcdn.net/thumb/R800x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99CFF13359C4B0D334)

예를 들어, **#0000FF**의 값은 RR과 GG는 0의 값이고, 청색인 BB만 가장 밝은 FF의 값을 가지게 되니 청색으로 표현된다.


+ **RGB**

RGB 색상은 rgb(적색, 녹색, 청색)의 형태로, 각 변수값(적색, 녹색, 청색) 의 색상의 강도를 정의하고, 0~255의 정수로 된 퍼센트 값(0%~255%)을 가지게 된다.

![Image](https://framework7.io/i/docs/color-picker-rgb-sliders.png)

예를 들어, rgb(0,0,255)의 값은 청색이 255로 가장 높은 값으로 지정되고 나머지는 0%의 값이니 청색으로 표현된다.


+ **HSL**

HSL 색상은 hsl(색조, 채도, 명도)의 형태로 색조, 채도 및 밝기를 좌표를 이용해 나타낸다.

![Image](https://framework7.io/i/docs/color-picker-hsb-sliders.png)

색조는 색상환에서 0~360까지 - 0 혹은 360은 적색, 120은 녹색, 240은 청색을 나타낸다.

채도는 퍼센테이지 값을 가지며, 0%는 회색의 음영을 가지게 된다.

명도 또한 퍼센테이지 값을 가지며, 0%는 검정, 100%는 하얀색이 된다.


참고:

https://webdir.tistory.com/406 [WEBDIR]

https://ko.wikipedia.org/wiki/%EC%83%89_%EA%B3%B5%EA%B0%84#RGB_%EC%83%89_%EA%B3%B5%EA%B0%84

https://ko.wikipedia.org/wiki/HSV_%EC%83%89_%EA%B3%B5%EA%B0%84

https://framework7.io/docs/color-picker.html
