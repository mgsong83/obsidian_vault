


$$ y = x \cdot  W + b $$


Fully Connected Layer 또는 Dense Layer 라고도 부르는 선형곱으로 이루어진 신경망

실제로 구현을 시도해보자!

```python
def linear(x, W, b):
	y = torch.matmul(x,W) + b
	return y
```

하지만 이렇게는 사용할 수 없다. (계산은 가능하지만 학습이 되지 않음) 
W, b 는 학습이 되어야 하는 parameter 인데 따로 등록이 되어있지 않기 때문



### nn.Module 에서 상속 받는 방법 ###

통상 pytorch 에서는 신경망을 직접 구현하기보다는 torch.nn 으로 부터 상속 받아서 이 중에 init과 forward 두 개만 수정해서 사용하는 경우가 많음. 

```python
import torch.nn as nn

class MyLinear(nn.Module):
	def __init__(self, input_dim=3, output_dim=2):
		self.input_dim = input_dim
		self.output_dim = output_dim
		super().__init__()

		self.W = torch.FloatTensor(input_dim, output_dim)
		self.b = torch.FloatTensor(output_dim)

	def forward(self, x):
		y = torch.matmul(x, self.W) + self.b
		return y

```

이렇게 클래스를 만들고

```python
linear = MyLinear(3, 2) #input, output dim 
y = linear(x)
```

하지만 이렇게 클래스를 만들어도 실제로는 사용이 불가능하다. 
왜냐하면 파라메터 등록이 안되어있기 때문, 이를 확인해보기 위해서 아래와 같이 확인해보면 아무것도 출력이 되지 않는다. 

객체 이름 *linear*를 바로 부르면 알아서 forward가 실행된다. (정확히는 forward를 포함한 여러 hook이 같이 돌아간다. 앞단 뒷단에 여러 옵션들이 붙긴함)




![[Pasted image 20240611164421.png]]


Trainable 한 파라메터를 등록하기 위해서는 다음처럼 등록을 해줘야 한다.
```python
import torch.nn as nn

class MyLinear(nn.Module):
	def __init__(self, input_dim=3, output_dim=2):
		self.input_dim = input_dim
		self.output_dim = output_dim
		super().__init__()

		self.W = nn.Parameter(torch.FloatTensor(input_dim, output_dim))
		self.b = nn.Parameter(torch.FloatTensor(output_dim))

	def forward(self, x):
		y = torch.matmul(x, self.W) + self.b
		return y



```
\
 위 라인 9, 10과 같이 학습이 가능한 (변동 가능한) 파라메터를 `nn.Parameter()` 로 등록을 해줘야한다.

이렇게 하면
![[Pasted image 20240611164739.png]]
요렇게 학습이 되는 파라메터로 등록이 된다. 


### nn.Linear 를 사용 하는 방법 ###


하지만 이렇게 수작업으로 Linear Layer를 구현하는 건 몹시 비효율적이므로, 이왕이면 미리 만들어진 Layer를 사용하면 된다.


```python
linear = nn.Linear(3,2)
y = linear(x)
```


또 nn.Module 를 상속 받아서  사용할 때 다른 nn.Module  을 넣을 수 있다.  
이 경우에는 보통 module 의 `__init__`  부분에 sub layer 들을 정의하고, forward 부분에서 이들이 어떻게 통과하는지를 정의한다. 








