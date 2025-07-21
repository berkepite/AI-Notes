0-1 arasında bir olasılık değeri üretir. Sigmoid fonksiyonunu kullanır.

$Sigmoid\:f(x) = \dfrac{1}{1+e^{-x}}$

Bir mail'in spam olup olmadığı, bir telefon bataryasının değiştirilip değiştirilmeyeceği, hava yağmurlu olacak mı olmayacak mı gibi sorulara olasılıkla cevap vermeye çalışır.

Aşağıdaki denklem logistic regression'ın lineer kısmını göstermektedir.
$z=b+w_1x_1+w_2x_2+...+w_Nx_N$

- $z$ lineer denklemin çıktısıdır, yani [[#Log-odds]]
- $b$ biastır.
- $w$ ağırlıklar.
- $x$ değerleri ise bir örneğin feature'larıdır.

Logistic regression olasılık değeri alınmak istediğinde, $z$ değeri sigmoid fonksiyonuna verilir. Sonuçta 0-1 arasında bir değer çıkar.

$y'=\dfrac{1}{1+e^{-z}}$

- $y'$ logistic regression'ın çıktısı yani olasılık değeridir.
- $z$ burada lineer denklemin çıktısıdır.

![[Pasted image 20250711153809.png]]
>In Figure 2, a linear equation becomes input to the sigmoid function, which bends the straight line into an s-shape. Notice that the linear equation can output very big or very small values of z, but the output of the sigmoid function, y', is always between 0 and 1, exclusive. For example, the yellow square on the left graph has a z value of –10, but the sigmoid function in the right graph maps that –10 into a y' value of 0.00004.

## **Training**

Logistic Regression modelleri Linear Regression modelleri gibi eğitilir, ancak 2 önemli fark vardır.

1. Logistic Regression modelleri squared-loss yerine [[#Log-Loss]] fonksiyonunu kullanır.
2. Overfitting'i önlemek için [[#Regularization]] uygulamak zorunludur.
## **Log-Loss**
Giriş değerleri artarken çıkış değerlerinin lineer bir şekilde arttığı [[Linear Regression]] modelinde *Squared-loss* kullandık. Ancak [[Logistic Regression]] modelinde giriş değerlerimizin değişimi çıkış değerlerimizin değişimiyle lineer olarak orantılı değil. 

[[#Log-odds]] değeri ($z$) 0'a yakınken giriş değerlerindeki küçük bir değişim $y$ değerinde büyük bir değişim yaratırken, $z$ değeri çok büyük veya çok küçük iken giriş değerlerindeki değişim $y$ değerinde çok küçük bir değişim yaratır.

| input | logistic output | required digits of precision |
| ----- | --------------- | ---------------------------- |
| 5     | 0.993           | 3                            |
| 6     | 0.997           | 3                            |
| 7     | 0.999           | 3                            |
| 8     | 0.9997          | 4                            |
| 9     | 0.9999          | 4                            |
| 10    | 0.99998         | 5                            |
>If you used squared loss to calculate errors for the sigmoid function, as the output got closer and closer to `0` and `1`, you would need more memory to preserve the precision needed to track these values.

>Instead, the loss function for logistic regression is [**Log Loss**](https://developers.google.com/machine-learning/glossary#Log_Loss). The Log Loss equation returns the logarithm of the magnitude of the change, rather than just the distance from data to prediction. Log Loss is calculated as follows:

![[Pasted image 20250711155713.png]]

- $(x,y)\in D$ (x, y) ikililerinden oluşan datasetimiz.
- $y$ verimizdeki etiket değeri, yani 0 veya 1.
- $y'$ modelimiz tahmini.
## **Regularization**
Logistic Regression'da büyük feature boyutlarında loss değeri 0'a oldukça yaklaşır, bu da overfitting demektir. Bu overfittingi önlemek için Logistic Regression modelleri 2 seçenekten birini kullanır.

1. $L_2$ regularization
2. Early Stopping: Eğitim adımlarını limitler.

>Any mechanism that reduces [**overfitting**](https://developers.google.com/machine-learning/glossary#overfitting). Popular types of regularization include:

- [**L1 regularization**](https://developers.google.com/machine-learning/glossary#L1_regularization)
- [**L2 regularization**](https://developers.google.com/machine-learning/glossary#L2_regularization)
- [**dropout regularization**](https://developers.google.com/machine-learning/glossary#dropout_regularization)
- [**early stopping**](https://developers.google.com/machine-learning/glossary#early_stopping) (this is not a formal regularization method, but can effectively limit overfitting)

>Regularization can also be defined as the penalty on a model's complexity.
## **Log-odds**

Bir olayın olma olasılığının logaritması olarak tanımlanır.

>If the event is a binary probability, then **odds** refers to the ratio of the probability of success (_p_) to the probability of failure (1-_p_). For example, suppose that a given event has a 90% probability of success and a 10% probability of failure. In this case, odds is calculated as follows:

 $odds=\dfrac{p}{1-p}=\dfrac{0.9}{0.1}=9$

>The log-odds is simply the logarithm of the odds. By convention, "logarithm" refers to [natural logarithm](https://wikipedia.org/wiki/Natural_logarithm), but logarithm could actually be any base greater than 1. Sticking to convention, the log-odds of our example is therefore:

$log-odds=ln(9)=2.22$

The log-odds function is the inverse of the [**sigmoid function**](https://developers.google.com/machine-learning/glossary#sigmoid-function).

