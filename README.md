# -冒泡排序
比较类排序，算法描述：
* 比较相邻的两个元素，如果前面的比后面的值要大，就把他们互换位置；
* 对每一对相邻的元素做这样的事情，从头到尾，最后最后面的值应该是最大的；
* 针对未排序的区域（前面没有选好的元素）重复以上操作；
* 直到排序完成。

 算法复杂度 ： O（n²）
 
``` python
 '''冒泡排序'''
 def BubbleSort(array):
    length = len(array)
    for i in range(length):
        if array[j] > array[j+1]:
            array[j+1], array[j] = array[j], array[j+1]
	return array	
 ```
 
 # -选择排序
 比较类排序，算法描述：
 * 第一步，在未排序的序列中找到最小的元素，放置已排序序列的末尾；
 * 第二步，再从未排序的序列中继续寻找最小的元素，放置已排序序列的末尾；
 * 重复第二步，直到所有元素排序完成。
 
 算法复杂度：  O(n²)
 
```python
'''选择排序'''
def selection_sort(arr):
    """选择排序"""
    # 第一层for表示循环选择的遍数
    for i in range(len(arr) - 1):
        # 将起始元素设为最小元素
        min_index = i
        # 第二层for表示最小元素和后面的元素逐个比较
        for j in range(i + 1, len(arr)):
            if arr[j] < arr[min_index]:
                # 如果当前元素比最小元素小，则把当前元素角标记为最小元素角标
                min_index = j
        # 查找一遍后将最小元素与起始元素互换
        arr[min_index], arr[i] = arr[i], arr[min_index]
    return arr
```

# -插入排序
比较类算法，算法描述：
* 选取未排序的元素，插入到已排序区间的合适位置，直到未排序区间为空

算法复杂度为O（n²）
```python
'''插入排序'''
def InsertSort(myList):
    #获取列表长度
    length = len(myList)
    for i in range(1,length):
        #设置当前值前一个元素的标识
        j = i - 1
        #如果当前值小于前一个元素,则将当前值作为一个临时变量存储,将前一个元素后移一位
        if(myList[i] < myList[j]):
            temp = myList[i]
            myList[i] = myList[j]
            #继续往前寻找,如果有比临时变量大的数字,则后移一位,直到找到比临时变量小的元素或者达到列表第一个元素
            j = j-1
            while j>=0 and myList[j] > temp:
                myList[j+1] = myList[j]
                j = j-1
            #将临时变量赋值给合适位置
            myList[j+1] = temp
```

# -归并排序
采用分治法，算法描述：
* 将数组不断二分，直到最后每个部分都只包含一个数据
* 然后对每个数据分别进行排序
* 最后将排序好的相邻的两部分合并在一起，如此整个数组就是有序了

算法复杂度为O（nlongn）
```python
'''归并排序'''
def merge(a, b):
    c = []
    h = j = 0
    while j < len(a) and h < len(b):
        if a[j] < b[h]:
            c.append(a[j])
            j += 1
        else:
            c.append(b[h])
            h += 1
    if j == len(a):
        for i in b[h:]:
            c.append(i)
    else:
        for i in a[j:]:
            c.append(i)
    return c
def merge_sort(lists):
    if len(lists) <= 1:
        return lists
    middle = len(lists)//2
    left = merge_sort(lists[:middle])
    right = merge_sort(lists[middle:])
    return merge(left, right)
```

# -快速排序
采用分治法，算法描述为：
* 每轮迭代会选取数组中的任意一个数据作为基准（pivot），将小于它的元素放在它的左边，将大于他的元素放在它的右边
* 再利用分治思想，继续对两侧进行同样的操作，直至每个区间缩小为1，完成排序

算法复杂度为O（nlongn）
```python
'''快速排序'''
def partition(arr,low,high): 
    i = ( low-1 )         # 最小元素索引
    pivot = arr[high]     
    for j in range(low , high): 
        # 当前元素小于或等于 pivot 
        if   arr[j] <= pivot: 
            i = i+1 
            arr[i],arr[j] = arr[j],arr[i] 
    arr[i+1],arr[high] = arr[high],arr[i+1] 
    return ( i+1 ) 
# arr[] --> 排序数组
# low  --> 起始索引
# high  --> 结束索引
# 快速排序函数
def quickSort(arr,low,high): 
    if low < high: 
        pi = partition(arr,low,high) 
        quickSort(arr, low, pi-1) 
        quickSort(arr, pi+1, high) 
```
