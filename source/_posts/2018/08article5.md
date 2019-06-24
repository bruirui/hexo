---
title: 排序算法
urlname: article5
date: 2018-08-27 11:13:18
tags: JavaScript
---

> [<font color="#456782">1.冒泡排序</font>](#1)
  [<font color="#456782">2.选择排序</font>](#2)
  [<font color="#456782">3.快速排序(二分法排序)</font>](#3)
  [<font color="#456782">4.插入排序</font>](#4)

<h4 id="1">1.冒泡排序</h4>中心思想：比较相邻元素的大小，互换位置
```
function bubbleSort(arr){
	let arrLen = arr.length;
	for(let i = 0; i < arrLen; i++){
		//每循环一次将最小值排到数组最后一个元素
		for(let j = 0; j < arrLen - 1 - i; j++){
			let a = arr[j],
				b = arr[j+1];
			if(a < b){	
				//降序
				arr[j] = b;
				arr[j+1] = a;
			}
		}
	}
	retrun arr;
}
```

<h4 id="2">2. 选择排序</h4>中心思想：按顺序比较，找到最大值或最小值
```
function selectionSort(arr){
	let minIndex, temp;
	for(let i = 0; i < arr.length - 1; i++){
		minIndex = i;
		//每循环一次将最大值排到较后的位置
		for(let j = i+1; j < arr.length; j++){
			if(arr[j] < arr[minIndex]){
				minIndex = j;
			}
		}
		//升序
		temp = arr[minIndex];
		arr[minIndex] = arr[i];
		arr[i] = temp;
	}
}
```

<h4 id="3">3. 快速排序(二分法排序)</h4>中心思想：将n个元素分成大致相等的两部分(也就是除以2),取array[n/2]与中间元素比较大小,小于放左边数组,大于放右边数组
```
function quickSort(arr){
	if(arr.length < 1) return arr;
	let middleIndex = Math.floor(arr.length / 2),
		middleItem = arr.splice(middleItem,1),
		leftArr = [],
		rightArr = [];
	for(let i = 0; i < arr.length; i++){
		if(arr[i] < middleItem[0]){
			leftArr.push(arr[i]);
		}else{
			rightArr.push(arr[i]);
		}
	}
	return quickSort(leftArr).concat(middleItem).concat(quickSort(rightArr));
}
```
<h4 id="4">4. 插入排序</h4>中心思想：在已经排好序的数组中插入到相应的位置，以从小到大排序为例，扫描已经排好序的片段的每一项，如大于，则继续往后，直到他小于一项时，将其插入到这项的前面
```
function insertSort(array){
    /*start根据已排列好的项数决定*/
    var start=1;
    /*按顺序，每一项检查已排列好的序列*/
    for(var i=start; i<array.length; start++,i++){
      /*跟已排好序的序列做对比，并插入到合适的位置*/
      for(var j=0; j<start; j++){
        /*小于或者等于时（我们是升序）插入到该项前面*/
        if(array[i]<=array[j]){
          console.log(array[i]+' '+array[j]);
          array.splice(j,0,array[i]);
          /*删除原有项*/
          array.splice(i+1,1);
          break;
        }
      }
    }
}
```