---
title: Staircase | HackerRank
author: Doğan Aktar
date: 2020-10-24 21:46:00 +0800
categories: [Algorithms]
tags: [hackerrank]
---

## 

Merhaba, bu problem ile başladığım problem çözümü serisinde severek kullandığım [HackerRank](https://www.hackerrank.com/dashboard) sitesinde bana ve size yeni bilgiler katacak, farklı bakış açılarıyla çözülebilecek problemleri paylaşacağım. Hemen ilk problemimize geçelim. İlk problem olarak Staircase problemini çözeceğiz. Probleme [buradan](https://www.hackerrank.com/challenges/staircase/problem) ulaşabilirsiniz.

Problemde bizden girilen integer **n** değeri kadar karelerden "**#**" oluşan bir merdiven yapmamızı istiyor. Fakat bu merdiven giderek azalan boşluklardan oluşmak zorunda.

Örneğin: **n = 4** girdisi için istenen çıktı:

```python
   #
  ##
 ###
####
```
verilen örnekteki gibi merdiven sağa dayalı olmalıdır.

Gelelim problemimizin çözümüne.

Öncelikle kullanıcıdan kaç basamaklı bir merdiven istediğini alıp, daha sonra yazacağımız staircase fonksiyonuna bu değeri atıyoruz.
```python
n = int(input())
staircase(n)
```
daha sonra merdiveni hesaplayacak fonksiyonu yazıyoruz:

```python
def staircase(n):
    for i in range(1, n+1):
        print(" " * (n-i) + i*"#")
```
döngüyü 1 den başlatmamızın nedeni **print()** fonksiyonunda **n-i** sayıda boşluk ve **i** sayıda kare yazdırmamız gerektiği. Eğer döngüyü 0 dan başlatmış olsaydık ilk adımda n sayıda boşluk ve 0 sayıda kare yazdırmış olacaktı. Döngüyü **n+1** e kadar götürmemizin nedeni ise pythonda **for** döngüsünün aldığı 2. değere **kadar** gitmesi.Eğer bu sayı n olsayı her zaman 1 adımımız eksik olacaktı.

Videolu çözüme [buradan](https://www.youtube.com/watch?v=6a0Fw7q7Amk&t=2s) ulaşabilirsiniz.
