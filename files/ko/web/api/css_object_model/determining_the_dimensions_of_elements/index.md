---
title: Determining the dimensions of elements
slug: Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements
translation_of: Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements
original_slug: Determining_the_dimensions_of_elements
---
엘리먼트의 너비와 높이를 알기 위해 살펴볼 수 있는 여러 속성이 있습니다. 또한, 요구하는 사항에 딱 맞는 것을 고르기 다소 까다로울 수도 있습니다. 이 글은 여러분이 필요에 맞는 속성을 고르는데 도움을 주기 위해 작성했습니다.

### 공간을 얼마나 차지하나요?

표시된 컨텐트의 너비, 스크롤바, 패딩까지 포함해서 엘리먼트가 차지하는 전체 공간을 알고 싶다면, [`offsetWidth`](/en/DOM/element.offsetWidth "en/DOM/element.offsetWidth")와 `offsetHeight 속성을 사용하세요:`

![Image:Dimensions-offset.png](/@api/deki/files/186/=Dimensions-offset.png)

### 보이는 컨텐트의 크기는요?

패딩은 포함하되 경계선, 여백, 스크롤바는 포함시키지 않고 보이는 컨텐트가 실제로 차지하는 공간이 알고 싶다면, [`clientWidth`](/en/DOM/element.clientWidth "en/DOM/element.clientWidth")와 [`clientHeight`](/en/DOM/element.clientHeight "en/DOM/element.clientHeight") 속성을 사용하세요:

![Image:Dimensions-client.png](/@api/deki/files/185/=Dimensions-client.png)

### 컨텐트는 얼마나 크나요?

컨텐트의 실제 크기를 알고 싶다면(보여지는 부분만이 아닌 전체 컨텐트 크기), [`scrollWidth`](/en/DOM/element.scrollWidth "en/DOM/element.scrollWidth")와 [`scrollHeight`](/en/DOM/element.scrollHeight "en/DOM/element.scrollHeight") 속성을 사용하세요. 이 속성들은 엘리먼트 컨텐트의 전체 크기에 해당하는 너비와 높이를 반환합니다. 보여지는 영역이 작아서 스크롤바를 사용하고 있다해도 관계없습니다.

예를 들어, 600x400 픽셀 크기의 엘리먼트가 300x300 픽셀의 스크롤박스에서 보여진다면 `scrollWidth`는 600을, `scrollHeight`는 400을 각각 반환합니다.

### 참고자료

[MSDN: Measuring Element Dimension and Location](<https://docs.microsoft.com/en-us/previous-versions//hh781509(v=vs.85)>)
