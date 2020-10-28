---
title: Sub-array Division | HackerRank
author: Doğan Aktar
date: 2020-10-28 16:46:00 +0800
categories: [Algorithms]
tags: [hackerrank]
---

## 

[Problemimizde](https://www.hackerrank.com/challenges/the-birthday-bar/problem) Lily ve Ron isimli iki çocuğa her diliminin üstünde sayı yazan bir çikolata veriliyor. Bu çikolatayı paylaştıracak olan kişi Lily. Fakat Lily çikolatayı şu şekilde paylaştırmak istiyor:

- Ron'un doğum ayına denk gelecek şekilde bitişik dilim olmalı.
- Dilimlerin üzerindeki sayıların toplamı da doğduğu güne denk gelmeli.

## Örneğin

Dilimleri üzerindeki sayılar sırasıyla **s = [2,2,1,3,2]** olacak şekilde 5 parçalı bir çikolata verilsin. Ron'un doğum günü **d = 2** ve doğduğu ay **m = 2** olsun. Yani üzerindeki sayıların toplamının 4 olduğu 2 bitişik dilim arıyoruz. Bu şartı sağlayan **[2,2]** ve **[1,3]** dilimleri var. Bu yüzden çıktımız **2** olacak.

Örnek girdi şöyle verilsin:
```
5
1 2 1 3 2
3 2
```
Bize **5** dilimli bir çikolata verilip üzerindeki sayıların toplamı **3** olan **2** bitişik dilim mevcut mu diye kontrol etmemiz isteniyor. Bu şartı sağlayan **[1,2]** ve **[2,1]** dilimleri mevcut. Dolayısıyla çıktımız;

```
2
```
olmalıdır.

Gelelim kod kısmına.

```python
n = int(input().strip())

s = list(map(int, input().rstrip().split()))

dm = input().rstrip().split()

d = int(dm[0])

m = int(dm[1])

result = birthday(s, d, m)

print(str(result) + '\n')
```

Toplamda 3 girdi alacağımız için burada yaptığımız işlem ilk olarak kaç dilimli bir çikolata girileceğini almak. Daha sonrasında ise girilen her bir dilimi **s** isimli bir değişkene liste olarak atıyoruz. Ve son girdimiz gün ve ay olacağı için onları **dm** isimli bir değişkene atıp onun ilk elemanını(günü) **d** isimli değişkene atayıp ikinci elemanı(ayı) **m** isimli bir değişkene atıyoruz. Ve son olarak fonksiyonun sonucunu **result** isimli bir değişkene atayıp ekrana yazdırıyoruz. Gelelim fonksiyonumuza.

```python
def birthday(s, d, m):
    count = 0
    output = 0
    if len(s) < m:
        return 0
    elif len(s) == 1 and s[0] == d:
        return 1
    else:
        for i in range(0, len(s) - m + 1):
            for j in range (i, i + m):
                count += s[j]
            if count == d:
                output += 1    
                count = 0
            else:
                count = 0
    return output  
```
Burada 3 ihtimali ele alarak çözmemiz lazım;

1. İhtimal dilim sayısının doğum ayından küçük olması, böyle bir durumda çikolata veremeyeceğimiz için çıktımız **0**

2. İhtimal dilim sayısının 1 olması, böyle bir durumda **s**'in tek elemanı olan **s[0]** doğum gününe eşit ise tek bir dilim vardır ve bu da şartı sağlıyordur o yüzden çıktımız **1**

3. İhtimal ise dilim sayısının doğum ayından fazla olması. Bu durumda doğum ayı sayısındaki her bitişik dilimin toplamının doğum gününe eşit olup olmadığını kontrol etmemiz lazım. Açtığımız ilk döngüde listenin ilk elemanından yani ilk dilimden **son dilim - doğum ayı** kadar gitmemiz lazım. Bunu yapmamızın nedeni **out of index** hatasından kaçınmak. **+1** eklememizin nedeni ise pythonda for döngüsünün aldığı 2. değere **kadar** gitmesi. Her elemanını gezme olayını tamamladıktan sonra 2. bir döngü açıyoruz. Bu döngüde bulunduğumuz dilimden sonraki doğum ayı sayısındaki bitişik dilimlerin toplamlarının doğum gününe eşit olup olmadığına bakmak. Eğer eşitlerse çıktımız olacak **output** değişkenine bakıyoruz değil ise bir sonraki elemana geçip tekrar bitişik dilimlere bakıyoruz. Böylece doğum ayı kadar olan her bir bitişik dilimi kontrol etmiş oluyoruz. 

Videolu çözüme [buradan](https://www.youtube.com/watch?v=oOH6lyWnbwc) ulaşabilirsiniz.
