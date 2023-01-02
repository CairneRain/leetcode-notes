# Java刷题

---

## ACM输入输出

### 数字

- 多组输入， 0 0则结束输入

```java
import java.util.Scanner;
Scanner in = new Scanner(System.in);
while(in.hasNextInt()){
    int a = in.nextInt();
    int b = in.nextInt();
    System.out.println(a);
    System.out.println(b);
    if(a ==0 && b == 0) break;
}
```

- 第一行输入数据个数，后面输入数据

```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int num = in.nextInt();
        for(int i = 0; i < num; i++) { 
            int a = in.nextInt();
            int b = in.nextInt();
            //处理
        }
    }
}
```

### 字符串

next(), nextLine()

```java
Scanner in = new Scanner(System.in);
String n = in.nextLine();//读取到回车
String n = in.next();//读取到空白符前，不会吞掉空格，但前面有空白符会忽略
```

- 第一行个数 第二行字符串

```java
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = in.nextInt();
        in.nextLine();
        while (in.hasNext()) { 
            String[] s = in.nextLine().split(" ");
        }
    }
}

```

### 格式化

```java
String str=String.format("%.2f",3.555)
```

### 排序

```java
int[][] nums=new int[n][2];
//从小到大排序
Arrays.sort(nums, (a, b) -> a[1] - b[1]);
//从小到大排序
Arrays.sort(a, Collections.reverseOrder());
```

https://blog.csdn.net/yjlhz/article/details/115586630

### 常量

```java
Integer.MAX_VALUE;
Integer.MIN_VALUE;
```



----

## 常用数据结构

```java
//数组
int[] result = new int[10];
result.length;
Arrays.fill(result,1);
Arrays.equals(arr1,arr2);
Arrays.toString(result);

//Collection 数组
List<Integer> list[] = new ArrayList[len];
```

```java
//stack
Deque<Integer> stack = new ArrayDeque<Integer>();
stack.push(123);
stack.pop();
stack.offer(123);
stack.poll();
stack.peek();
stack.isEmpty();

//double-ended queue(deque)
Deque<Integer> deque = new ArrayQueue<Integer>();
deque.add(11);//队头
deque.addLast(11);//队尾
deque.peek();//看队头
deque.peekLast();//看队尾
deque.remove();//移除队头
deque.removeLast();//移除队尾
deque.push();// == deque.addFirst();
deque.pop();// == deque.removeFirst();

//queue
Queue<int[]> queue = new LinkedList<>();
queue.offer(new int[]{0,0});
queue.poll();
queue.isEmpty();

//PriorityQueue, 默认是natural ordering
Queue<String> queue= new PriorityQueue<>();
queue.offer("apple");
queue.poll(); //返回优先级最高的

//List
List<Integer> list = new ArrayList<Integer>();
List<Integer> list = new LinkedList<Integer>();
list.add(1,value);
list.remove(1,value);
list.get(1);
list.size();
list.toArray(new int[arr.size()][]);//转为int[][]

//Map
Map<String, Integer> map=new HashMap<>();
map.put("123",123);
map.get("123");
map.getOrDefault("test",0);//如果没有“test” 则获取默认值（0）
map.equals(map2);//比较是否相同

//set
Set<String> set = new HashSet<>();//无序
Set<String> set = new TreeSet<>();//有序
set.add("apple");
```

```java
Collection.sort(list);
```

```java
//遍历
for(Iterator<String> it = list.iterator(); it.hashNext();){
    String s = it.next();
}
for (Map.Entry<String, String> entry : map.entrySet()) {
    String mapKey = entry.getKey();
    String mapValue = entry.getValue();
    System.out.println(mapKey + "：" + mapValue);
}
for(String s : list){
    System.out.println(s);
}
```

```java
//String
String s="";
s.substring(n,s.length());
s.trim()
```

### 工具类

```java
Arrays.sort(nums);//排序
Arrays.equals(nums1,nums2);//一一比较
```

### 根据map的value给key排序

```java
List<Character> list = new ArrayList<Character>(map.keySet());
Collections.sort(list, (a, b) -> map.get(b) - map.get(a));//降序
```

### Comparator

```java
Queue<Integer> pq = new PrioriotyQueue<>(Comparator.naturalOrder());//自然排序，升序
Queue<Integer> pq = new PrioriotyQueue<>((a,b) -> a-b);//升序
Queue<Integer> pq = new PrioriotyQueue<>(Comparator.reverseOrder());//反转，降序
Queue<Integer> pq = new PrioriotyQueue<>((a,b) -> b-a);//降序
```

-----

## Algorithm

### 冒泡排序

> 两轮循环，每次会把一个最大的放在最右边

```java
public class BubbleSort {
     public static void main(String[] args) {
         int[] arrays =new int[]{15,63,97,12,235,66};
         for (int i=0;i<arrays.length-1;i++){
             for(int j=0;j<arrays.length-1-i;j++){
                 //前面的比后面的大，就交换
                 if (arrays[j] > arrays[j+1]){
                    int temp = 0;
                   	temp = arrays[j];
                    arrays[j] = arrays[j+1];
                    arrays[j+1] = temp;
                }
            }
        }
        System.out.println(Arrays.toString(arrays));
     }
}
```

