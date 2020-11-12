---
title: Utopian Tree | HackerRank
author: Doğan Aktar
date: 2020-11-12 15:19:00 +0800
categories: [Algorithms]
tags: [hackerrank]
---

## 

Ütopik bir ağaç yılda 2 döngü şeklinde büyüyor. Her ilkbaharda mevcut yüksekliğinin 2 katı kadar büyüyor ve her yaz da mevcut boyu 1 metre artıyor. [Problemde](https://www.hackerrank.com/challenges/utopian-tree/problem) bize ilk dikildiğinde 1 metre olan fidanımızın **n** döngü sonraki boyunun ne kadar olacağını soruyor.

## Örneğin 

büyüme döngüsü sayısı **n = 5** olsun. Hesaplamamız şöyle olacak:
```
Period  Height
0          1
1          2
2          3
3          6
4          7
5          14
```
Bir örnek daha verelim. Örnek girdi şöyle olsun:
```
3
0
1
4
```
Burada 3 ağaç gireceğini ve her bir ağacın kaç döngü geçireceğini vermiş. Bu girdinin çıktısı:
```
1
2
7
```
olmalıdır. Çünkü:
- İlk girdide ağaç **0** döngü geçiriyor yani mevcut boyuyla kalıyor. İlk ekildiklerinde 1 metre oldukları için ilk ağacın boyu 1 metre.
- İkinci girdide ağac **1** döngü geçiriyor. İlk döngümüz ilkbahar ile başladığı için ağaç boyunu 2'ye katlıyor böylece döngü sonunda boyu **2** metre oluyor.
- Üçüncü girdide ise ağacımız **4** döngü geçiriyor. 1. döngüde boyunu ikiye katlıyor döngü sonu boyu **2** metre. 2. döngüde yaz mevsimi yani boyu 1 metre artıyor döngü sonu boyu **3** metre. 3. döngü tekrar ilkbahar boyunu 2'ye katlıyor ve döngü sonu yeni boyu **6** metre. 4. döngüde son olarak yaz mevsiminde boyu 1 metre artıyor ve ağacımızın son boyu **7** metre.

Gelelim kod kısmına:

```python
t = int(input())
for t_itr in range(t):
    n = list(map(int, input().rstrip().split()))

    result = utopianTree(n)

    print(result)
```
Burada ilk olarak kaç ağaç gireceğini alıp ağaç sayısı kadar girdi alacak bir döngü açtık. Böylece her girilen ağacı bir listeye attık. Daha sonra şimdi yazacağımız fonksiyonun sonucunu **result** isimli bir değişkene atayıp onu ekrana yazdırdık. Gelelim fonkisyonumuza:
```python
def utopianTree(n):
    growth = 0
    for i in n:
        for j in range(0, i+1):
            if j % 2 == 0:
                growth += 1
            elif j % 2 == 1:
                growth *= 2
        return growth
```

Burada yaptığımı ilk işlem ağacın boyunu tutmak için değeri 0 olan bir değişken yazmak. Daha sonra 2 döngü açıyoruz ilk döngü listedeki ağaçların büyüme döngülerinin sayısını almak için. İkincisi ise aldığımız büyüme döngülerinde işlem yapabilmek için. İlk döngümüz 0 dan başlıyor ve ağacımız ilk dikildiğinde 1 metre. Sonraki mevsimde ise boyunu 2'ye katlıyor. Ve bu döngü sürekli böyle devam ediyor. Yani döngünün tek olduğu yıllar boyunu 2'ye katlarken boyunun çift olduğu yıllarda boyu yalnızca 1 metre artıyor. Mod `%` operatörünün yardımıyla bunu rahatlıkla yapıp problemimizi çözüyoruz.

Kodun tam hali şu şekilde:

```python
def utopianTree(n):
    growth = 0
    for i in n:
        for j in range(0, i+1):
            if j % 2 == 0:
                growth += 1
            elif j % 2 == 1:
                growth *= 2
        return growth


t = int(input())
for t_itr in range(t):
    n = list(map(int, input().rstrip().split()))

    result = utopianTree(n)

    print(result)

```
