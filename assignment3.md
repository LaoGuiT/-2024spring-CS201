# Assignment #3: March月考

Updated 1537 GMT+8 March 6, 2024

2024 spring, Complied by 姚哲恒 生命科学学院==同学的姓名、院系==



**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:
- Learn about Time and Space complexities
- Learn the basics of individual Data Structures
- Learn the basics of Algorithms
- Practice Problems on DSA

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

==（请改为同学的操作系统、编程环境等）==

操作系统：macOS Ventura 13.4.1 (c)

Python编程环境：Spyder IDE 5.2.2, PyCharm 2023.1.4 (Professional Edition)

C/C++编程环境：Mac terminal vi (version 9.0.1424), g++/gcc (Apple clang version 14.0.3, clang-1403.0.22.14.1)



## 1. 题目

**02945: 拦截导弹**

http://cs101.openjudge.cn/practice/02945/



思路：



##### 代码

```python
k=int(input())
if k==0:
    print(0)
else:
    daodan=list(map(int,input().split()))
    ku=[0]*k
    ku[0]=1
    for i in range(1,k):
        a=[]
        for j in range(0,i):
            if daodan[j]>=daodan[i]:
                a.append(ku[j])
        if a:
            ku[i]=1+max(a)
        else:
            ku[i]=1
    print(max(ku))
```



代码运行截图 ==（至少包含有"Accepted"）==

![屏幕截图 2024-03-06 202044](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-03-06 202044.png)



**04147:汉诺塔问题(Tower of Hanoi)**

http://cs101.openjudge.cn/practice/04147



思路：![屏幕截图 2024-03-06 203004](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-03-06 203004.png)



##### 代码

```python
def hanoi(n, source, auxiliary, target):
    if n > 0:
        hanoi(n - 1, source, target, auxiliary)

        print(f'{n}:{source}->{target}')

        hanoi(n - 1, auxiliary,source,target )
n,a,b,c=input().split()
n=int(n)
hanoi(n,a,b,c)

```



代码运行截图 ==（至少包含有"Accepted"）==





**03253: 约瑟夫问题No.2**

http://cs101.openjudge.cn/practice/03253



思路：



##### 代码

```python
while True:    
        n,p,k=map(int,input().split())
        if (n,p,k)==(0,0,0):
            False
            break
        else:
            pp=[i for i in range(1,n+1)]
            dead=[]
            d=p-1
            while len(pp)!=0:
                d=(k-1+d)%(len(pp))
                dead.append(pp[d])
                del pp[d]
            print(','.join(map(str,dead)))

```



代码运行截![屏幕截图 2024-03-06 203051](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-03-06 203051.png)图 ==（AC代码截图，至少包含有"Accepted")==





**21554:排队做实验 (greedy)v0.2**

http://cs101.openjudge.cn/practice/21554



思路：



##### 代码

```python
n=int(input())
a=list(map(int,input().split()))
b=[]
t=1
for i in a:
    b.append((i,t))
    t+=1
b.sort()
a.sort()
c=[]
k=0
for i in range(1,n):
    k+=sum(a[0:i])
for i in range(n):
    c.append(b[i][1])
k=k/n
print(*c)
print('%.2f'% k)

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![屏幕截图 2024-03-06 202840](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-03-06 202840.png)



**19963:买学区房**

http://cs101.openjudge.cn/practice/19963



思路：



##### 代码

```python
n=int(input())
pairs = [i[1:-1] for i in input().split()]
distance1 = [ sum(map(int,i.split(','))) for i in pairs]
price1=list(map(int,input().split()))
for i in range(n):
    distance1[i]=distance1[i]/price1[i]
distance2=sorted(distance1)
price2=sorted(price1)
if n%2!=0:
    midd=distance2[int((n-1)//2)]
    middp=price2[int((n-1)//2)]
else:
    midd=(distance2[int(n//2)-1]+distance2[int(n//2)])/2
    middp=(price2[int(n//2)-1]+price2[int(n//2)])/2
count=0
for i in range(n):
    if price1[i]<middp and distance1[i]>midd:
        count+=1
print(count)# 

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==



![屏幕截图 2024-03-06 202848](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-03-06 202848.png)

**27300: 模型整理**

http://cs101.openjudge.cn/practice/27300



思路：



##### 代码

```python
from collections import defaultdict
n=int(input())
ku=defaultdict(list)
a=defaultdict()
a['B']=1000
a['M']=1
ans1=[]
def exchange(b):
    num=float(b[0:len(b)-1])*a[b[-1]]
    return num
for i in range(n):
    h,b=input().split('-')
    ku[h].append((b,exchange(b)))
for key in ku:
    ans1.append(key)
ans1.sort()
for key in ans1:
    kk=list((x,y) for (x,y) in ku[key])
    kk.sort(key=lambda y:y[1])
    ans=list(x for (x,y) in kk)
    print(f'{str(key)}: '+', '.join(ans))

```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![屏幕截图 2024-03-06 202904](C:\Users\legion\Pictures\Screenshots\屏幕截图 2024-03-06 202904.png)



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“2024spring每日选做”、CF、LeetCode、洛谷等网站题目。==

因为在做定量分析化学实验，月考没有能够去机房参加，晚上抽了两个小时AC6，基本上是卡点写完，但是能AC6还是很高兴的！（虽然有点慢。不过值得深思的是，闫老师标注E的两题反而是我花的时间最长的，感觉递归还是有些欠缺，特别是汉诺塔那题，知道要写递归，但是有点无从下手，要在这方面继续加强。



```python
Sample Input:
(100,200) (50,50) (100,300) (150,50) (50,50)

#巧妙得读取数字，并组内加和
pairs = [i[1:-1] for i in input().split()]
distances = [ sum(map(int,i.split(','))) for i in pairs]
```





```python
#补一个进制转换
dec_num = 10  # 十进制数
bin_num = bin(dec_num)[2:]  # 转换为二进制，并去掉前缀'0b'
print(bin_num)  # 输出结果为：1010
oct_num = oct(dec_num)[2:]  # 转换为八进制，并去掉前缀'0o'
print(oct_num)  # 输出结果为：12
hex_num = hex(dec_num)[2:]  # 转换为十六进制，并去掉前缀'0x'
print(hex_num)  # 输出结果为：a

bin_str = "num" //  # n进制字符串
dec_num = int(bin_str, n)  # 转换为十进制
print(dec_num)  # 输出结果为：十进制数
```

