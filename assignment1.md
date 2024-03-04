# Assignment #1: 拉齐大家Python水平

Updated 0940 GMT+8 Feb 19, 2024

2023 fall, Complied by 姚哲恒 生命科学学院==同学的姓名、院系==



**说明：**

1）数算课程的先修课是计概，由于计概学习中可能使用了不同的编程语言，而数算课程要求Python语言，因此第一周作业练习Python编程。如果有同学坚持使用C/C++，也可以，但是建议也要会Python语言。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

==（请改为同学的操作系统、编程环境等）==

操作系统：Windows11

Python编程环境：VS Code

## 1. 题目

### 20742: 泰波拿契數

http://cs101.openjudge.cn/practice/20742/



思路：



##### 代码

```python
a=0
b=1
c=1
n=int(input())
if n>2:
    for i in range(2,n):
        d=a+b+c
        a,b,c=b,c,d
    print(c)
elif n==0:
    print(0)
elif n==1:
    print(1)
elif n==2:
    print(1)

```



代码运行截图 ==（至少包含有"Accepted"）==

![屏幕截图 2024-02-19 105820](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-02-19 105820.png)



### 58A. Chat room

greedy/strings, 1000, http://codeforces.com/problemset/problem/58/A



思路：



##### 代码

```python
s=input()
e=1
if 'h'in s and'e'in s and'l'in s and 'o'in s:
        a=s.find('h')
        b=s[a:].find('e')+a
        c=s[b:].find('l')+b
        l=s[c+1:].find('l')+c+1
        d=s[l+1:].find('o')+l+1
        if a<b<c<l<d:
            print('YES')
            e=0
        else:
            e=1      
else:
        e=1
if e==1:
    print('NO')

```



代码运行截图 ==（至少包含有"Accepted"）==

![屏幕截图 2024-02-20 152243](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-02-20 152243.png)



### 118A. String Task

implementation/strings, 1000, http://codeforces.com/problemset/problem/118/A



思路：



##### 代码

```python
string=input().lower()
ans=''
for i in string:
    if i not in "aeiouy":
        ans+='.'+i
print(ans)

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==



![屏幕截图 2024-02-20 153111](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-02-20 153111.png)

### 22359: Goldbach Conjecture

http://cs101.openjudge.cn/practice/22359/



思路：



##### 代码

```python
x=int(input())  			          
numbers=[True]*(x + 1)		 
numbers[0]=numbers[1]=False			
for i in range(2,int(x**0.5)+1)	:				
        if numbers[i]:							
            j=i*i										
            while j <= x:								 			
                numbers[j]=False
                j+=i   
for i in range(1,x+1):
    if numbers[i]:
         if numbers[x-i]:
            print(i,x-i)
            break  

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![屏幕截图 2024-02-19 111121](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-02-19 111121.png)



### 23563: 多项式时间复杂度

http://cs101.openjudge.cn/practice/23563/



思路：



##### 代码

```python
a=(input().split('+'))
ku=[]
b=list(i.split('^') for i in a)
for j in b:
    if j[0][0]!='0':
        ku.append(int(j[-1]))
print('n^'+str(max(ku)))

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![屏幕截图 2024-02-19 112332](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-02-19 112332.png)



### 24684: 直播计票

http://cs101.openjudge.cn/practice/24684/



思路：



##### 代码

```python
ku=[0]*100001
ans=[]
lln=input().split()
a=[int(i) for i in lln]
for i in a:
    ku[i]+=1
c=max(ku)
for i in range(1,max(a)+1):
    if ku[i]==c:
      ans.append(i)
print(*sorted(ans))

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![屏幕截图 2024-02-19 113602](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-02-19 113602.png)



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“数算pre每日选做”、CF、LeetCode、洛谷等网站题目。==

作业和目前的每日选做还是很简单的，所以自己也做了一些OJ“数算pre每日选做”的题（上个学期计概最后只有ac3，非常不理想，希望这学期的数算能取得一个满意的成绩！

下面是每日选做的收获：

**OJ05467：多项式加法**

```python
from collections import defaultdict
def readin(x):
    data=[]
    for j in range(1,len(x)-1,2):
        data.append((int(x[j-1]),int(x[j])))
    return data
n=int(input())
for i in range(n):
    ans=defaultdict(int)
    a=input().split()
    b=input().split()
    dataa=readin(a)
    datab=readin(b)
    for k in dataa:
        ans[k[1]]+=k[0]
    for k in datab:
        ans[k[1]]+=k[0]
    for i in sorted(ans,reverse=True):
        if ans[i]!=0:
            print(f'[ {ans[i]} {i} ] ',end='')
    print()
```

收获：1.用 ans=defaultdict(int)创建一个未知容量的dict，且未经操作时数据值均为0

​	   2.print(f'[ {ans[i]} {i} ] ',end='')end默认是换行，这里end=‘ ’，即把换行替换成了‘ ’ 要实现分行输出就需要在末尾加上print（）

**OJ******27653:Fraction类******

```python
##老老实实写Fraction
def gcd(m,n): 
        while m%n != 0: 
            oldm = m 
            oldn = n 

            m = oldn 
            n = oldm % oldn 
        return n
class Fraction:
    def __init__(self,top,bottom):
        self.num=top
        self.den=bottom

    def __str__(self): 
        return str(self.num) + "/" + str(self.den) 

    def show(self): 
        print(self.num, "/", self.den) 

    def __add__(self, otherfraction): 
        newnum = self.num * otherfraction.den+self.den * otherfraction.num 
        newden = self.den * otherfraction.den 
        common = gcd(newnum,newden) 
        return Fraction(newnum//common, newden//common) 


a,b,c,d=input().split()
a,b,c,d=int(a),int(b),int(c),int(d)
f1=Fraction(a,b)
f2=Fraction(c,d)
print(f1.__add__(f2))


# def __eq__(self, other): 
#     firstnum = self.num * other.den 
#     secondnum = other.num * self.den 
#     return firstnum == secondnum
#该函数用于Fraction类中两数是否相等的快速判断

##这题简单其实直接用一个gcd就可以，不需要用Fraction，代码如下：
def gcd(m,n): 
        while m%n != 0: 
            oldm = m 
            oldn = n 
            m = oldn 
            n = oldm % oldn 
        return n
   		####后来才知道，math库里有gcd函数，所以又简化了代码
a,b,c,d=input().split()
a,b,c,d=int(a),int(b),int(c),int(d)

e,f=a*d+b*c,b*d
n=gcd(e,f)

print(str(e//n)+'/'+str(f//n))
```

收获：1.首先知道了gcd函数（即欧几里得算法寻找最大公因数

​	   2.Fraction类中想要输出结果就得重新定义一个show和str，否则会无法响应print或者报错

​	   3.在Fraction对象相加时应该自己定义函数____add____

​		

另外就是复习了上学期的一些dp题目，比如采药、幸福的寒假生活。之前其实没有很好的理解掌握dp，现在再去重新学一遍，感觉理解比之前顺畅一些，希望能有更大的进步吧。
