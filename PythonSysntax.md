# == 과 is 비교.
<code>is</code> : 같은 객체를 가리키고 있는 두 변수에 대해서 비교하여 같으면 True를 반환한다.<br/>
<code>==</code> : 변수가 참조하고 있는 값에 대해 비교하여 같으면 True를 반환한다.<br/><br/>
파이썬은 small integer objects에 대해서만 캐쉬 데이터를 가지고 있기 때문에 다음과 같이 예제가 동작함.<br/><br/>
<code>
\>>>1000 is 10**3<br/>
False<br/>

\>>>1000 is 10**3<br/>
False<br/>
<br/>
\>>>[] is []<br/>
False<br/>
\>>>[] == []<br/>
True<br/>
<br/>
\>>> "a" is "a"<br/>
True<br/>
\>>> "aa" is "a" * 2<br/>
True<br/>
\>>> x = "a"<br/>
\>>> "aa" is x * 2<br/>
False<br/>
\>>> "aa" is intern(x*2)<br/>
True<br/>
<br/>
</code>

# not v and v != 0
- v(변수)가 거짓이고,
- v의 값은 0이 아니다.
- 파이썬에서 변수가 거짓인 경우는?
    - 값(value)이 0인경우.
    - 객체의 경우 참조(Ref)가 None을 가리키는 경우.
>> not v : 객체가 None일 경우, 값이 0일 경우 True<br/>
>> not v and v != 0 : v가 None일 경우인데?<br/>
>> 그럼 v is None 과 뭐가 다른걸까..???<br/>
<br/>
---
# @property
- get, set에 대한 액션을 변수에 직접 접근하지 않고 메서드(getter, setter)로 호출되도록 하려면 @property를 사용하면 된다.
- getter함수에 @property 데코레이터. 
- setter함수에 @메서드이름.setter 데코레이터.
- 이렇게 하면 .color="red" 경우 color(clr)메서드 실행되고
- .color 이렇게 쓰면 __color이 반환된다.

```
class Test:

    def __init__(self):
        self.__color = "red"

    @property
    def color(self):
        return self.__color

    @color.setter
    def color(self,clr):
        self.__color = clr

if __name__ == '__main__':

    t = Test()
    t.color = "blue"

    print(t.color)
```