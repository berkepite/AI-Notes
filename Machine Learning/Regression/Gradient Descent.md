Bu aslında modeldeki ağırlıklar ve biaslarla oynayan matematiksel işlemdir.

Kullanıcının belirlediği tekrar sayısıyla aşağıdaki işlemleri yapar. Ağırlık ve bias değerleri 0'a yakın random değerlerle başlar.

1. Loss function'ı kullanarak ağırlık ve biaslardan loss değerini hesapla.
2. Loss değerini azaltmak için ağırlık ve bias değerlerini hangi yöne götüreceğini belirle.
3. Ağırlık ve bias değerlerini bu yönde küçük bir miktarda değiştir.
4. İlk adıma dön ve loss değerini daha fazla küçültemeyeceğin yere kadar devam et.

![[Pasted image 20250711000538.png]]

## **Convergence**
Loss değerinin belirli bir düzeye gelip model eğitilmeye devam edilse bile daha fazla azaltılamayacağı durumdur.