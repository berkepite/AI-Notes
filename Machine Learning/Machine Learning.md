# [[Supervised Learning]]

## [[Regression]]

### [[Linear Regression]]

## [[Classification]]
Bu modelde çıkış verileri numerik olmaktan ziyade bir çeşit belirtir. 2 türü vardır.
### Binary Classification
İkili sınıflandırma, ya evet ya hayır. Resimde kedi var mı yok mu?

### Multiclass Classification
Sınıflar birden fazla olur, mesela mnist datasetindeki 0-9 arası çıktılar, yine mnist datasetindeki giysi resimlerden (boot, ankle boot, sandals, shirt) örnek verilebilir.

# Unsupervised Learning
Bu modellerde verilerin bir etiketi yoktur, model verileri kendi ortak özelliklerine göre gruplamaya çalışır. Kendi gruplama kurallarını kendi oluşturur.

![[Pasted image 20250710212834.png]]

# Reinforcement Learning
Bir ortamda gösterilen davranışlara göre ödül ve ceza almaya dayalı bir eğitim yöntemidir. Bu modeller en fazla ödülü almak için optimize olurlar. Bir robotun bir alanda yürümesi veya AlphaGo oyununu oynayabilmesi bu modellerle olur.

# Generative AI
Birden çok türde input alabilen ve birden çok türde output verebilen bir modeller sınıfıdır. Eşsiz resimler çizebilir, şaka yapabilir, bir şeyi nasıl yapmamız gerektiğini anlatabilir. 
- Bir resim stilini çok çalışmış bir ressamın aynı resim stilinde resim çizmesi,
- Aynı türde müzik dinlemiş bir grubun yine aynı türe benzer müzikler yapması,
- Çok iyi bir LoL oyuncusunu analiz edip onun gibi oynayan yeni yetme oyuncular gibi.

| Model         | Input                                                                                                                                                                                                             | Example output                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Text-to-text  | Who invented the Le Mans race?                                                                                                                                                                                    | The 24 Hours of Le Mans was founded by the Automobile Club de l'Ouest (ACO), a motoring organization founded in 1906. The first race was held on 26 and 27 May 1923 on the Sarthe Circuit, a 13.426-kilometre (8.345-mile) road circuit located near the town of Le Mans in France. The race was originally conceived as a way to promote the ACO and the Sarthe region.  <br>Source: [Bard](https://bard.google.com/) |
| Text-to-image | An alien octopus floats through a portal while reading a newspaper.                                                                                                                                               | ![Image of a cartoon octopus.](https://developers.google.com/static/machine-learning/intro-to-ml/images/octopus.png)  <br>Source: [Imagen](https://imagen.research.google/)                                                                                                                                                                                                                                            |
| Text-to-video | A photorealistic teddy bear is swimming in the ocean at San Francisco. The teddy bear goes under water. The teddy bear keeps swimming under the water with colorful fishes. A panda bear is swimming under water. | ![Video of a teddy bear swimming underwater.](https://developers.google.com/static/machine-learning/intro-to-ml/images/teddy_bear.gif)  <br>Source: [Phenaki](https://phenaki.video/)                                                                                                                                                                                                                                  |
| Text-to-code  | Write a Python loop that loops over a list of numbers and prints the prime numbers.                                                                                                                               | for number in numbers:<br>  # Check if the number is prime.<br>  is_prime = True<br>  for i in range(2, number):<br>    if number % i == 0:<br>        is_prime = False<br>        break<br>  # If the number is prime, print it.<br>  if is_prime:<br>    print(number)<br> <br>Source: [Bard](https://bard.google.com/)                                                                                              |
| Image-to-text | ![Image of a flamingo.](https://developers.google.com/static/machine-learning/intro-to-ml/images/flamingo.png)                                                                                                    | This is a flamingo. They are found in the Caribbean.  <br>Source: [Google DeepMind](https://www.deepmind.com/blog/tackling-multiple-tasks-with-a-single-visual-language-model)                                                                                                                                                                                                                                         |
>To produce unique and creative outputs, generative models are initially trained using an unsupervised approach, where the model learns to mimic the data it's trained on. The model is sometimes trained further using supervised or reinforcement learning on specific data related to tasks the model might be asked to perform, for example, summarize an article or edit a photo.

>Generative AI is a quickly evolving technology with new use cases constantly being discovered. For example, generative models are helping businesses refine their ecommerce product images by automatically removing distracting backgrounds or improving the quality of low-resolution images.