

결국 코드에서 연산이 되는 것들은 tensor 들!

Tensor 의 **위치**가 중요함 
- CPU (RAM) 에 있거나
- GPU (VRAM) 에 있을 수 있음
단 Torch 에서는 같은 위치에 있는 Tensor 끼리만 연산이 가능! GPU 라도 같은 Device가 아니면 연산이 불가능 (GPU가 여러개일 때)


----

GPU 에 Tensor를 생성하는 방법

GPU의 경우 처음부터 cuda:0 ~ cuda:7 과 같이 일련번호를 받음.

1) torch.cuda 를 사용해서 지정

`torch.cuda.FloatTensor(2, 2)`




