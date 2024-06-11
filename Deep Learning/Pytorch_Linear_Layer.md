


$$ y = x \cdot  W + b $$


Fully Connected Layer 또는 Dense Layer 라고도 부르는 선형곱으로 이루어진 신경망


구현 

```python
def linear(x, W, b):
	y = torch.matmul(x,W) + b
	return y
```

하지만 이렇게는 사용할 수 없다. (계산은 가능하지만 학습이 되지 않음)

W, b 는 학습이 되어야 하는 parameter 인데 따로 등록이 되어있지 않기 때문



### nn.Module 에서 상속 받는 방법 ###

```python
import torch.nn as nn

class MyLinear(nn.Module):
	def __init__(self, input_dim=3, output_dim=2):
		self.input_dim = input_dim
		self.output_dim = output_dim
		super().
```
