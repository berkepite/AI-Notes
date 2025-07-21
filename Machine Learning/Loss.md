Loss bir modelin çıktılarının ne oranda hatalı olduğunu gösteren sayısal bir değerdir. Bir modeli eğitmenin ana amacı loss'u en aza indirgemektir. Loss değeri gerçek değerle tahmin edilen değerin arasındaki farkı gösterir. Bu farkı hesaplamak için 2 farklı yöntem vardır, ya farkların karesini alırız ya da farkların mutlak değerini.

$2 - 5 = -3 \to loss=3$
$2 - 5 = -3 \to loss = 9$

## **Loss types**

| Loss type                                                                                                        | Definition                                                                                           | Equation                                                       |
| ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| **[L1 loss](https://developers.google.com/machine-learning/glossary#l1-loss)**                                   | The sum of the absolute values of the difference between the predicted values and the actual values. | $\sum \vert actual\:value - predicted\:value\vert$             |
| **[Mean absolute error (MAE)](https://developers.google.com/machine-learning/glossary#mean-absolute-error-mae)** | The average of L1 losses across a set of *N* examples.                                               | $\frac{1}{N} \sum \vert actual\:value - predicted\:value\vert$ |
| **[L2 loss](https://developers.google.com/machine-learning/glossary#l2-loss)**                                   | The sum of the squared difference between the predicted values and the actual values.                | $\sum(actual\:value - predicted\:value)^2$                     |
| **[Mean squared error (MSE)](https://developers.google.com/machine-learning/glossary#mean-squared-error-mse)**   | The average of L2 losses across a set of *N* examples.                                               | $\frac{1}{N}\sum(actual\:value - predicted\:value)^2$          |
>The functional difference between L1 loss and L2 loss (or between MAE and MSE) is squaring. When the difference between the prediction and label is large, squaring makes the loss even larger. When the difference is small (less than 1), squaring makes the loss even smaller.

>When processing multiple examples at once, we recommend averaging the losses across all the examples, whether using MAE or MSE.

## **Outlier**
Genel geçer verilerin dışında kalan örnek verilere verilen isimdir. Mesela genellikle arabalar 2000-5000 pound arasında ve galon başına 8-50 mil yol alır ama 8000 pound olan arabalar da vardır, galon başına 100 mil giden arabalar da vardır. Bunlara **Outlier** denir.

## **Choosing a Loss Function**
Loss function seçerken outlier'lara nasıl davranacağımızı belirlemek önemlidir. MAE kullanırsak eğer modelimiz outlier'lardan fazla etkilenmez, MSE kullanırsak modelimiz outlier'lara daha fazla yanaşır. $L_2$ loss (kare alınan) modeli daha fazla cezalandırır $L_1$'e göre.


![[Pasted image 20250710234607.png]]
>MSE ile eğitilmiş bir model

![[Pasted image 20250710234617.png]]
>MAE ile eğitilmiş bir model