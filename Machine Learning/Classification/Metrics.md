## **Accuracy**
Accuracy tüm doğru tahminlerin tüm tahminlere oranıdır.

![[Pasted image 20250711164517.png]]

>Because it incorporates all four outcomes from the [confusion matrix](https://developers.google.com/machine-learning/crash-course/classification/thresholding#confusion_matrix) (TP, FP, TN, FN), given a balanced dataset, with similar numbers of examples in both classes, accuracy can serve as a coarse-grained measure of model quality. For this reason, it is often the default evaluation metric used for generic or unspecified models carrying out generic or unspecified tasks.

>However, when the dataset is imbalanced, or where one kind of mistake (FN or FP) is more costly than the other, which is the case in most real-world applications, it's better to optimize for one of the other metrics instead.

>For heavily imbalanced datasets, where one class appears very rarely, say 1% of the time, a model that predicts negative 100% of the time would score 99% on accuracy, despite being useless.

## **Recall**
True positive rate de denir. Tüm doğru sınıflanmış pozitiflerin tüm gerçek pozitiflere oranıdır.

![[Pasted image 20250711164905.png]]

>False negatives are actual positives that were misclassified as negatives, which is why they appear in the denominator. In the spam classification example, recall measures the _fraction of spam emails that were correctly classified as spam._ This is why another name for recall is **probability of detection**: it answers the question "What fraction of spam emails are detected by this model?"

## **False Positive Rate**

Tüm yanlış sınıflandırılmış negatiflerin tüm gerçek negatiflere oranıdır.

![[Pasted image 20250711165406.png]]

>False positives are actual negatives that were misclassified, which is why they appear in the denominator. In the spam classification example, FPR measures the _fraction of legitimate emails that were incorrectly classified as spam,_ or the model's rate of false alarms.

>In an imbalanced dataset where the number of actual negatives is very, very low, say 1-2 examples in total, FPR is less meaningful and less useful as a metric.

## **Precision**

Doğru bir şekilde sınıflandırılmış tüm pozitiflerin tüm pozitif olarak sınıflandırılmışlara oranıdır.

![[Pasted image 20250711165633.png]]

>Precision improves as false positives decrease, while recall improves when false negatives decrease. But as seen in the previous section, increasing the classification threshold tends to decrease the number of false positives and increase the number of false negatives, while decreasing the threshold has the opposite effects. As a result, precision and recall often show an inverse relationship, where improving one of them worsens the other.

## **F1 Score**
>The **F1 score** is the harmonic mean (a kind of average) of precision and recall.

![[Pasted image 20250711170032.png]]

>This metric balances the importance of precision and recall, and is preferable to accuracy for class-imbalanced datasets. When precision and recall both have perfect scores of 1.0, F1 will also have a perfect score of 1.0. More broadly, when precision and recall are close in value, F1 will be close to their value. When precision and recall are far apart, F1 will be similar to whichever metric is worse.


## Choice of metric and tradeoffs

>The metric(s) you choose to prioritize when evaluating the model and choosing a threshold depend on the costs, benefits, and risks of the specific problem. In the spam classification example, it often makes sense to prioritize recall, nabbing all the spam emails, or precision, trying to ensure that spam-labeled emails are in fact spam, or some balance of the two, above some minimum accuracy level.

| Metric                           | Guidance                                                                                                                                                                                                                              |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Accuracy                         | Use as a rough indicator of model training progress/convergence for balanced datasets.<br><br>For model performance, use only in combination with other metrics.<br><br>Avoid for imbalanced datasets. Consider using another metric. |
| Recall  <br>(True positive rate) | Use when false negatives are more expensive than false positives.                                                                                                                                                                     |
| False positive rate              | Use when false positives are more expensive than false negatives.                                                                                                                                                                     |
| Precision                        | Use when it's very important for positive predictions to be accurate.                                                                                                                                                                 |

## **Classification ROC - AUC**

Bu metriklerin hepsi tek bir threshold değeri üzerinden hesaplandı az önce. Farklı threshold değerleri için de hesaplamalar yapmak istiyorsak farklı araçlar kullanmamız gerekiyor.

### Receiver-operating characteristic curve (ROC)
>The [**ROC curve**](https://developers.google.com/machine-learning/glossary#roc-receiver-operating-characteristic-curve) is a visual representation of model performance across all thresholds. The long version of the name, receiver operating characteristic, is a holdover from WWII radar detection.

>The ROC curve is drawn by calculating the true positive rate (TPR) and false positive rate (FPR) at every possible threshold (in practice, at selected intervals), then graphing TPR over FPR. A perfect model, which at some threshold has a TPR of 1.0 and a FPR of 0.0, can be represented by either a point at (0, 1) if all other thresholds are ignored, or by the following:

![[Pasted image 20250711171820.png]]

### Area under the curve (AUC)

>The [**area under the ROC curve (AUC)**](https://developers.google.com/machine-learning/glossary#AUC) represents the probability that the model, if given a randomly chosen positive and negative example, will rank the positive higher than the negative.

>The perfect model above, containing a square with sides of length 1, has an area under the curve (AUC) of 1.0. This means there is a 100% probability that the model will correctly rank a randomly chosen positive example higher than a randomly chosen negative example. In other words, looking at the spread of data points below, AUC gives the probability that the model will place a randomly chosen square to the right of a randomly chosen circle, independent of where the threshold is set.

![[Pasted image 20250711172125.png]]
>In more concrete terms, a spam classifier with AUC of 1.0 always assigns a random spam email a higher probability of being spam than a random legitimate email. The actual classification of each email depends on the threshold that you choose.

>For a binary classifier, a model that does exactly as well as random guesses or coin flips has a ROC that is a diagonal line from (0,0) to (1,1). The AUC is 0.5, representing a 50% probability of correctly ranking a random positive and negative example.

>In the spam classifier example, a spam classifier with AUC of 0.5 assigns a random spam email a higher probability of being spam than a random legitimate email only half the time.

![[Pasted image 20250711172253.png]]

### Precision-Recall Curve

>AUC and ROC work well for comparing models when the dataset is roughly balanced between classes. When the dataset is imbalanced, precision-recall curves (PRCs) and the area under those curves may offer a better comparative visualization of model performance. Precision-recall curves are created by plotting precision on the y-axis and recall on the x-axis across all thresholds.

![[Pasted image 20250711172448.png]]

### AUC and ROC for choosing model and threshold

>AUC is a useful measure for comparing the performance of two different models, as long as the dataset is roughly balanced. The model with greater area under the curve is generally the better one.

![[Pasted image 20250711172652.png]]

>If false positives (false alarms) are highly costly, it may make sense to choose a threshold that gives a lower FPR, like the one at point A, even if TPR is reduced. Conversely, if false positives are cheap and false negatives (missed true positives) highly costly, the threshold for point C, which maximizes TPR, may be preferable. If the costs are roughly equivalent, point B may offer the best balance between TPR and FPR.



![[Pasted image 20250711172753.png]]

## **Classification - Prediction Bias**

Modelin tahminlerinin ortalamasıyla gerçek değerlerin ortalamasının farkıdır.

>Prediction bias is the difference between the mean of a model's [**predictions**](https://developers.google.com/machine-learning/glossary#prediction)and the mean of [**ground-truth**](https://developers.google.com/machine-learning/glossary#ground-truth) labels in the data. A model trained on a dataset where 5% of the emails are spam should predict, on average, that 5% of the emails it classifies are spam. In other words, the mean of the labels in the ground-truth dataset is 0.05, and the mean of the model's predictions should also be 0.05. If this is the case, the model has zero prediction bias. Of course, the model might still have other problems.

>If the model instead predicts 50% of the time that an email is spam, then something is wrong with the training dataset, the new dataset the model is applied to, or with the model itself. Any significant difference between the two means suggests that the model has some prediction bias.

>Prediction bias can be caused by:

- Biases or noise in the data, including biased sampling for the training set
- Too-strong regularization, meaning that the model was oversimplified and lost some necessary complexity
- Bugs in the model training pipeline
- The set of features provided to the model being insufficient for the task