### 快速排序

> 用两个指针，两端扫描，一个大一个小的交换。让一个基准数到达它的位置。
>
> 最后递归左右两端
>
> https://blog.csdn.net/shujuelin/article/details/82423852

```java
public class QuickSort {
    public static void quickSort(int[] arr,int low,int high){
        int i,j,temp,t;
        if(low>high){
            return;
        }
        i=low;
        j=high;
        //temp就是基准位
        temp = arr[low];
        while (i<j) {
            //先看右边，依次往左递减
            while (temp<=arr[j]&&i<j) {
                j--;
            }
            //再看左边，依次往右递增
            while (temp>=arr[i]&&i<j) {
                i++;
            }
            //如果满足条件则交换
            if (i<j) {
                t = arr[j];
                arr[j] = arr[i];
                arr[i] = t;
            }
        }
        //最后将基准为与i和j相等位置的数字交换
         arr[low] = arr[i];
         arr[i] = temp;
        //递归调用左半数组
        quickSort(arr, low, j-1);
        //递归调用右半数组
        quickSort(arr, j+1, high);
    }
    public static void main(String[] args){
        int[] arr = {10,7,2,4,7,62,3,4,2,1,8,9,19};
        quickSort(arr, 0, arr.length-1);
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

### 插入排序

> 从1到n依次往回判断是否小于前面全部的元素，小于则交换

```java
public class InsertSort {
    public static void main(String[] args) {
         int[] array = new int[]{15,63,97,12,235,66};
         for(int i=1; i<array.length; i++){
             //从当前位置从前往后扫描
             for (int j=i; j>=1; j--){
                 //是否小于前面的元素
                 if (array[j] < array[j-1]){
                    int temp = 0;
                    temp = array[j];
                    array[j] = array[j-1];
                    array[j-1] = temp;
                 }
                 else {
                    break;
                 }
            }
        }
        System.out.println("排序后的结果："+ Arrays.toString(array));
    }
}
```

### 归并排序

```java
static void merge_sort(int[] arr, int[] result, int start, int end) {
    if (start >= end)
        return;
    int mid = (end + start) / 2;
    int start1 = start, end1 = mid;
    int start2 = mid + 1, end2 = end;
    merge_sort(arr, result, start1, end1);
    merge_sort(arr, result, start2, end2);
    int k = start;
    while (start1 <= end1 && start2 <= end2)
        result[k++] = arr[start1] < arr[start2] ? arr[start1++] : arr[start2++];
    while (start1 <= end1)
        result[k++] = arr[start1++];
    while (start2 <= end2)
        result[k++] = arr[start2++];
    for (k = start; k <= end; k++)
        arr[k] = result[k];
}

public static void merge_sort(int[] arr) {
    int len = arr.length;
    int[] result = new int[len];
    merge_sort(arr, result, 0, len - 1);
}
```

```java
//链表版
static void merge_sort(Node n){
    if(n!=null&&n.next!=null){
        //快慢指针找中间
        Node fast=n.next;
        Node slow=n;
        while(fast!=null&&fast.next!=null){
            fast=fast.next.next;
            slow=slow.next;
        }
        Node p1=merge_sort(slow);
        slow.next=null;//important
        Node p2=merge_sort(node);
        //sort
        Node head=new Node();
        Node current=head;
        while(p1!=null&&p2!=null){
            if(p1.val<p2.val){
                current.next=p1;
                p1=p1.next;
            }
            else{
                current.next=p2;
                p2=p2.next;
            }
            current=current.next;
        }
        if(p1!=null){
            current.next=p1;
        }
        if(p2!=null){
            current.next=p2;
        }
        return head.n
    }
}
```

### HeapSort

```java

```

### 二分查找

```java
public static int recursionBinarySearch(int[] arr,int key,int low,int high){
		
		if(key < arr[low] || key > arr[high] || low > high){
			return -1;
		}
		
		int middle = (low + high) / 2;			//初始中间位置
		if(arr[middle] > key){
			//比关键字大则关键字在左区域
			return recursionBinarySearch(arr, key, low, middle - 1);
		}else if(arr[middle] < key){
			//比关键字小则关键字在右区域
			return recursionBinarySearch(arr, key, middle + 1, high);
		}else {
			return middle;
		}
}
```

## 算法模板

### DSU

### Floyd's Cycle-Finding Algorithm 

- slow and fast pointer

### Backtracking

### Double Pointer

### DFS

- 可以先forloop，在forloop中dfs

### BFS

- 在while(!queue.isEmpty())中forloop queue.size()

### Divide and Conquer

### monotonic stack

### Graph 拓扑排序（判断图是否有环）

- DFS(依次遍历所有node，记录状态为0 未搜索，1搜索中，2搜索完成，对于遍历中出现1的，则有环)
- BFS(预先保存所有的node的in-degree, 把in-degree为0的放入queue，遍历queue中的所有元素，同时对queue中元素所包含的元素的in-degree --, 最后判断是否遍历所有节点，如果没有全部遍历，则有环)

## Math

### Prime

- [Sieve of Eratosthenes](https://leetcode.com/problems/count-primes/solutions/2805950/java-simple-solution/)
