# json-response-and-parshing

1.get요청
- 주소에 데이터를 담아 보낸다. 데이터 형태는 key = value
특징 : body가 없고 데이터를 body에 담아 보내지 않는다.

2.post, put, delete 요청(데이터를 변경한다.)
- 데이터를 담아보내야 할 것이 많음. body에 데이터를 담아 보낸다. 데이터 형태는 json으로 통일하는 것이 좋다.
- post는 form태그에 method를 post로 정해서 보내면 되지만 get과 post요청밖에 못한다.
- 그래서 자바스크립트로 요청을 해야한다.(통일이 안됨)

통일 : 자바스크립트로 ajax요청 + 데이터는 json으로 요청한다!!

3.스프링 컨트롤러의 파싱 전략1
- 스프링 컨트롤러는 key-value 데이터를 자동으로 파싱하여 변수에 담아준다
- 가령 get요청은 key=value이고 post 요청중에 x-www-form-urlencoded시에도 key=value이기 때문에 이러한 데이터는
함수의 파라미터로 받을 수 있다.

4.스프링 컨트롤러의 파싱 전략2
- 스프링은 key=vlaue 형태의 데이터를 오브젝트로 파싱해서 받아주는 역할도 한다.
- 이때 주의 할점은 setter가 없으면 key=value 데이터를 스프링이 파싱해서 넣어주지 못한다.

5.key=value가 아닌 데이터는 어떻게 파싱할까?
- json 데이터나 일반 text데이터는 스프링 컨트롤러에서 받기 위해 @RequestBody어노테이션이 필요하다.
- 기본전략이 스프링 컨트롤러는 key=value 데이터를 파싱해서 받아주는 일을 하는데 다른 형태의 데이터(json)는
스프링이 파싱해서 오브젝트로 받지 못한다. 그래서 @RequestBody 어노테이션을 붙이면 MessageConverter 클래스를
구현한 Jackson 라이브러리가 발동하면서 json 데이터를 자바 오브젝트로 파싱하여 받아준다.
