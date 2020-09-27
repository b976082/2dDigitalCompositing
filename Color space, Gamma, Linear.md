# Week4 Class
#### B976082 박순범

# Color space, Gamma, Linear color


## **Color space**

### **RGB**

- 빛의 특성을 이용해 색사를 표현하는 방법

- R(적색), G(녹색). B(청색)의 삼원색이 각각 최댓값이 되면 흰색이 되는 가산 혼합법으로 색을 조합

- 일반적으로 sRGB와 Adobe RGB가 주로 사용됨

![week4-14](https://user-images.githubusercontent.com/70869138/94374485-832cf700-0147-11eb-815e-85e4b7474269.png)


### **sRGB(standard RGB)**

 - 1996년 HP와 MS에서 제안한 컴퓨터를 위한 RGB 색공간, HDTV 시스템에서 사용하는 Rec.709와 동일한 gamut을 가짐
 
 - sRGB 데이터를 HDTV에서 그대로 출력시의 문제점
 
=> 감마 설정에서 약간 차이가 존재하여 이미지가 조금 어둡게 표현된다.
 
 (요즘 비디오 관련 장비와 편집 SW에서는 sRGB - Rec.709간 상호 변환시 자동으로 감마 보정을 해준다. 하지만 이 자동보정 기능이 문제를 일으키는 경우가 존재하기 때문에 표준 모니터의 중요성이 강조된다.)
 

### **Adobe RGB**

 - 1998년 Adobe에서 공개한 RGB 기반의 색공간.
 
 - sRGB가 녹색 계열의 색을 온전히 구현하지 못하는 문제를 해결함
 
 - 더 넓은 gamut 기반으로 색을 재배열 하는 방법을 사용하여 sRGB보다 재현할 수 있는 범위를 더 넓혔다.
 
 - 디카로 촬영한 이미지를 컴퓨터에서 확인할 때 채도가 낮고 녹색이 진한 것 처럼 이상하게 보인다면?
 
=> 사용한 이미지 뷰어에서 촬영된 이미지 파일의 색 공간을 제대로 지원하지 못하기 때문.

 (이 경우 대부분 sRGB만 지원하는 이미지 뷰어로 Adobe RGB로 쵤영된 이미지를 보는 경우이다. Adobe RGB를 정식 지원하는 이미지 뷰오를 사용하거나 해당 이미지를 sRGB 색공간으로 변환하여 본다.)

![week4-15](https://user-images.githubusercontent.com/70869138/94374894-7958c300-014a-11eb-89e6-620b9f9c32da.png)



### + **Color gamut**

 색공간(Color space)과 혼용해서 쓰이기도 하는데, 색공간은 HSB와 같이 색을 섞는 공간으로, 색영역을 색을 표시하는 범위로 표현한다.
 
 ![1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile24.uf.tistory.com%2Fimage%2F99A0684A5A682EB82E0391)
 
 색영역(색역)은 일반적으로 sRGB, AdobeRGB가 가장 많이 쓰인다. 이외에도 목적에 따라 DCI-P3, ProPhotoRGB, Wide-GamutRGB등의 색영역이 정의되어 있다. 이외에도 비디오에서의 색영역 DCI-P3, rec.709, rec.2020등이 있다.
 
 
## **Gamma and Linear color**

 사람의 눈이 어두움에 훨씬 민감하다. 그래서 어두운 칼러에는 많은 비트 영역을 할 당하고, 빛의 변화가 있는 밝은 쪽은 조금 적은 비트를 할당하여 한정된 비트를 최대한 사용하여 사람 눈과 비슷하게 저장하는 Gamma Encoding을 한다.

 이렇게 Gamma Encoding된 이미지들을 모니터에서 보여줄 때는 Video Card에서 Decoding해서 최종 보정된 이미지를 보여준다. Gamma가 적용된 이미지의 encoding/deconding 작업을 Gamma Correction이라고 부른다.

 그리고 그 연산 시에 사용되는 Input 값의 지수값을 **감마(Gamma)**라고 부른다.

 결국, 밝게 저장된 Gamma Encoding된 이미지를 모니터에서 Decoding해서 보여주게 되면 Gamma Correction이 발생하여 어두운 영역이 잘 살아 있는 우리 눈이 잘 보이는 것과 비슷한 이미지로 보여지게 되는 것이다.
 
 반면 **Linear Color Space**는 Gamma Encoding을 사용하지 않는 Color Space다. 수학적으로 정확한 포멧이다. 따라서 Gamma Color Space와는 달리 쉐이더나 색 연산 시에 강점을 가진다.
 
![week4-16](http://rapapa.net/wp/wp-content/uploads/2018/06/linearcolourspace_1.png)

 쉐이더에서 빛의 Intensity를 강하게 올렸을 때, 하얗게 타버리는 정도가 감마 Space가 훨씬 더 빨리 발생한다.

 즉, Linear space가 강한 빛 아래서의 색 표현을 훨씬 풍부하게 할 수 있다.

 둘째로, Linear space는 Color 데이터가 렌더 파이프라인을 탈 때 보정 연산이나 변환 연산들이 없다. 따라서 Gamma (midtone) 보상 연산을 거치는 Gamma Space보다 연산 오류나 정확도 면에서 더 나은 결과를 가져온다고 한다.
 
![2](http://rapapa.net/wp/wp-content/uploads/2018/06/i2eZj9U.png)

 두가지 그래프를 합해서 나온 출력값이 Linear 그래프와 얼추 같아 보여도, 실제 데이터는 아래에 뭉쳐 있어 어두은 영역이 더 넓게 표현된다.
 
 참고:
 
 https://dg087.tistory.com/35
 
 http://rapapa.net/?p=3406
 
 https://pid.samsungdisplay.com/ko/learning-center/white-papers/wide-color-gamut-displays
 
 https://whiteknight3672.tistory.com/192
 
 https://blog.naver.com/PostView.nhn?blogId=cdw0424&logNo=221827528747
