Giriş değerleri ile çıkış değerleri doğru orantılı veya ters orantılı ise kullanılır.
Feature'lar ve label'lar arasındaki ilişkiyi bulur.

Bir arabanın ağırlığıyla harcadığı yakıt miktarını tahmin etmeye çalışalım.
Verilerimiz aşağıdaki gibi olsun.

| Pounds in 1000s (feature) | Miles per gallon (label) |
| ------------------------- | ------------------------ |
| 3.5                       | 18                       |
| 3.69                      | 15                       |
| 3.44                      | 18                       |
| 3.43                      | 16                       |
| 4.34                      | 15                       |
| 4.42                      | 14                       |
| 2.37                      | 24                       |
Bu verileri bir grafiğe koyduğumuzda aşağıdaki gibi genel bir çizgi çekebiliyoruz çünkü feature'larla label arasında bir lineer orantı var.

![[Pasted image 20250710225208.png]]

Matematiksel olarak model böyle tanımlanabilir 
$y = mx + b$

-  $y$ is miles per gallon—the value we want to predict.
-  $m$ is the slope of the line.
-  $x$ is pounds—our input value.
-  $b$ is the y-intercept.

Makine öğrenmesinde bu ifadeyi şu şekilde yazarız
$y' = b + w_1x_1$

-  $y'$ is the predicted label—the output.
- $b$ is the [**bias**](https://developers.google.com/machine-learning/glossary#bias-math-or-bias-term) of the model. Bias is the same concept as the y-intercept in the algebraic equation for a line. In ML, bias is sometimes referred to as $w$. Bias is a [**parameter**](https://developers.google.com/machine-learning/glossary#parameter) of the model and is calculated during training.
- $w_1$ is the [**weight**](https://developers.google.com/machine-learning/glossary#weight) of the feature. Weight is the same concept as the slope in the algebraic equation for a line. Weight is a [**parameter**](https://developers.google.com/machine-learning/glossary#parameter) of the model and is calculated during training.
- $x_1$ is a [**feature**](https://developers.google.com/machine-learning/glossary#feature)—the input.

In our example, we'd calculate the weight and bias from the line we drew. The bias is 34 (where the line intersects the y-axis), and the weight is –4.6 (the slope of the line). The model would be defined as $y'=34+(-4.6)x_1$ , and we could use it to make predictions. For instance, using this model, a 4,000-pound car would have a predicted fuel efficiency of 15.6 miles per gallon.

![[Pasted image 20250710230733.png]]
> Using the model, a 4,000-pound car has a predicted fuel efficiency of 15.6 miles per gallon.

Modeller birden çok feature'a bağımlı olabilir, aşağıda 5 feature'a dayalı bir modelin ifadesi verilmiştir.

$y'=b+w_1x_1+w_2x_2+w_3x_3+w_4x_4+w_5x_5$

Bu yeni feature değerleri; motor gücü, silindir sayısı, hızlanma, motor büyüklüğü gibi değerler olabilir.