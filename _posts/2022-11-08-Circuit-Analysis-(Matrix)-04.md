---
title: 04. Circuit Analysis(Matrix)
Author: YoungHoon Ko
date: 2022-11-08 02:20:00 +0900
categories: [University(2022-Second-Semester), Circuit Analysis]
tags: [circuit_analysis, python]
---

[toc]

## 2022-11-08 회로이론 과제

### 파이썬으로 2X2 행렬값을 입력한 후, 역행렬을 구해보자

#### 코드

##### 1. 생각의 흐름을 따라 작성

```python
print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")
a = list(map(int, input('Input the elements in a 2x2 Matrix: ').split(' ')))
# print(a)

det_a = a[0]*a[3] - a[1]*a[2]
# print(det_a)

x = []
while a != []:
    x.append(a[:2])
    a = a[2:]
# print(x)

x[0][0], x[0][1], x[1][0], x[1][1] = x[1][1], -x[0][1], -x[1][0], x[0][0]
# print(x)

res = []
for j in range(len(x)):
    for z in range(len(x)):
        k = float(x[j][z]/det_a)
        res.append('%0.2f' % k)
# print(res)

for v in range(1):
    print('The inverse Matrix is ? [', end="")
    for y in range(len(res)):
        if res[1] == res[y]:
            print(str(res[y]), end='; ')
        elif res[3] == res[y]:
            print(str(res[y]), end="")
        else:
            print(str(res[y]), end=' ')
    print(']')
print('~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~')
```

- **코드가 아주 더럽고 보기도 쉽지 않다.**(`매우 안 좋은 코드 작성법`)

- **위의 코드를 좀 더 보기 쉽고 간단한 코드로 바꿔보자**

##### 2. 함수 사용

```python
def make_a_matrix():
    mtx_ls = list(
        map(int, input("Input the elements in a 2x2 Matrix: ").split(' ')))
    a = mtx_ls[0]
    b = mtx_ls[1]
    c = mtx_ls[2]
    d = mtx_ls[3]
    mtx_2x2 = [[a, b], [c, d]]
    return mtx_2x2


def make_a_reverse_matrix(mtx_2x2):
    a_1 = mtx_2x2[0][0]
    b_1 = mtx_2x2[0][1]
    c_1 = mtx_2x2[1][0]
    d_1 = mtx_2x2[1][1]

    det_mtx = a_1 * d_1 - b_1 * c_1
    if det_mtx != 0:
        det_mtx = 1/det_mtx

        rv_a = det_mtx * d_1
        rv_a = round(rv_a, 2)

        rv_b = -(det_mtx * b_1)
        rv_b = round(rv_b, 2)

        rv_c = -(det_mtx * c_1)
        rv_c = round(rv_c, 2)

        rv_d = det_mtx * a_1
        rv_d = round(rv_d, 2)

        rv_mtx = [[rv_a, rv_b], [rv_c, rv_d]]

    return rv_mtx


def res_mtx(make_a_reverse_matrix):
    print("The inverse Matrix is ? [%.2f %.2f; %.2f %.2f]" % (make_a_reverse_matrix[0][0],
          make_a_reverse_matrix[0][1], make_a_reverse_matrix[1][0], make_a_reverse_matrix[1][1]))


print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")
arr_mtx = make_a_matrix()
resv_mtx = make_a_reverse_matrix(arr_mtx)
res_mtx(resv_mtx)
print("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~")
```

- **좀 더 깔끔한 코드로 변했다.**(`편안`)



##### 결과

```python
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Input the elements in a 2x2 Matrix: 2 4 6 8 
The inverse Matrix is ? [-1.00 0.50; 0.75 -0.25]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```





```markdown
솔직히 말하면 위의 코드는 내가 과제를 제출할 때 사용했던 코드이다.
제출 후에 너무 불편한 마음과 함수를 사용하고 싶은 마음에 주변의 선배 혹은 동기들에게 조언을 구한 뒤 다시 작성한 코드이다.

아직 함수를 다루는 것이 쉽지 않고 이해가 되지 않는 부분이 많다.
그러나 이렇게라도 하는 것이 나에게는 도움이 된다는 것은 자명한 사실이다.

이번 과제를 다시 한 번 풀어봄으로써 나는 좀 더 성장함을 느낀다.
이번을 발판 삼아서 더욱 더 멋진 코드를 짤 수 있도록 하겠다.
```

