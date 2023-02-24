# PointNet 활용 1단계

활용단계에서는 H-up 3D 데이터를 PointCloud로 변환해 분류해보는 예제를 진행.<br><br>
>### **Class 종류**  
 ```Processing... (클래스 이름) : DC_FLANGE   
    Processing... (클래스 이름) : REDUCER   
    Processing... (클래스 이름) : VALVE```
    <br>
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
>### **학습결과**  
  val_loss 값이 일률적으로 적어지게 하기 위해 옵션값을 조정하였다. Convolution Layer에 Activation Funtion을 ReLU에서 Sigmoid 함수로 변경하였고, Batch Size를 32에서 128로 확대하였음. Optimizers는 기존 Learning Rate를 0.0001에서 기본값으로 진행.<br>
<img src = https://user-images.githubusercontent.com/60258130/221104266-a8c86884-38d1-40bd-9ed8-41d9afd715b9.png width = "700px">   
<br><br>
>### **분류 결과 이미지**   
<img src = https://user-images.githubusercontent.com/60258130/221104250-f603c61f-3a4d-44f2-9d4e-adbecd0cafd8.png width = "700px">   
