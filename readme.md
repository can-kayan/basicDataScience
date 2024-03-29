# About
Basic operations with numpy, pandas and matplotlib
## Numpy
### range
Number generation from 0 to 10

```bash
lise =np.array(range(0,10))
print(lise)
```
### arange
Increments of two from 0 to 20
```bash
liste=np.arange(0,20,2)
print(liste)
```

### zeos --> 
Generating a matrix or list with values of 0
```bash
zr1=np.zeros(5)
zr2=np.zeros((2,5))
print(zr2)
```

### ones
produces matrix or list with values 1
```bash
one1=np.ones(5)
one2=np.ones((5,4))
print(one2)
```

### linspace
Generate 30 evenly spaced numbers from 0 to 10
```bash
lin=np.linspace(0,10,30)
print(lin)
```

### eye
Creates an identity matrix based on the specified number
```bash
ey=np.eye(3)
print(ey)
```
### random & randn
 Generates real scoped values up to the specified number > If there is an even number, it produces matirx & random numbers
 ```bash
rndn1=np.random.randn(8)
rndn2=np.random.randn(5,5)
print(rndn2)
```
### randint
randint(start,end,number) produces integer
```bash
rndnt1=np.random.randint(1,10)
rndnt2=np.random.randint(1,20,3)
print(rndnt1)
```
### reshape
Creates matrix from array (row, column)
```bash
matrixs=rndnt2.reshape(3,1)
### print(matrixs)
```
### max & min
```bash
maxx=rndnt2.max()
```
### argmax & argmin
index number of the largest value and index number of the smallest value
```bash
argmaxx=rndnt2.argmax()
argminn=rndnt2.argmin()
print(argminn)
print(argmaxx)
```
### shape
Provides row and column information of the created matrix
```bash
rowAndColumn=matrixs.shape
print(rowAndColumn)
```

##Pandas
```bash
import pandas as pd
matrixnew=np.random.rand(3,4)
dataFrame=pd.DataFrame(matrixnew)
print(dataFrame)
print("\n")
newDataFame=pd.DataFrame(matrixnew,index=["oneR","twoR","treR"],columns=["oneC","twoC","treC","fourC"])
print(newDataFame)
```

### ---> column
```bash
print(newDataFame["oneC"])
print(newDataFame[["oneC","fourC"]])
```

### ---> row
```bash
print("\n")
print(newDataFame.loc["oneR"])
print(newDataFame.iloc[2])
```

### --> Add column
```bash
newList=["rOne","rTwo","rTre"]
newDataFame["New column"]=newList
print(newDataFame)
```
### --> Drop Column
```bash
newDataFame.drop("New column",axis=1,inplace=True)
print(newDataFame)
```

### -->kolonu indexe eşitleme
```bash
newDataFame.set_index("New column",inplace=True)
print(newDataFame) 
```

### --> Multi Index
```bash
oneIndex=["Simpson","Simpson","Simpson","South Park","South Park","South Park"]
inIndex=["Homer","Bart","Marge","Cartman","Kenny","Kyle"]
indeksOne=list(zip(oneIndex,inIndex))
indexOne=pd.MultiIndex.from_tuples(indeksOne)
cizgiList=[[40,"A"],[11,"B"],[32,"C"],[55,"G"],[12,"F"],[11,"E"]]
cizgiNumpy=np.array(cizgiList)
cizdiDataFrame=pd.DataFrame(cizgiNumpy,index=indexOne,columns=["Yas","Meslek"])
cizdiDataFrame.index.names=["Film Adı","İsim"]
print(cizdiDataFrame)

dicValue={"Istanbul":[30,20,np.nan]
          ,"Ankara":[40,np.nan,34]
          ,"Izmir":[35,np.nan,55]
          ,"Balikesir":[20,np.nan,np.nan]}
listIndex=["Pazartesi","Sali","Carsamba"]
DataFrames=pd.DataFrame(dicValue,listIndex)
print(DataFrames)
```
### --> Delete empty data row
```bash
print(DataFrames.dropna(axis=0))
```
### --> Delete empty data col
```bash
print(DataFrames.dropna(axis=1))
```
### -->Delete those with more than 2 empty values (Row and Column)
```bash
### print(DataFrames.dropna(axis=0,thresh=2))
### print(DataFrames.dropna(axis=1,thresh=2))
```
### -->Assigning values to empty data can be either str or int.
```bash
print(DataFrames.fillna("-"))
```

