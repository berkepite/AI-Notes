Bu öğrenme şeklinde modeller etiketlenmiş verileri tekrar tekrar [[Loss]] function'la işleyerek (back propagation) daha önce görülmemiş veriler hakkında tahminde bulunabilir.

# Data
Datasetler feature'lar ve label'lardan oluşur.
> Labeled
![[Pasted image 20250710215107.png]]

> Unlabeled
> ![[Pasted image 20250710215213.png]]


## Dataset characteristics

>A dataset is characterized by its size and diversity. Size indicates the number of examples. Diversity indicates the range those examples cover. Good datasets are both large and highly diverse.

>Datasets can be large and diverse, or large but not diverse, or small but highly diverse. In other words, a large dataset doesn't guarantee sufficient diversity, and a dataset that is highly diverse doesn't guarantee sufficient examples.

>For instance, a dataset might contain 100 years worth of data, but only for the month of July. Using this dataset to predict rainfall in January would produce poor predictions. Conversely, a dataset might cover only a few years but contain every month. This dataset might produce poor predictions because it doesn't contain enough years to account for variability.

>A dataset can also be characterized by the number of its features. For example, some weather datasets might contain hundreds of features, ranging from satellite imagery to cloud coverage values. Other datasets might contain only three or four features, like humidity, atmospheric pressure, and temperature. Datasets with more features can help a model discover additional patterns and make better predictions. However, datasets with more features don't _always_ produce models that make better predictions because some features might have no causal relationship to the label.

# Model

>In supervised learning, a model is the complex collection of numbers that define the mathematical relationship from specific input feature patterns to specific output label values. The model discovers these patterns through training

# Training
Bir model tahminde bulunmadan önce eğitilmelidir. Bir modeli eğitmek için etiketli veri setleri veririz. Modelin ana amacı feature'lardan bir etiketi en iyi şekilde tahmin eden algoritmayı geliştirmektir. 

Model çıktılarıyla olması gereken değerleri karşılaştırır ve bu farka *loss* denir, bu karşılaştırmalardan sonra kademeli olarak model iç değerlerini günceller.

Mesela bir evin değeri 3M tahmin edildi ama gerçek değeri 2.7M, aradaki farkı kapatmak için model kendi algoritmasını 2.7M'e yakınsayacak şekilde değiştirmeye çalışır. Sonuç olarak ortalamada her bir örnek veri için en iyi tahmini yapmaya çalışır.

>During training, ML practitioners can make subtle adjustments to the configurations and features the model uses to make predictions. For example, certain features have more predictive power than others. Therefore, ML practitioners can select which features the model uses during training. For example, suppose a weather dataset contains`time_of_day` as a feature. In this case, an ML practitioner can add or remove `time_of_day` during training to see whether the model makes better predictions with or without it.

# Evaluation
Evaluasyon eğitilen modeli test etmek için kullanılır. Eğitilen modele etiketi çıkartılmış veriler verilir ve bu verilere göre yaptığı tahminin başarısı ölçülür.

# Inference
> Once we're satisfied with the results from evaluating the model, we can use the model to make predictions, called [inferences](https://developers.google.com/machine-learning/glossary#inference), on unlabeled examples. In the weather app example, we would give the model the current weather conditions—like temperature, atmospheric pressure, and relative humidity—and it would predict the amount of rainfall.