Classification bir örneğin hangi sınıfa ait olduğunu tahmin eder. Örnek olarak sınıflardan biri *spam* diğeri *not-spam* olabilir. 2 çeşidi vardır.

1. [[Binary Classification]]
2. [[Multi-class Classification]]

## **Threshold**
Diyelim ki bir [[Logistic Regression]] modelimiz var, bu modelin çıktısı 0.7 diyelim. Bu 0.7 spam olma olasılığı olsun; *1 = spam, 0 = spam değil*.
Hangi değer aralığının spam olup olmadığını **threshold** değeri ile belirliyoruz.
Threshold değerimiz 0.6 ise 0.6 dan daha büyük değerler *spam* olarak sınıflanır, 0.6 ve daha küçük değerler ise *not-spam* olarak sınıflanır.

## **Confusion Matrix**
|                    | Actual positive                                                                                                                                                 | Actual negative                                                                                                                                 |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Predicted positive | **True positive (TP)**: A spam email correctly classified as a spam email. These are the spam messages automatically sent to the spam folder.                   | **False positive (FP)**: A not-spam email misclassified as spam. These are the legitimate emails that wind up in the spam folder.               |
| Predicted negative | **False negative (FN)**: A spam email misclassified as not-spam. These are spam emails that aren't caught by the spam filter and make their way into the inbox. | **True negative (TN)**: A not-spam email correctly classified as not-spam. These are the legitimate emails that are sent directly to the inbox. |
>Notice that the total in each row gives all predicted positives (TP + FP) and all predicted negatives (FN + TN), regardless of validity. The total in each column, meanwhile, gives all real positives (TP + FN) and all real negatives (FP + TN) regardless of model classification.

>When the total of actual positives is not close to the total of actual negatives, the dataset is [**imbalanced**](https://developers.google.com/machine-learning/glossary#class_imbalanced_data_set). An instance of an imbalanced dataset might be a set of thousands of photos of clouds, where the rare cloud type you are interested in, say, volutus clouds, only appears a few times.

Bu matrix değerleri belli [[Metrics|performans metriklerini]] hesaplamak için kullanılır.