### -->GroupBy
```bash
priceDictionary={"Departman":["Yazılım","Yazılım","Pazarlama","Pazarlama","Hukuk","Hukuk"],
                 "Calisan Ismi":["Ali","Fatma","Fatos","Can","Zeyno","Asik"],
                 "Maas":[100,150,200,300,400,500]}
dictionaryDataFrame=pd.DataFrame(priceDictionary)
groupByObject=dictionaryDataFrame.groupby("Departman")
print(dictionaryDataFrame)

print(groupByObject.count())
```
### --> Max/Min
```bash
print(f"{groupByObject.max()}\n{groupByObject.min()}")
```
### -->Average
```bash
print(f"{groupByObject.mean(1)}")
```
### -->Median
```bash
print(groupByObject.median(1))
```
### -->All description
```bash
print(groupByObject.describe())
```

### Concatenation
DataFrame Merge
```bash
dictionOne={"Isim":["Ahmet","Mehmet","Zeynep","Atil"],
            "Spor":["kosu","yuzme","hentbol","basketbol"],
            "Kalori":[100,200,300,400]}
oneFrame=pd.DataFrame(dictionOne,index=[1,2,3,4])
dictionTwo={"Isim":["Osman","Levent","Atlas","Fatıma"],
            "Spor":["kosu","yuzme","hentbol","basketbol"],
            "Kalori":[150,250,350,450]}
twoFrame=pd.DataFrame(dictionTwo,index=[5,6,7,8])

dictionTre={"Isim":["Ayse","mahmut","Emre","Nur"],
            "Spor":["kosu","yuzme","hentbol","basketbol"],
            "Kalori":[250,350,450,550]}
treFrame=pd.DataFrame(dictionTre,index=[9,10,11,12])
```
### -->Concat
```bash
print(pd.concat([oneFrame,twoFrame,treFrame],axis=0))
```

### Merge
Fusing, Joining related tables
```bash
dictionOne={"Isim":["Ahmet","Mehmet","Zeynep","Atil"],
            "Kalori":[100,200,300,400]}
dictionTwo={"Isim":["Ahmet","Mehmet","Zeynep","Atil"],
            "Spor":["kosu","yuzme","hentbol","basketbol"]}
mergeOneData=pd.DataFrame(dictionOne)
mergeTwoData=pd.DataFrame(dictionTwo)
print(f"{mergeOneData}\n{mergeTwoData}")
```
### -->Merge
```bash
 print(pd.merge(mergeOneData,mergeTwoData,on="Isim"))

priceDictionary={"Departman":["Yazılım","Yazılım","Pazarlama","Pazarlama","Hukuk","Hukuk"],
                 "Calisan Ismi":["Ali","Fatma","Fatos","Can","Zeyno","Asik"],
                 "Maas":[100,150,200,300,400,500]}
dictionaryDataFrame=pd.DataFrame(priceDictionary)
```
### --> Unique
prints repetitive words once
```bash
print(dictionaryDataFrame["Departman"].unique())
```
###  --> NUnique
gives different word count
```bash
print(dictionaryDataFrame["Departman"].nunique())
```
### --> value_counts
Returns the number of repetitions of words
```bash
print(dictionaryDataFrame["Departman"].value_counts())
```
### --> apply
do not act on
```bash
def calculate(maas):
    return maas*0.66
print(dictionaryDataFrame["Maas"].apply(calculate))
```
### --> isnull
empty values are true, filled values are false
```bash
 print(dictionaryDataFrame["Departman"].isnull())
```
###  Pivot_table 
```bash
dicktion={"Karakter Sinifi":["South Park","South Park","South Park","Simpson","Simpson","Simpson"],
          "Karakter Ismi":["catman","kenny","kenny","homer","bart","bart"],
          "Karakter Yas":[9,10,50,20,21,11]}
charterDF=pd.DataFrame(dicktion)
print(charterDF.pivot_table(values="Karakter Yas",index=["Karakter Sinifi","Karakter Ismi"],aggfunc=np.sum))
```

 ## Matplotlib
