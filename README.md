# BinaySearch
BinaySearch with Striver
---
- A Searching Algo
- Ex. Search page in book , search word in dict

> ## Iterative code 
![](./img/binSearch.png)

```cpp
int search(vector<int> &nums, int key)
{
    int s = 0, e = nums.size() - 1, m;
    while (s <= e)
    {
        m = s + (e - s) / 2;
        if (nums[m] == key) return m;
        else if (nums[m] > key) e = m - 1;
        else  s = m + 1;
    }
    return -1;
}
```
> ## Recursion Code
```cpp
int bs(int s, int e, vector<int> &nums, int key)
{
    if (s > e)
        return -1;
    int m = s + (e - s) / 2;
    if (nums[m] == key)
        return m;
    else if (nums[m] > key)
        return bs(s, m - 1, nums, key);
    else
        return bs(m + 1, e, nums, key);
}
int search(vector<int> &nums, int key)
{
    int s = 0, e = nums.size();
    return bs(s, e, nums, key);
}
```
> ## Time Complexity
- Log(n) --> log2(n)
> ## OverFlow case
when s = num > 0, e = INT_MAX
than m = (s + e)/2  int over flow 
so use 
```cpp
m = s - (e-s)/2;
```
> # Lower Bound
Smallest Index such that arr[ind] >= x
![](./img/lower_bound.png)

Question
![](./img/LB_1.png)
![](./img/LB_@.png)

```cpp
int lowerBound(vector<int> arr, int n, int x) {
	int s =0,e = n-1 , m , lb = n ;
    while(s<=e){
        m = s + (e-s)/2;
         if(arr[m]>=x){
              e =m-1;
              lb = m;
        }
        else
            s = m+1;   
    }
    return lb;
}
```
> Recursion code
```cpp
int LB(int s , int e ,int &lb , int x, vector<int>& arr){
    if(s>e)return lb;
    int m = s + (e-s)/2;
    if(arr[m]>=x){
        lb = m;
     return LB(s, m-1,lb,x,arr);
    }
    else return LB(m+1,e,lb,x,arr);
}

int lowerBound(vector<int> arr, int n, int x) {
	int s =0,e =n-1,lb=n;
    return LB(s,e,lb,x,arr);
}
```
> ONE line code USing function
```cpp
int lowerBound(vector<int> arr, int n, int x) {
	
    return lower_bound(arr.begin(),arr.end(),x)-arr.begin();
}
```

> # UPPER BOUND
if smallest index such that arr[ind]>x
![](./img/UB_1.png)
![](./img/UB_2.png) 

solve 
![](./img/UBBB_0.png)

```cpp
int upperBound(vector<int> &arr, int x, int n){
	int s =0,e = n-1 ,m,ub=n;
	while(s<=e){
		m = s + (e-s)/2;
		if(arr[m]>x)
		{
			ub = m;
			e = m-1;
		}
		else s =m+1;
	}
	return ub;
}
```
> One line code 
```cpp
int upperBound(vector<int> &arr, int x, int n){
	
	return upper_bound(arr.begin(),arr.end(),x) - arr.begin();
}	
```
> # Search Insert Position
![](./img/Search%20Insert%20Position%20.png)
![](./img/Search%20Insert%20Position-2.png)

Approch --> this question can be solve by 
          both index due to unique element in the array

```cpp
// using lower bound
int searchInsert(vector<int>& arr, int m)
{
return lower_bound(arr.begin(),arr.end(),m)-arr.begin();

}
```
```cpp
// using uppor bound
int searchInsert(vector<int>& arr, int m)
{
return upper_bound(arr.begin(),arr.end(),m)-arr.begin();

}
```

