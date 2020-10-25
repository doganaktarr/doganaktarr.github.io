## 

Problemde bize verilen  12-saat AM/PM formatlı saati 24-saat formatına çevirmemizi istiyor. Probleme [buradan](https://www.hackerrank.com/challenges/time-conversion/problem) ulaşabilirsiniz.

## **Örneğin**
- **s = '12:01:00PM'** girdisini

```python
'12:01:00'
``` 
olarak yazarken

- **s = '12:01:00AM'** girdisini

```python
'00:01:00'
```
olarak yazmak zorundayız.


**Input Format** her zaman hh:mm:ssAM veya hh:mm:ssPM olacak şekilde çözüme geçelim.

Öncelikle kullanıcıdan saat girdimizi alıyoruz

```python
s = input()
``` 
daha sonra yazacak olacağımız fonksiyonun sonucunu bir değişkene atayıp sonucu ekrana yazdırıyoruz.
```python
result = timeConversion(s)
print(result)
``` 
gelelim asıl işi yapacak olan fonksiyonumuza.
```python
def timeConversion(s):
    time = s.split(":")
``` 
burada ilk yaptığımız işlem girilen saati `split()` komutu ile her ':' işaretini gördüğümüzde ayırıyoruz. Böylece girdimiz 3 parçaya bölünmüş oluyor. 
```python
	if s[-2:] == "PM" and int(time[0]) < 12:
            time[0] = str(int(time[0])+12)
    
    if s[-2:] == "AM" and int(time[0]) > 12:
            time[0] = str(int(time[0])-12)

    if s[-2:] == "AM" and time[0] == "12":
            time[0] = "00"
```
Saat çevirmesi yapabilmemiz için saatin 12 den küçük veya büyük olup olmadığına aynı zamanda AM veya PM olduğuna bakmalıyız. Girdimizin son 2 hanesi her zaman 'AM' veya 'PM' vereceği için `s[-2:]` yardımıyla son 2 haneye bakıyoruz.
Daha sonra `split()` yardımıyla `time` değişkenine attığımız stringlerin ilk indisi her zaman saati vereceği için aldığımız son iki haneyle bunları kıyaslıyoruz. Yalnız bir şeye dikkat etmemiz gerek. Aldığımız veri her zaman string olacağı için matematiksel işlem yapamayız, bunu yapabilmek için `time` değişkeninden aldığımız veriyi `int()` yardımıyla integer değere çevirip daha sonra 12'den küçük, büyük veya eşit olduğuna bakıyoruz. Eğer saatimiz 12'den küçük ve "PM" ise öğleden sonra olduğu için saatimize 12 ekliyoruz. Eğer saatimiz 12'den büyük ve "AM" ise öğleden önce olduğu için saatimizden 12 çıkarıyoruz. Ve son olarak saatimiz 12'ye eşit ve "AM" ise Gece 12 yi geçti demektir bu yüzden saatimizi "00" yapıyoruz.
```python
    rtime = ':'.join(time)
    return str(rtime[:-2])
``` 
ve son olarak `join()` komutu yardımı ile `split()` komutu ile ayırdığımız girdiği tekrar birleştirip yeni bir değişkene atıyoruz. Bu değişkeni tekrar stringe çevirip fonksiyona return ediyoruz.

Kodumuzun bitmiş hali şu şekilde oluyor:
```python
def timeConversion(s):
    time = s.split(":")
    if s[-2:] == "PM" and int(time[0]) < 12:
            time[0] = str(int(time[0])+12)
    
    if s[-2:] == "AM" and int(time[0]) > 12:
            time[0] = str(int(time[0])-12)

    if s[-2:] == "AM" and time[0] == "12":
            time[0] = "00"
    
    rtime = ':'.join(time)
    return str(rtime[:-2])
    
s = input()
result = timeConversion(s)
print(result)    
```
Videolu çözüme [buradan](https://www.youtube.com/watch?v=MLih-p0-jMY) ulaşabilirsiniz.
