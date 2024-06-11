

결국 코드에서 연산이 되는 것들은 tensor 들!

Tensor 의 **위치**가 중요함 
- CPU (RAM) 에 있거나
- GPU (VRAM) 에 있을 수 있음
단 Torch 에서는 같은 위치에 있는 Tensor 끼리만 연산이 가능! GPU 라도 같은 Device가 아니면 연산이 불가능 (GPU가 여러개일 때)


----

### GPU 에 Tensor를  원하는 위치에 (GPU에) 생성하는 방법


GPU의 경우 처음부터 cuda:0 ~ cuda:7 과 같이 일련번호를 받음.

1) torch.cuda 를 사용해서 GPU를 지정해서 생성

`torch.FloatTensor` -> `torch.cuda.FloatTensor(2, 2)`


2) 또는 일반적으로 생성한 다음에 GPU로 이동시키기

```python
x = torch.FloatTensor(2,2)
x.cuda()
```

3) device 를 지정해서 이동시키기

``` python
dev = torch.device('cuda:0')
x.cuda(device=dev)
```

단 여기서 편의상 이동이라고 표현했지만, 기본적으로는 모든 애들이 복사가 됨.
따라서, 위 명령어를 실행시켜도 `x.device` 를 찍어보면 type = cpu 로 나옴을 확인 할 수 있다. 하지만 가장 많이 사용하는 방법은 to 를 사용하는 방법이다. (이름 자체가 좀 더 직관적)


4) to 를 사용해서 이동시키기

```python
x.to(device=dev)
```



---- 


### model 자체를 move 하는 방법


```python
linear = nn.Linear(2,2)
linear.cuda()
```

요렇게 모델을 `cuda()`로 보낼 때에는 복사가 아니라 이동이 된다.  마찬가지로

```python
linear.to(dev)
```
``