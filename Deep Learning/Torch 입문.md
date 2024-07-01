

차원이 높고 복잡한 데이터는 비선형인 경우 + Plot으로 확인이 어려운 경우가 많음

--> 복잡한 모델이 필요하다.

크고 깊은 모델로 복잡성을 채워줄 수 있음 

+

Activation Layer 를 넣어줘서 비선형성도 채워줄 수 있음

= 모델은 충분히 복잡하니 Loss 만 작게 훈련하면 장땡임 (실제와 예측값의 차이가 적을 수록)




---- 


Loss 가 작아지는 원리  \<Back Propagation\>

우리의 목적 :  주어진 데이터와 출력이 똑같은 함수를 만드는 것 
			-> 출력이 같다 = Loss 가 0 이다. [[Loss Function]]
			
			
현재 Loss function 을 만드는  $\theta_t$  (Weight, bias) 를 업데이트 하여 더 나은 $\theta_{t+1}$ 로 가자.


Deep Learning 함수가 동작하는 방법
: Xi 를 넣어서 Yi 를 구하고, 실제 Y 와 비교하여 Loss 를 구한다.

나의 Loss 에 영향을 주는 애 :  $\hat{y}$  <- 에 영향을 주는 애들 을 미분하여 영향력을 확인
(여기까지는 Back Propagation 과 관계없음-> 하지만 되게 어려움. 깊은 모델에서 학습이 사실상 불가능)

각 Layer 에서 Weight 들을 W1, W2, W3 라고 할 때
가장 마지막에서 구해놓은 영향력 (미분값)을 계속해서 재활용 할 수 있음!

미분을 다른 변수들의 미분의 곱으로 표현함 (체인룰)

$$
	\frac{\partial{y}}{\partial{x}} = \frac{\partial{y}}{\partial{h}} \frac{\partial{h}}{\partial{x}}
$$

loss를 구할 때는 가장 마지막부터 계산한 값을 다시 재활용함. `loss.backward`
실제로 x를 넣어서 y를 구함 `forward()` : feed forward


과거의 딥러닝은 feed forward 를 만들고, 그것에 대한 미분식을 만들어서 c++등으로 구현하였음
-> 현재는 프레임 워크에서 AutoGrad 같은 기능으로 자동 미분 수행
(Tensorflow 에서 complie 하는 순간 미분식이 만들어짐)


---- 























\      






