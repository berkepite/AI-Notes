Hyperparameters modeli eğitirken göz önüne almamız gereken diğer değişkenlerdir. Bunlar:

- [[#Learning Rate]]
- [[#Batch Size]]
- [[#Epochs]]

>In contrast, [**parameters**](https://developers.google.com/machine-learning/glossary#parameter) are the variables, like the weights and bias, that are part of the model itself. In other words, hyperparameters are values that you control; parameters are values that the model calculates during training.

## **Learning Rate**
Bu hiperparametre [[Gradient Descent]] işleminde parametreleri ne güçte ayarlayacağını belirler.
$0.5$'lik bir learning rate parametreleri (ağırlık ve bias) $0.1$'lik bir learning rate'den 5 kat daha fazla değiştirir.

>[**Learning rate**](https://developers.google.com/machine-learning/glossary#learning-rate) is a floating point number you set that influences how quickly the model converges. If the learning rate is too low, the model can take a long time to converge. However, if the learning rate is too high, the model never converges, but instead bounces around the weights and bias that minimize the loss. The goal is to pick a learning rate that's not too high nor too low so that the model converges quickly.

![[Pasted image 20250711002556.png]]
![[Pasted image 20250711002617.png]]

>A learning rate that's too large never converges because each iteration either causes the loss to bounce around or continually increase. In Figure 23, the loss curve shows the model decreasing and then increasing loss after each iteration, and in Figure 24 the loss increases at later iterations:

![[Pasted image 20250711002657.png]]

## **Batch Size**
Model'in ağırlık ve biaslarla oynamadan önce işlediği örnek sayısıdır. Verisetindeki her örneğe bakmadan ortalama olarak iyi bir gradient seçmek için iki yaygın teknik vardır

- [[#Stochastic Gradient Descent]]
- [[#mini-batch Stochastic Gradient Descent]]

### **Stochastic Gradient Descent**
İterasyon başına 1 örnek verisi kullanır, yeterince iterasyon verildiğinde sonuç verir ancak loss değeri gürültülüdür (noisy) — loss değeri her bir iterasyonda yükselip alçalır.

![[Pasted image 20250711004551.png]]

### **Mini-batch stochastic gradient descent (mini-batch SGD)**
*N* örnek veri var ise *1* ile *N* arasında rastgele örnekler seçer. Ortalama gradient değerlerini hesaplar ve iterasyon başına bir kez ağırlık ve bias değerlerini günceller. Büyük batch size'lar full-batch gradient descent gibi davranırken küçük batch size'lar SGD gibi davranır.
![[Pasted image 20250711005313.png]]

>When training a model, you might think that noise is an undesirable characteristic that should be eliminated. However, a certain amount of noise can be a good thing. In later modules, you'll learn how noise can help a model [**generalize**](https://developers.google.com/machine-learning/glossary#generalization) better and find the optimal weights and bias in a [**neural network**](https://developers.google.com/machine-learning/glossary#neural-network).


## **Epochs**
Eğitimde 1 epoch, modelimizin eğitim setindeki tüm verilerin üzerinden 1 kez geçmiş olduğunu gösterir. 1000 örneklik bir verisetinde 100 mini-batch size'ı seçtiysek 10 iterasyon sonra 1 epoch tamamlanmış olacaktır.

The following table describes how batch size and epochs relate to the number of times a model updates its parameters.

|Batch type|When weights and bias updates occur|
|---|---|
|Full batch|After the model looks at all the examples in the dataset. For instance, if a dataset contains 1,000 examples and the model trains for 20 epochs, the model updates the weights and bias 20 times, once per epoch.|
|Stochastic gradient descent|After the model looks at a single example from the dataset. For instance, if a dataset contains 1,000 examples and trains for 20 epochs, the model updates the weights and bias 20,000 times.|
|Mini-batch stochastic gradient descent|After the model looks at the examples in each batch. For instance, if a dataset contains 1,000 examples, and the batch size is 100, and the model trains for 20 epochs, the model updates the weights and bias 200 times.|