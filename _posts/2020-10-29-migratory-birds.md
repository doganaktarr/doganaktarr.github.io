---
title: Migratory Birds | HackerRank
author: Doğan Aktar
date: 2020-10-29 18:07:00 +0800
categories: [Algorithms]
tags: [hackerrank]
---

## 

Bu [problemde](https://www.hackerrank.com/challenges/migratory-birds/problem) göç eden kuşları inceleyen bir grupta görevliyiz. Göç eden her kuş tipi bir integer değer ile belirtiliyor. Bizden istenen iste göç eden kuş grubunda en fazla hangi kuş tipi olduğunu bulmak. Eğer aynı sayıda kuş tipi var ise en düşük değeri almamızı istiyor. Mesela göç eden kuşların listesi şöyle olsun **arr = [1,1,2,2,3]**. Burada görüldüğü üzere en fazla sayıda olan 2 kuş tipi var **1** ve **2**. En küçük integer tipi alacağımız için problemimizin çıktısı **1** olacak.

## Örneğin
```
6
1 4 4 4 5 3
```
girdisinin çıktısı
```
4
```
olmalı. Çünkü en fazla olan kuş tipi **4**.

Gelelim çözümümüze:

```python
arr_count = int(input().strip())

arr = list(map(int, input().rstrip().split()))

result = migratoryBirds(arr)

print(str(result) + '\n'
```
burada yaptığımız işlem öncelikle kullanıcıdan kaç adet kuş gireceği. Bu değeri aldıktan sonra girilen her bir kuşu **arr** isimli bir değişkene atıyoruz. Sonrasında ise aşağıda kodlayacağımız fonksiyonun sonucunu **result** isimli bir değişkene atayıp ekrana yazdıracağız.
```python
def migratoryBirds(arr):
    return max(set(arr), key = arr.count)
```
burada fonksiyonumuzun yaptığı işlem öncelikle `set()` komutu ile listedeki aynı elemanların sadece 1 kere alındığı yeni bir kütüphane oluşturuyoruz. Örneğin **liste = [1,2,2,3,3]** listesinin **set(liste)** hâli şöyledir; **{1,2,3}**. Bu işlemi yaptıktan sonra `key` yardımıyla kütüphanedeki her bir elemanı alıp listede kaç tane olduğuna bakıyoruz. `max()` yardımı ile de en fazla sayıda olanı alıp fonksiyona `return` ediyoruz. Peki ya aynı sayıda birden fazla eleman olursa? Python'da `max()` komutu default olarak aynı sayıda olanların en ufağını aldığı için bu problemde sorunsuz bir şekilde çalışacaktır.

Kodun bitmiş hâli şöyledir:

```python
def migratoryBirds(arr):
    return max(set(arr), key = arr.count)


arr_count = int(input().strip())

arr = list(map(int, input().rstrip().split()))

result = migratoryBirds(arr)

print(str(result) + '\n')
```

Videolu çözüme [buradan](https://www.youtube.com/watch?v=CqK4WyP7xsk&t=9s) ulaşabilirsiniz.
