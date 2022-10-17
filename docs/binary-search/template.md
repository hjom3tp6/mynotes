template
---

`Binary Search`

binary search find the first one

```java
public static int searchFirst(int[] arr, int target) {
  int left = 0;
  int right = arr.length - 1;
  while (left < right) {
    int mid = ( left + right ) / 2;
    if (target <= arr[mid]) {
      right = mid;
    } else {
      left = mid + 1;
    }
  }
  return left;
}
```

binary search find the last one

```java
public static int searchLast(int[] arr, int target) {
  int left = 0;
  int right = arr.length - 1;
  while ( left < right ) {
    int mid = ( left + right + 1) / 2;
    if ( target >= arr[mid] ) {
      left = mid;
    } else {
      right = mid - 1;
    }
  }
  return left;

}
```
