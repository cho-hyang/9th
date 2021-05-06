# _버블 정렬(Bubble Sort)_

## 알고리즘 코드

```java
package com.company;

public class Main {
    private static void bubbleSort(int[] arr){
        bubbleSort(arr, arr.length-1);
    }
    private static void bubbleSort(int[] arr, int last){
        if(last>0){
            for(int i=1; i<=last; i++) {
                if(arr[i-1]>arr[i]){
                    swap(arr, i-1, i);
                }
            }
            bubbleSort(arr, last-1);
        }
    }
    private static void swap(int[] arr, int source, int target){
        int temp=arr[source];
        arr[source]=arr[target];
        arr[target]=temp;
    }

    private static void printArray(int[] arr){
        for(int data : arr){
            System.out.print(data + ", ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        int[] arr = {3,5,4,2,1};
        printArray(arr);
        bubbleSort(arr);
        printArray(arr);

    }
}
```

## 알고리즘 코드 실행 결과

![버블소트 실행](https://user-images.githubusercontent.com/80511265/117266311-15d90580-ae90-11eb-85ba-892138b40325.PNG)

## 버블 정렬 성능 평가

- 비교 횟수
  최상, 평균, 최악 모두 일정
  (n-1)+(n-2)+...+2+1= n(n-1)/2

- 안쪽 for-루프의 if-조건이 '참'일 때의 자리바꿈은 O(1)

- 시간복잡도 : –n(n-1)/2 x O(1) = O(n^2) x O(1) = O(n^2)



# _선택 정렬(Selection Sort)_

## 알고리즘 코드

```java
package com.company;

public class Main {
    private static void printArray(int[] array){
        for(int i:array){
            System.out.print(i+", ");
        }
        System.out.println();
    }

    private static void swap(int[] array, int left, int right){
        int temp=array[left];
        array[left]=array[right];
        array[right]=temp;
    }

    private static void selectionSort(int[] array){
        int min;
        for(int i=0; i<array.length-1; i++){
            min=i;
            for(int j=i; j<array.length; j++){
                if(array[j]<array[min]){
                    min=j;
                }
            }
            if(min != i){
                swap(array, i, min);
            }
        }
    }

    public static void main(String[] args) {
        int [] array = {5, 4, 1, 3, 2};
        printArray(array);
        selectionSort(array);
        printArray(array);

    }
}
```

## 알고리즘 코드 실행 결과

![셀렉션소트 실행](https://user-images.githubusercontent.com/80511265/117266396-30ab7a00-ae90-11eb-98a9-f5ba3c26c82e.PNG)

## 선택 정렬 성능 평가

- 루프 내부 수행 횟수

  1+2+3+...+(n-2)+(n-1)=n(n-1)/2

- 루프 내부의 if-조건이 '참'일 떄의 자리바꿈은 O(1)

- 시간복잡도 :  n(n-1)/2 x O(1) = O(n^2)

- 항상 일정한 시간복잡도를 나타낸다. 입력에 민감하지 않은 알고리즘이다.



# _삽입 정렬(Insertion Sort)_

## 알고리즘 코드

```java
package com.company;

public class Main {
    private static void printArray(int[] array){
        for(int i : array){
            System.out.print(i+", ");
        }
        System.out.println();
    }

    private static void insertionSort(int[] array){
        int key, value;
        for(int i=1; i<array.length; i++){
            key = i;
            value=array[i];

            while(key>0 && value<array[key-1]){
                array[key]=array[key-1];
                key--;
            }
            array[key]=value;

        }
    }
    
    public static void main(String[] args) {
        int[] array = {5,3,4,6,1};
        printArray(array);
        insertionSort(array);
        printArray(array);
    }
}
```

## 알고리즘 코드 실행 결과

![삽입소트 실행](https://user-images.githubusercontent.com/80511265/117266466-40c35980-ae90-11eb-86cf-273da6fe709f.PNG)

## 삽입 정렬 성능 평가

- 루프 내부의 수행 횟수

  1+2+...+(n-2)+(n-1)=n(n-1)/2

- 루프 내부 수행 시간

  O(1)

- 시간복잡도 : n(n-1)/2 x O(1) = O(n^2)

- 입력의 상태에 따라 수행 시간이 달라질 수 있음.

- (n-1)번의 비교만 하면 정렬을 마지게 됨. 이 때가, 삽입 정렬 최선의 경우이고 시간복잡도는 O(n)

- 삽입 정렬은 거의 정렬된 입력에 대해서 다른 정렬 알고리즘보다 빠르다.



# _쉘 정렬(Shell Sort)_

## 알고리즘 코드

```java
package com.company;

public class Main {
    public static void main(String[] args) {
        int[] arr = {5,7,9,3,1};
        int N = arr.length;

        for(int i = N / 2; i > 0; i /= 2) {
            for(int j = i; j < N; j++) {
                int k;
                int temp = arr[j];

                for(k = j - i; k >= 0 && arr[k] > temp; k -= i) {
                    arr[k + i] = arr[k];
                }
                arr[k + i] = temp;
            }
        }

        for(int a : arr) {
            System.out.print(a +", ");
        }
    }

}
```

## 알고리즘 코드 실행 결과

![쉘소트 실행](https://user-images.githubusercontent.com/80511265/117266527-4faa0c00-ae90-11eb-9fda-e79ef297541c.PNG)

## 쉘 정렬 성능 평가

- 쉘 정렬의 시간복잡도는 아직 풀리지 않았다. 

  (가장 좋은 간격을 알아내야 하는 것이 선행되어야 하기 때문)

- (최악의 경우)시간복잡도 : O(n^2)

- (많은 실험을 통한)시간복잡도 : O(n^1.25)

- 쉘 정렬은 입력 크기가 매우 크지 않은 경우에 매우 좋은 성능을 보임.

- 임베디드 시스템에 주로 사용


