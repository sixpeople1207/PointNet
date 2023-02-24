# PointNet 활용 1단계

활용단계에서는 H-up 3D 데이터를 PointCloud로 변환해 분류해보는 예제를 진행.  

>### **Class 종류**  
> >Processing... (클래스 이름) : DC_FLANGE  
Processing... (클래스 이름) : REDUCER  
Processing... (클래스 이름) : VALVE  

>### **학습결과**  
val_loss 값이 일률적으로 적어지게 하기 위해 옵션값을 조정하였다. Convolution Layer에 Activation Funtion을 ReLU에서 Sigmoid 함수로 변경하였고, Batch Size를 32에서 128로 확대하였음. Optimizers는 기존 Learning Rate를 0.0001에서 기본값으로 진행.
<img src = https://user-images.githubusercontent.com/60258130/221104266-a8c86884-38d1-40bd-9ed8-41d9afd715b9.png>

>### **분류 결과 이미지**   
<img src = https://user-images.githubusercontent.com/60258130/221104250-f603c61f-3a4d-44f2-9d4e-adbecd0cafd8.png>


