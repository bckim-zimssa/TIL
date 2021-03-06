# regex / 정규 표현식

폼 태그 검증과 같은 것을 할 때, 정규 표현식을 사용하면 편하다.  
일반적으로 `string.match(정규표현식)` `정규표현식.test(string)` 과 같은 방식으로 검증을 한다.

---
**note**
match, test 함수는 string에 해당 정규 표현식이 포함되는가? 에 관련된 내용이다. 즉, 이 표현식에 포함만 되면, 되는 것이다.

---

## 로그인

### 아이디 

이메일 같은 경우에는 html type으로 설정해주면 알아서 이메일 체킹을 해주는데, 아이디 같은 경우에는 정규표현식으로 이를 처리해줘야한다.

영어 + 숫자만을 허용하고 싶을때

```js
const validateNickname = str => {
	const reg = /^[a-zA-Z0-9]+$/;
	const result = reg.test(str);
	if (!result) return false;
	return true;
};
```
와 같은 방식을 택하면 된다.

- `^` : 첫 글자에 해당하는 부분을 지정할 수 있다.
- `[a-z]`: a~z까지의 모든 알파벳이 들어갈 수 있다. 
- `+` : 1개 or 그 이상을 의미한다.
- `$` : 마지막 글자와 매칭될 글자를 선택할 수 있다. 예를 들어, `/t$/` 이면, t로 끝나는 글자를 고를 수 있다. 

즉, 위의 regex를 해석하면, 첫 글자는 `[a-zA-Z0-9]` 패턴에 해당된다. `[a-zA-Z0-9]` 는 알파벳+숫자가 들어갈 수 있다는 뜻이다. 그러한 글자가 한글자 이상이고, 해당 패턴으로 끝이나야 한다.

### 비밀번호
