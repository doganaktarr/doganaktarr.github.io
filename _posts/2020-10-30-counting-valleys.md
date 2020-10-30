---
title: Counting Valleys | HackerRank
author: Doğan Aktar
date: 2020-10-30 18:46:00 +0800
categories: [Algorithms]
tags: [hackerrank]
---

## 

[Problemimizde](https://www.hackerrank.com/challenges/counting-valleys/problem) her adımının kaydını tutan bir sporcunun kaç defa vadi aştığını bulmamızı istiyor. Sporcumuz yokuş yukarı attığı her adımı, **U**, yokuş aşağı attığı her adımı ise **D** olarak kaydediyor. Peki sporcunun vadi aşıp aşmadığını nasıl anlayacağız?. Sporcumuz her zaman deniz seviyesinde başladığı için deniz seviyesinin altına her inip çıktığında bir vadi aştığını anlamış olacağız.

## Örneğin

```
8
UDDDUDUU
```
girdisi verilmiş olsun. Bu girdimizin çıktısının şu şekilde olması lazım;
```
1
```
Çıktımız **1**, çünkü deniz seviyesini _ , yukarı adımı /, ve aşağı adımı da \ olarak alalım. O zaman yukarıdaki girdimizin şekli şöyle olacak;
```
_/\      _
   \    /
    \/\/
```
burada görüldüğü gibi sporcumuz deniz seviyesinin altına sadece 1 defa inip çıkıyor.

Hadi çözüme geçelim:

```python
steps = int(input().strip())

path = input()

result = countingValleys(steps, path)

print(str(result) + '\n')
```
burada ilk olarak sporcumuzun kaç adım attığını daha sonrasında da gittiği yolu aldık. Sonra da aşağıda kodlayacağımız fonksiyonun sonucunu **result** isimli bir değişkene atayıp sonucumuzu ekrana yazdırdık. Şimdi fonksiyonumuzu kodlayalım.

```python
def countingValleys(steps, path):
    seaLevel = 0
    valley = 0

    for i in range(0, len(path)):
        if path[i] == "U":
            seaLevel += 1
        else:
            seaLevel -= 1
        if seaLevel == 0 and path[i] == "U":
            valley += 1           
    return valley
```

burada öncelikle iki adet 0 değerli değişken atadık. Birisi deniz seviyesinin altında mı üstünde olduğumuzu tutmak için, diğeri ise kaç vadi aştığımızı tutmak için. Daha sonra yolun başından sonuna kadar bir döngü açtık. Ve deniz seviyesine her çıktığımızda **seaLevel** değişkenimizi **1** arttırıp, deniz seviyesinden her indiğimizde ise **1** azalttık. Ve son olarak son attığımız adımla deniz seviyesine ulaştıysak ve bu adım yokuş yukarı **U** ise bir vadiyi aştık demektir, böylece aştığımız vadi sayısını tutacağımız değişkeni **1** arttırabiliriz.

Kodun tam hâli şöyle:
```python
def countingValleys(steps, path):
    seaLevel = 0
    valley = 0

    for i in range(0, len(path)):
        if path[i] == "U":
            seaLevel += 1
        else:
            seaLevel -= 1
        if seaLevel == 0 and path[i] == "U":
            valley += 1           
    return valley


steps = int(input().strip())

path = input()

result = countingValleys(steps, path)

print(str(result) + '\n')
```
