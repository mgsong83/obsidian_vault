

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
: Xi 를 넣어서 Yi 를 구하고, 

\      





