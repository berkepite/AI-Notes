Bir model eğitirken verilerimizin değerleri 0-1 arasında veya 1000-5000 arasında olabilir, bu da ağırlık değerlerinin ya çok büyük ya da çok küçük olmasını sağlayabilir. Bunun için verileri normalize etmemiz gerekiyor.
## **Z-Score**
Her bir giriş değeri kendi *Z-Score* değerine dönüştürülür. Z-Score değeri bir giriş değerinin ortalamadan kaç standart sapma kadar farklı olduğunu gösterir.

60 ortalamalı 10 standart sapmalı bir feature düşünelim.
75 değeri bu durumda +1.5 *Z-Score* değerine sahip olur.

$Z\text{-}Score = (75-60) / 10 = +1.5$

38 değeri bu durumda -2.2 *Z-Score* değerine sahip olur.

$Z\text{-}Score = (38-60) / 10 = -2.2$