```bash
import matplotlib.pyplot as plt
import matplotlib
%matplotlib inline

yasListesi=[1,2,3,4,5,6,7,8,9]
kiloListesi=[10,20,30,40,1,60,70,80,90]
npYas=np.array(yasListesi)
npKilo=np.array(kiloListesi)

plt.plot(npYas,npKilo,"r*-")### grafik verisi (x ekseni , y ekseni,renkGösterimTipi)
plt.title("Simple Graphics")### grafik başlığı
plt.xlabel("Yas")###  x eksen başlığı
plt.ylabel("Kilo")### y eksen başlığı

plt.subplot(1,2,1)###  (sıra,kolonSayısı,ÇizilenGrafik)
plt.plot(npYas , npKilo)
plt.subplot(1,2,2)
plt.plot(npKilo, npYas)

figure=plt.figure()
figureAxes=figure.add_axes([0.2,0.2,0.3,0.3]) ### ([xKonum,yKonum,xBoyut,yBoyut])
figureAxes.plot(npYas,npKilo,"y*-")
figureAxes.set_xlabel("x eksen")
figureAxes.set_ylabel("y eksen")
figureAxes.set_title("Başlık")
```

### -->nested chart
```bash
figure=plt.figure()
figureAxes1=figure.add_axes([0.1,0.1,0.8,0.8]) ### ([xKonum,yKonum,xBoyut,yBoyut])
figureAxes2=figure.add_axes([0.3,0.7,0.2,0.2]) ### ([xKonum,yKonum,xBoyut,yBoyut])
figureAxes1.plot(npYas,npKilo)
figureAxes2.plot(npKilo,npYas)

plt.subplot() ###  --> Figure ve eksen getirir (Boş grafik)
plt.figure()### -->Figure getirir eksen veya grafik yok

```
### --> SubPlot
```bash
npArrayOne=np.array(np.linspace(1,100,10))
npArrayTwo=np.array(np.linspace(1,1000,10))

(figureMe, axesMe)=plt.subplots(nrows=1, ncols=2)
axesMe.plot(npArrayOne,npArrayTwo,"r*-")
for exen in axesMe :
   exen.plot(npArrayOne,npArrayTwo,"r*-")
   exen.set_xlabel("X Eksen")
plt.tight_layout()### içe içe geçmeyi önler

```

### --> Add a data header
```bash
newFigure=plt.figure()
newAxes=newFigure.add_axes([0.1,0.1,0.9,0.9])
newAxes.plot(npArrayOne,npArrayTwo**2,label="dizi 1",color="### 001020")### hex coduna göre renk verme
newAxes.plot(npArrayTwo,npArrayOne**4,label="dizi 2",alpha=1,linewidth=2.0)### alpha saydamlık ### -->linewidht = çizgi stili linewidht="[".",":","--","-."] gibi"
newAxes.legend(loc=6)
newFigure.savefig("newFigure",dpi=100) # -->dpi==çözünürlük/Kalite
plt.scatter(npArrayOne, npArrayTwo) # -->Scatter noktalar ile veriyi gösterir
newArrayList=np.random.randint(0,100,50)
plt.hist(newArrayList)
plt.boxplot(newArrayList**2)
``` 




