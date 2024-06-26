

학습이 잘 되고 있는지를 정량적으로 나타낼 수 있는 숫자를 나타내기 위한 함수
일반적으로 작을 수록 학습이 잘 되고 있음을 나타나게 설계된다.

실제 Labeled 된 참 값 (Ground truth) 를 y 라고 하고, 내가 주어진 data(x값)을 가지고 계산한 값의 결과가 f(x) 라고 할 때 통상 아래와 같이 정의되는데

$$ Loss = \sum_{i=1}^{N}{||y_i - f(x_i)||} $$

즉 참값과 예측값의 차이의 크기를 나타내는 방법인데  다음의 방법들이 사용된다.


### 두 점 사이의 거리  L1, L2 

L1 은 절대값 (멘하탄 거리)
L2 는 제곱값 (유클리언 거리)

L1, L2 의 경우 

특히 L2를 사용하는 경우 MSE가 된다. 이 때 제곱이 들어가기 때문에 차원이 커질 수록 값이 매우 커지게 되서 표현량이 터져버릴 수 있기 때문에 이를 보통 normalized 한 값을 사용한다.

MSE 나 RMSE 가 L2를 사용하는 방법이다. 





pytorch 에서는 MSE를 구현할 수 도 있지만, 왠만하면 미리 정의된 함수를 사용하는 걸 권장

직접 구현하는 방법

```python
def mse(y_hat, y):
	return ((y_hat - y)**2).mean()
```


### Predefine 된 함수/객체를 사용하기

함수 사용 방법

```python
import torch.nn.functional as F

F.mse_loss(y_hat, y) 

F.mse_loss(y_hat, y, reduction = 'sum')  # 평균이 아닌 최종 합
F.mse_loss(y_hat, y, reduction = 'none') # element wise로 계산이 되서 나옴.

```

reduction의 경우 최종적으로 계산된 lose들의 값을 1개의 값, 즉 스칼라로 환산해주는 방법이기 때문에 기본적으로는 mean 이 사용되지만, 원한다면 총합, 또는 아예 scalar로 합치지 않은 값을 받을 수 도 있다. 


객체를 사용하는 방법

```python
import torch.nn as nn

mse_loss = nn.MSELoss()
mse_loss(y_hat, y)

```


