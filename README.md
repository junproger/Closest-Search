# Closest-Search

Given an integer array sorted in ascending order and a certain integer; the task is to find the element of the array closest to this number.

'use strict';
const arr1 = [102, 201, 210, 420, 630, 1201, 2022, 2202, 20020, 20200, 200200, 1010010, 2020202, 2002002];
const arr2 = null;
const num1 = 550;
const num2 = 505500;
/* O-notation = O(log(n)); */
function closestSearch(arr, num) {
	let part = 2;
	let size = arr.length;
	let root = Math.trunc(size/part);
	if (num > arr[size - 1]) {
		return arr[size - 1];
	} else if (num < arr[0]) {
		return arr[0];
	} else if (num < arr[root]) {
		while (true) {
			part += 1;
			root = Math.trunc(size/part);
				if (num > arr[root]) {
					break;
				};
		};
		while (true) {
			if (Math.abs(num - arr[root]) < Math.abs(arr[root + 1]- num)) {
				return arr[root];
					break;
			} else {
				root += 1;
					continue;
			};
		};
	} else if (num > arr[root]) {
		while (true) {
			part += 1;
			root = Math.trunc((size/part) * (part - 1));
				if (num < arr[root]) {
					break;
				};
		};
		while (true) {
			if (Math.abs(num - arr[root - 1]) > Math.abs(arr[root] - num)) {
				return arr[root];
					break;
			} else {
				root -= 1;
					continue;
			};
		};
	};
};
console.log(closestSearch(arr1, num1));
console.log(closestSearch(arr1, num2));
