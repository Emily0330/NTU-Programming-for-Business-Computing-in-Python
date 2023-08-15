### LPT Algorithm (Longest Processing Time first algorithm)
NP-hard problem，最佳解難找，但用此演算法可以找到近似最佳解的解。且在有排序(decreasing)的情況下，此解不會超過最佳解的$\frac{4}{3}$倍；沒排序的情況下，不會超過最佳解的$2$倍。
![](https://hackmd.io/_uploads/SJU6UwIj2.png)

### Inventory Control 存貨控制
因素: 叫貨需要時間、且有成本，不可能一樣一樣叫貨。
* Commom inventory policies
    * the (Q, R) policy
        * R: reorder point
        * 存貨每低於R，就叫Q的量
    * the (s, S) policy
        * s: reorder point
        * 存貨每低於s，補到S
### Travelling Salesman Problem (TSP)
* Dijk's algorithm (a greedy algorithm)

### functions: **ord** and **chr**
* ord告訴你內部編碼，chr告訴你某編碼的對應字元
* 編碼是int形式
![](https://hackmd.io/_uploads/rJWPIkho2.png)
* 中文也可使用
![](https://hackmd.io/_uploads/ByMU6J3o2.png)


### Unicode
能選的話選**UTF-8** (1,2,3 bytes for a char)
vs **UTF-16** (1,2 bytes for a char)
把下面這行放在Python程式碼第一或二行，告訴Python interpreter你要用utf-8編碼

```
# -*-coding: utf8-*-
```
![](https://hackmd.io/_uploads/rJ4l91njn.png)

前面加u是告訴Python這是一個Unicode字串，要用適當的解碼方式轉換成Unicode。但是Python Ver. 3.X之後就不用加了
```
# -*-coding: utf8-*-
msg=u'中文測試'
print(msg) # output: 中文測試
```

### Common String Operations
* str.capitalize() 一句話的第一個字大寫
* str.title() 每個詞的第一個字大寫
![](https://hackmd.io/_uploads/Bkdkygnin.png)
* count operation: 算指定substrings的數量
![](https://hackmd.io/_uploads/ryPY1lhih.png)
* find: 找某substring出現的第一個index
* isnumeric(): check是否「每個字元」都是數字。e.g. "123.4"會得到False
![](https://hackmd.io/_uploads/ByN-exhin.png)
* str.strip(): 沒有傳入參數=>去掉左右兩側的空白；有傳入參數=>去掉字串中有的參數裡的所有字元
![](https://hackmd.io/_uploads/ryylWxhi3.png)

* 正確敘述:
    * 字元的編碼系統為 ASCII 編碼，目前大部分電腦系統使用的編碼系統中的英文字母與ASCII相容 
    * mydict=dict() #This is a constructor
    * 今天有一個dictionary變數**test = {'one': '一', 'two': '二', 'three': '三'}**，如果我print(test)，它的輸出會是：
        * {'one': '一', 'two': '二', 'three': '三'}
### Tuple
* faster than list
* 宣告一個只有一個元素的tuple:
`tup = (11,) #加一個','在元素之後`
* 不能append element，但可以串接另一個tuple(也可以串接一個element的tuple)
![](https://hackmd.io/_uploads/ryhYW_hin.png)

* tuple是immutable，所以不能~~TUPLE.sort()~~，但可以用sorted function (which **returns a list**)
```
mytuple = (3,2,1)
mytuple = sorted(mytuple)
print(mytuple) #output: [1,2,3] #it's a LIST !!
```
* len()/max()/min()/count(某元素)
* list,tuple轉換
![](https://hackmd.io/_uploads/SyfpMu2on.png)

### zip
![](https://hackmd.io/_uploads/B1aE4O2o3.png)

### Lambda
* 定義簡單函式用的
```
funcNAME = lambda parameter_list: expression
```
* alist = map(lambda x: **x%5**, alist) #對alist的每個元素取餘數
![](https://hackmd.io/_uploads/B1IvcO2j3.png)

### map(跟C++的map不一樣!!)
* 見仁見智，有些人覺得這樣做有自己的風格，但其實用迴圈也可以做到
```
map(function, iterable object)
#Apply the function on each element of the iterable object
```
![](https://hackmd.io/_uploads/SkGrn_3s3.png)

* print(out2) 會得到類似"<map object at 0x000001B8FF139750>"的東西，所以把map轉成list後再印出來才是我們要的內容

### dictionary
DICT.items()回傳的順序會依照key建立的順序(for Python ver. 3.6 or later)
![](https://hackmd.io/_uploads/rkSlbK2jn.png)
* output
![](https://hackmd.io/_uploads/SkXbWt3sn.png)
* DICT.get('KEY')
    * key不存在會return None(不會噴錯)，**不會改變**原來的DICT內容
* DICT.setdefault(KEY,defaultValue)
    * 找不到key就回傳defaultValue，並且**將'KEY':defaultValue加到DICT裡面**
* x in DICT
    * x是不是DICT的key
* DICT.keys()/DICT.values()
* ![Uploading file..._ybh98eszh]()

![](https://hackmd.io/_uploads/B1ga77K2i2.png)
output
![](https://hackmd.io/_uploads/HyGQXYhjh.png)
items()可以這樣用
![](https://hackmd.io/_uploads/Skwz4Ynon.png)
sorted(key_list)能將key照字母順序排
![](https://hackmd.io/_uploads/r1CDVthi3.png)

### set
* myset={}
* 印出的順序無法控制
* id(myset)
![](https://hackmd.io/_uploads/rkL7Kohjh.png)
* set.add(ELEM)/.remove(ELEM)
* |&-^
![](https://hackmd.io/_uploads/rJEEqihjn.png)
* operator **in**: set比list快很多，因為set是用hashing的方式來看元素是否在set中，但list是iterate through the whole list
    * note: timeit是用來計算執行時間的module，圖中用的timeit function，第一個參數是你要執行並計時的指令，setup是在執行之前要做什麼(這裡是要declare一個set or list)
    * set(range(500))，代表該set裡面裝0~499
    * 回傳的時間是執行100萬次的時間
![](https://hackmd.io/_uploads/B1R8ijnj3.png)

* "=" for **mutable object**
    * aliasing(別名)
    * 所以list2=list1，他們會指向同一塊記憶體(reference)
    * 若要copy而非aliasing，用 .copy() function
    ```
    aset2 = aset1.copy()
    ```
    * note for list:
        ```
        list2=list1[:] #copy一份，和list1.copy()一樣
        ```
* "=" for **immutable object**
    * 若把一個已知變數assign給另一個新變數，他會是aliasing，但若是assign一個新的值給該新變數，那新變數用的就會是一塊新的memory
    ![](https://hackmd.io/_uploads/Byz8Ci3sn.png)

### Shallow Copy & Deep Copy
* Shallow: 只複製一層
![](https://hackmd.io/_uploads/B1y-1ICj3.png)

* How to use deep copy?
```
import copy
new_dict = copy.deepcopy(old_dict)
```
![](https://hackmd.io/_uploads/S1LHyIAin.png)
![](https://hackmd.io/_uploads/HyphlLCi2.png)

### datetime
* datetime object
    * object's attributes
        * .year/.month/.day/.hour/.minute/.second
    * object's operators
        * "-"(minus): 得出兩datetime objects的差(days + seconds)
        * .total_seconds():上面得到的days也轉成seconds
        * datetime.datetime.strptime(STR, FORMAT_STR)
            * return datetime object
        ![](https://hackmd.io/_uploads/SkjH2Xb3n.png)

![](https://hackmd.io/_uploads/Hke9VI0in.png)
* DATETIME.date().weekday()
    * 0=>Mon, 6=>Sun
* 算從某時間開始，經過一段時間(自訂)，會到何時
![](https://hackmd.io/_uploads/SkxVm8Ai2.png)

* datetime.datetime.strptime(your_str,"FORMAT")
    * p means "parse"
![](https://hackmd.io/_uploads/S1meN80i2.png)

### 檔案處理
* Windows要注意: 檔案路徑要double backslashes
    * (跳脫字元用)
![](https://hackmd.io/_uploads/rJgXdU0j3.png)

* 現在大部分encoding都用'utf-8'；**'cp950' and 'Big5' are for big5**
```
file_var = open(<filename(full path)>, <mode>, encoding = <encoding>)
...
file_var.close() #記得關檔
```

```
FILE.readline() #讀入一行
```
* 用with open就不用關檔了
![](https://hackmd.io/_uploads/HkliEyvCjn.png)

### Try-Except
![](https://hackmd.io/_uploads/Hy-1ZwRoh.png)
* 用途:
![](https://hackmd.io/_uploads/ryZGZD0j3.png)

* **自己丟Exception!**

![](https://hackmd.io/_uploads/HJlyfv0jn.png)

## 股票
* 初級市場 VS 次級市場
    * 初級市場: 公司上市，首次發行股票
    * 次級市場: 發行之後的買賣皆屬次級市場
* Capital Asset Pricing Model (CAPM)
    * ![](https://hackmd.io/_uploads/ryyEjdRi2.png)
    * alpha是當市場報酬為0時，該個股的報酬率。若alpha>0，代表大盤就算不漲，個股也會漲
    * beta(系統風險)若為正，表個股報酬率跟市場報酬率走勢相同(一起漲跌)，(當市場上升(下降)一單位時，個股會上升(下降)多少)
        * ![](https://hackmd.io/_uploads/BkGG2uCsh.png)

### CSV files processing
```
import csv
# delimiter: 分隔字元；\t 是tab
# Looping over reader gives you each row.
csv_reader = csv.reader(FILE, delimiter = '\t')
```
* **開csv檔案時open()裡記得加一個參數newline=''**
    * 詳情請見csv documentation
* next(CSV_Reader)函數讀入下一行資料(會將內容拆成a list of strings)
![](https://hackmd.io/_uploads/Hy_HejJn2.png)

* Notice:
    * Looping over ```reader``` gives you each row.
    * WRITER = csv.writer(FILE)
    * WRITER.writerow(ROW)
        * 似乎會自己幫你用','分隔
    * ~~例子中~~用csv.DictReader讀的話，`arow`變數是可以用column name去取值的 ~~(試不出來??)~~，也不用處理header(自動變成dictionary的key)
![](https://hackmd.io/_uploads/SJRnIi133.png)

* csv sorter
    * ```pip install csvsorter```
    * 先做切割，各自排序，再組合 => 因此可處理大檔案
    * 但會需要暫存檔案，會存在current working directory，但是current working directory可能會沒有寫檔案的權利，因此要作適當處理。
        ```
        import os
        os.getcwd() # get current working directory
        ```
        ```
        wd = "電腦上可以讀寫的位置"
        os.chdir(wd) # change current working directory
        ```
* Notice:
    * 要開你要讀的檔案&寫入的檔案
    * csvsorter.csvsort()
        * [0,2]表示先照col 0排序，再照col 2排序
        * has_header = True 表示有header，第一行不要排
    * 檔案不是很大的話可直接用Excel來處理
![](https://hackmd.io/_uploads/SJtv2sy32.png)

### Simple Regression
* 求未知數的公式
    * $0<= R^2 <= 1$: $R$是相關係數
![](https://hackmd.io/_uploads/rJM5WTk2n.png)

### Plotting
![](https://hackmd.io/_uploads/r1yZPRk2n.png)

![](https://hackmd.io/_uploads/HJDzvC132.png)

## Class
* 一般的型別(ex. int, string,...)的變數叫variables, class的變數(variable)特別叫object
* Define a class & Declare an object
    ```
    class Date:
        pass #pass is a key word in Python, meaning doing nothing
    d = Date() # declare an object
    d.day = 9 # create an instance attribute
    ```
* instance var & static var
    * 如果同個class的所有objects該屬性要一樣 => static variables
![](https://hackmd.io/_uploads/HymmkCx33.png)
    * static variable(ex. `doubleDigit`)要用CLASS.VAR取值；instance variable(ex. `year,month,day`)要用SELF.VAR取值
![](https://hackmd.io/_uploads/S1rj1Cl3n.png)



* 同一個class的object可以有不同members，但最好不要這樣，unless you know what you are doing

* instance function (寫在class裡的operations，但屬於個別object，每個object呼叫的結果不盡相同)
    * 第一個傳入的parameter一定要是自己(即例子中的```self```(變數名可自取)，the invoking object itself)
    * 但是實際上在呼叫時是```OBJ.functionName() # Python會自己把invoking object算是第一個參數```
* static function
    * 只能存取static variable
    * 需要加`@staticmethod`這個decorator，且最好要用CLASS呼叫(用OBJ呼叫雖然可行，因為他能存取static variable，但容易讓其他人誤會)，其他就幾乎一樣
![](https://hackmd.io/_uploads/SyJjm0gn3.png)

![](https://hackmd.io/_uploads/B1vHz6lhh.png)
* constructor```__init__```
    * In Python, the constructor must be called ```__init__```，and it's automatically invoked when the object is declared.
    * 我們沒寫的話，系統會自動幫我們生出一個constructor，裡面什麼都不做
     
     ```
     def __init__(self, other_paras_you_need):
        #TODO
     ```
![](https://hackmd.io/_uploads/rkK4u6lhn.png)

* special function `__str__` to be defined in a class
    * 如果 `__str__`有return一個字串，那麼`print(OBJ)`時就不會印出OBJ存在的記憶體位置，而是印出該字串
![](https://hackmd.io/_uploads/r15yp6g2h.png)

### matplotlib
![](https://hackmd.io/_uploads/rJvbG4Z33.png)
* matplotlib.pyplot.hist(...)其實是有回傳值的!(所以matplotlib不一定要畫圖，有統計效果)
    * 如圖，`n`是每個bins(classes)內的frequency，`bins`是每個bins的endpoints
![](https://hackmd.io/_uploads/HJXEE4bn2.png)

* histogram vs bar chart
    * histogram(直方圖): continuous data
    * bar chart(長條圖): discrete data
* pie chart
![](https://hackmd.io/_uploads/HkK1EJ732.png)

![](https://hackmd.io/_uploads/Byg07yX32.png)


* line chart
![](https://hackmd.io/_uploads/rJVGL1Q23.png)

## game theory

* prisoners' dilemma
    * 合作能improve情況
    * Confession 是dominant strategy(不管對方做什麼決定，自己都是選擇confess較好)
![](https://hackmd.io/_uploads/HJ5P3lQhn.png)

* 不是每個game都有dominant strategy => new solution concept: **equilibrium**
* 沙灘賣冰
    * 兩個攤販都在0.5雖然不是唯一均分市場的解，卻是唯一讓兩攤販不會unilaterally deviate(在對方不移動的情況下，自己移動)的解
    * =>達到均衡
> In a (Nash) equilibrium, no player wants to deviate while others do not.

![](https://hackmd.io/_uploads/HkH2RgQn2.png)

## tkinter

![](https://hackmd.io/_uploads/ByKlav_n3.png)

* mainloop(): keep listening to event

![](https://hackmd.io/_uploads/H1hxk_u23.png)

![](https://hackmd.io/_uploads/By44GO_33.png)

* event listener
`command = self.clickBtnNum1`是參數，傳入一個function當參數!!(此function是一個event listener)
* `lblNum`是我們自己取的Calculator Class裡面的(Frame的Label object)Label屬性(object?)的名稱
* LABEL.configure(...) #有很多東西可以改，ex.顏色
* LABEL.cget("屬性名稱"): 會得到該Lable該屬性的內容
![](https://hackmd.io/_uploads/Hk8VEdOh2.png)

* tkinter library裡有個class叫font
    * `import tkinter.font as tkFont`
    * `f1` and `f2` are font objects
![](https://hackmd.io/_uploads/ryVUDdO33.png)

* 排數字
    * `columnspan`屬性

![](https://hackmd.io/_uploads/r1lk5_dhh.png)

* 把margins填滿
    * 屬性`sticky`:
        * 代表要靠哪個方位
        * `tk.NE+tk.SW`代表要把東北和西南填滿 => 整個框框填滿，no margins

![](https://hackmd.io/_uploads/Hkkbod_h2.png)

* textbox
    * 加上讓使用者可以用打字的功能
    * `.cget(屬性)`改成`.get(...)`(如下圖2)，參數"1.0",tk.END是指定開頭跟結尾
        * 1.0： the first line, 0th character
        * tk.END： until the last character
![](https://hackmd.io/_uploads/HJUcWFOnn.png)
![](https://hackmd.io/_uploads/rJZ6-t_n3.png)

* create a font object `f`給大家用
* `btnLoad`是按下就會畫出圖的按鈕
* `tk.Canvas(...)`: create a canvas object (canvas是一個class)
![](https://hackmd.io/_uploads/ry_5J9O2h.png)
![](https://hackmd.io/_uploads/Hyyaeqd33.png)

* `import os`把產生出來的png檔刪掉，以免硬碟都是垃圾
![](https://hackmd.io/_uploads/rkhSB9u23.png)































