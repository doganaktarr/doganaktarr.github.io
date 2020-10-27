---
title: Number Line Jumps | HackerRank
author: Doğan Aktar
date: 2020-10-27 15:00:00 +0800
categories: [Algorithms]
tags: [hackerrank]
---

## 

Problemde bizden 2 farklı konumdan başlayıp 2 farklı mesafelerde zıplayan kanguruların aynı anda aynı noktada olabilme ihtimallerini soruyor. Probleme [buradan](https://www.hackerrank.com/challenges/kangaroo/problem) ulaşabilirsiniz.

- İlk kanguru **x1** noktasından başlıyor ve **v1** metre zıplıyor.
- İkinci kanguru **x2** noktasından başlıyor ve **v2** metre zıplıyor.

Eğer kangurular aynı sayıda sıçrama sonrası buluşabilmeleri mümkünse çıktı olarak "YES", buluşamıyorlarsa "NO" yazdırmamız gerekiyor.

## Örneğin
`0 3 4 2`

girdisinin çıktısı

`YES`

şeklinde oluyor. Çünkü ilk kangurumuz **0** konumundan başlayıp **3** metre sıçrarken ikinci kangurumuz **4** konumundan başlayıp **2** metre sıçrıyor. Kangurular **4** sıçrama sonrası **12** noktasında buluşuyorlar.

**Not:** Kangurular en fazla 10000 metreye kadar sıçrayabiliyor.

Gelelim çözümümüze:
```python
x1V1X2V2 = input().split()

x1 = int(x1V1X2V2[0])
v1 = int(x1V1X2V2[1])
x2 = int(x1V1X2V2[2])
v2 = int(x1V1X2V2[3])

result = kangaroo(x1, v1, x2, v2)

print(result + '\n')
```
burada öncelikle girilen girdileri bir listeye atıyoruz. Bu listenin ilk elemanı ilk kangurumuzun konumunu **x1** ve ikinci elemanı ilk kangurunun zıplama mesafesi **v1** olacak şekilde atıyoruz. Daha sonra 3. ve 4. eleman da aynı şekilde ikinci kangurunun konumu **x2** ve zıplama mesafesi **v2** olacak şekilde atıyoruz. Daha sonra birazdan çözecek olacağımız fonksiyonun sonucunu bir değişkene atayıp bunu ekrana yazdırıyoruz. Gelelim fonksiyonumuza:

```python
def kangaroo(x1, v1, x2, v2):
    for i in range(10000):
        if (x1 + v1) == (x2 + v2):
            return "YES"
        x1 += v1
        x2 += v2
    return "NO"
```
burada yaptığımız ilk işlem fonksiyona az önce aldığımız değerleri vermek. Daha sonra kanguruların maksimum zıplayabileceği mesafeye kadar bir döngü açıyoruz. Döngünün içinde her bir adımda her iki kangurunun da mevcut konumuna zıplama mesafesini ekleyip birbirleriyle aynı konumlarda mı diye kontrol ediyoruz. Eğer aynı yerdelerse
`"YES"` çıktısını veriyoruz. Aynı konumda değilseler de mevcut konumlarına sıçrama mesafelerini ekleyip tekrar kontrol ediyoruz. Böylece iki kanguruyu da her bir sıçramalarından sonra kontrol ediyoruz. Eğer kangurular döngü boyunca hiç aynı konumda olmadılalarsa hiç buluşamadılar demektir bu yüzden `"NO"` çıktısını veriyoruz.

Kodumuzun tam hali şu şekildedir:

```python
def kangaroo(x1, v1, x2, v2):
    for i in range(10000):
        if (x1 + v1) == (x2 + v2):
            return "YES"
        x1 += v1
        x2 += v2
    return "NO"

x1V1X2V2 = input().split()

x1 = int(x1V1X2V2[0])
v1 = int(x1V1X2V2[1])
x2 = int(x1V1X2V2[2])
v2 = int(x1V1X2V2[3])

result = kangaroo(x1, v1, x2, v2)

print(result + '\n')
```

Videolu çözüme [buradan](https://www.youtube.com/watch?v=CpFqlG7DqMM&t=5s) ulaşabilirsiniz.
