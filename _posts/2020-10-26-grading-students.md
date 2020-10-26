---
title: Grading Students | HackerRank
author: Doğan Aktar
date: 2020-10-26 16:41:00 +0800
categories: [Algorithms]
tags: [hackerrank]
---

## 

Problemde bizden belli kurallara göre öğrencileri notlandırmamızı istiyor. Probleme [buradan](https://www.hackerrank.com/challenges/grading/problem) ulaşabilirsiniz. Öğrencileri şu kurallara göre notluyoruz:

- Eğer 40' tan aşağı not alıyorlarsa kalıyorlar.
- Diğer bir kural ise eğer notun bir sonraki 5'in katıyla arasındaki fark 3'ten küçük ise bir sonraki 5'in katına yuvarlıyoruz.

## Örneğin
- **grade = 84** ise çıktı **85** oluyor.(Çünkü 85-84 < 3)
- **grade = 29** ise çıktı **29** oluyor.(29 < 40)
- **grade = 38** ise çıktı **40** oluyor.(Çünkü 40-38 < 3)

olacak şekilde notlandırıyoruz. Mesela şöyle bir örnek girdi olsun:
```
4
73
67
38
33
```
girdisinin çıktısı
```
75
67
40
33
```
şeklinde olmalıdır. Şimdi çözüme geçelim.

```python
grades_count = int(input().strip())
grades = []

for _ in range(grades_count):
    grades_item = int(input())
    grades.append(grades_item)

result = gradingStudents(grades)
print('\n'.join(map(str, result)))
```
öncelikle yukarıda görüldüğü gibi ilk girdi olarak kullanıcıdan kaç tane not gireceğini alıyoruz. Daha sonra girilecek notlar için `grades` isimli bir boş liste açıyoruz. Daha sonra girilecek her notu listeye eklemek için bir döngü açıyoruz. Ve son olarak birazdan yazacağımız fonksiyonun bulduğu sonucu alt alta çıktılar olacak şekilde ekrana yazdırıyoruz. Şimdi gelelim fonksiyonumuza.

```python
def gradingStudents(grades):
    for i in range(0, len(grades)):
        if grades[i] > 37 and grades[i] % 5 != 0 and (grades[i] % 5) > 2:
            grades[i] += 5 - (grades[i] % 5 )
    return (grades)
```
burada ilk yaptığımız işlem yukarıda notları atadığımız listenin her bir elemanını gezmek için bir döngü açmak. Daha sonraki ilk şart notumuzun 37 den büyük olması, çünkü 38'den küçük notlar başarısız not olduğu için yuvarlanabilirliğine bakmaksızın aynen yazdırıyoruz. Diğer şart notun 5'e göre modunu almak, eğer not 5' e tam bölünüyorsa 5'in zaten katıdır, yani yuvarlamamıza gerek kalmadan aynen yazdırıyoruz. Ve son kalan ihtimal notun 38 den büyük ve 5'in katı olmaması. Burada yapacağımız işlem ise notun 5'e göre modunun 2'den büyük olup olmadığına bakmak. Eğer 2'den büyük ise notun kendisinden bir sonraki 5'in katından farkı 3'ten küçük demektir, yani yuvarlanabilir. Eğer bu şartı sağlıyorsa notu alıyoruz ve notun 5'e göre modunu 5'ten çıkarıp nota ekliyoruz. Böylece notumuz kendisinden bir sonraki 5'in katına yuvarlanmış oluyor.

Kodun tam hali şöyledir.
```python
def gradingStudents(grades):
    for i in range(0, len(grades)):
        if grades[i] > 37 and grades[i] % 5 != 0 and (grades[i] % 5) > 2:
            grades[i] += 5 - (grades[i] % 5 )
    return (grades)

grades_count = int(input().strip())
grades = []

for _ in range(grades_count):
    grades_item = int(input())
    grades.append(grades_item)

result = gradingStudents(grades)
print('\n'.join(map(str, result)))
```

Videolu çözüme [buradan](https://www.youtube.com/watch?v=aUnwlOtaqW0&t=4s) ulaşabilirsiniz.
