# PointNet 활용 1단계

활용단계에서는 H-up 3D 기자재 데이터를 PointCloud로 변환해 분류해보는 예제를 진행한다. <br>
+ 적은 학습데이터로 학습이 가능한지. 
+ 3D 데이터셋을 구축해서 학습이 가능한지.<br>

학습데이터셋은 3에서 5개정도로 지정하려고 했으나 진행과정 중 밸브 타입 중 플랜지를 포함하는 PVC가 존재해서 학습데이터를 2개를 더 늘렸다. 테스트데이터 셋은 1개~2개정도이다. 모델을 학습시키는 과정에서 계속해서 오버슛팅 문제와 학습이 제대로 되지 않는 이슈가 발생하였다. 학습데이터가 너무 적어서 그런 이유도 있었지만 모델의 파라미터를 수정함으로 문제들을 해결할 수 있었다.   

<br>

>### **데이터셋**  
클래스는 DC_FLANGE와 REDUCER , VALVE 3개의 클래스를 가지고 클래스마다 Train,test셋을 가진다.
 ```python
 Processing... (클래스 이름) : DC_FLANGE   
 Processing... (클래스 이름) : REDUCER   
 Processing... (클래스 이름) : VALVE
 ```
 <br>
 폴더구성.
<img src = "https://user-images.githubusercontent.com/60258130/221112008-bb3afc62-0080-4388-be3f-c7d3d82c861a.PNG" width =300>

<br>

 ---PointNet코드 생략---       
 
<br>

이제부터 PointNet으로 학습데이터를 불러들여 학습 시키기로 해보겠다. 기존코드로 학습한 모습이다.  
<br>
>### **PointNet 학습**  
 <br>
 
* **기존 코드의 이슈**   
 이슈 : Val_Loss에 오버슛팅이 발생했다. 제대로 학습이 되지 않아 분류가 되지 않는다.
 <img src="https://user-images.githubusercontent.com/60258130/221111422-dffdd878-7f9f-4cb6-9a96-4c120261892f.png" width = 600><br>

* **원인분석** : 학습데이터가 적은 이유인지 PointCloud 데이터의 문제인지 val_loss 값에 계속해서 오버슛팅이 발생하였다. Convolution Layer에 Activation Funtion을 ReLU에서 Sigmoid 함수로 변경하였고, Batch Size를 32에서 128로 확대하였음. Optimizers는 기존 Learning Rate를 0.0001에서 기본값으로 진행.  <br>


* **파라미터 변경한 모델 학습 결과**  
```python
Epoch 10/15
1/1 [==============================] - 1s 785ms/step - loss: 1.0812 - sparse_categorical_accuracy: 0.7692 - val_loss: 0.5071 - val_sparse_categorical_accuracy: 0.7500
Epoch 11/15
1/1 [==============================] - 1s 743ms/step - loss: 0.9652 - sparse_categorical_accuracy: 0.7692 - val_loss: 0.7049 - val_sparse_categorical_accuracy: 0.7500
Epoch 12/15
1/1 [==============================] - 1s 747ms/step - loss: 0.9482 - sparse_categorical_accuracy: 0.7692 - val_loss: 0.6542 - val_sparse_categorical_accuracy: 0.7500
Epoch 13/15
1/1 [==============================] - 1s 761ms/step - loss: 0.9214 - sparse_categorical_accuracy: 0.8462 - val_loss: 0.9881 - val_sparse_categorical_accuracy: 0.5000
Epoch 14/15
1/1 [==============================] - 1s 764ms/step - loss: 0.9644 - sparse_categorical_accuracy: 0.9231 - val_loss: 1.1610 - val_sparse_categorical_accuracy: 0.5000
Epoch 15/15
1/1 [==============================] - 1s 745ms/step - loss: 0.9850 - sparse_categorical_accuracy: 0.7692 - val_loss: 0.4795 - val_sparse_categorical_accuracy: 1.0000
)
```
<br><br>     
* **시각화**                        
<img src = https://user-images.githubusercontent.com/60258130/221104266-a8c86884-38d1-40bd-9ed8-41d9afd715b9.png width = "700px">   
<br><br>

>### **모델 검증**   
<img src = https://user-images.githubusercontent.com/60258130/221104250-f603c61f-3a4d-44f2-9d4e-adbecd0cafd8.png width = "700px">   
