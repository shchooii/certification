# 정보처리기사 실기 · 프로그래밍 통합 문제

- 수록 범위: 2022년 3회 ~ 2025년 3회
- 총 문제 수: 83문제
- C 40문제 / Java 32문제 / Python 11문제
- 각 언어별로 나눈 뒤, 회차와 문제 번호 순으로 정리했습니다.

---

# C 문제 (40문제)

---

## 2022년 3회 · 문제 1

- 출처: `2022년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 배열 〈mines〉의 각 칸에 들어갈 값을 쓰시오.

```c
#include <stdio.h>
main( ) {
    int field[4][4] = { {0,1,0,1}, {0,0,0,1}, {1,1,1,0}, {0,1,1,1} };
    int mines[4][4] = { {0,0,0,0}, {0,0,0,0}, {0,0,0,0}, {0,0,0,0} };
    int w = 4, h = 4;
    for (int y = 0; y < h; y++) {
        for (int x = 0; x < w; x++) {
            if (field[y][x] == 0) continue;
            for (int j = y - 1; j <= y + 1; j++) {
                for (int i = x - 1; i <= x + 1; i++) {
                    if (chkover(w, h, j, i) == 1)
                        mines[j][i] += 1;
                }
            }
        }
    }
}

int chkover(int w, int h, int j, int i) {
    if (i >= 0 && i < w && j >= 0 && j < h) return 1;
    return 0;
}
```

배열 〈field〉
| 0 | 1 | 0 | 1 |
|---|---|---|---|
| 0 | 0 | 0 | 1 |
| 1 | 1 | 1 | 0 |
| 0 | 1 | 1 | 1 |

배열 〈mines〉 : (각 칸의 값을 구하시오)

답:

---

---

## 2022년 3회 · 문제 13

- 출처: `2022년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
main() {
    int s, el = 0;
    for (int i = 6; i <= 30; i++) {
        s = 0;
        for (int j = 1; j <= i / 2; j++)
            if (i % j == 0)
                s = s + j;
        if (s == i)
            el++;
    }
    printf("%d", el);
}
```

답:

---

---

## 2023년 1회 · 문제 2

- 출처: `2023년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
main() {
    char a[] = "Art";
    char* p = NULL;
    p = a;
    printf("%s\n", a);
    printf("%c\n", *p);
    printf("%c\n", *a);
    printf("%s\n", p);
    for (int i = 0; a[i] != '\0'; i++)
        printf("%c", a[i]);
}
```

답:

---

---

## 2023년 1회 · 문제 3

- 출처: `2023년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
main() {
    char* a = "qwer";
    char* b = "qwtety";
    for (int i = 0; a[i] != '\0'; i++)
        for (int j = 0; b[j] != '\0'; j++)
            if (a[i] == b[j])
                printf("%c", a[i]);
}
```

답:

---

---

## 2023년 1회 · 문제 9

- 출처: `2023년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음은 2진수 101110을 10진수로 변환하는 C 언어 프로그램이다. 프로그램을 분석하여 괄호(①~②)에 들어갈 알맞은 답을 쓰시오.

```c
#include <stdio.h>
main() {
    int input = 101110;
    int di = 1;
    int sum = 0;
    while (1) {
        if (input == 0) break;
        sum = sum + (input ( ① )( ② )) * di;
        di = di * 2;
        input = input / 10;
    }
    printf("%d", sum);
}
```

답:
- ①
- ②

---

---

## 2023년 1회 · 문제 14

- 출처: `2023년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음은 버블 정렬을 이용하여 배열에 저장된 수를 오름차순으로 정렬하는 프로그램이다. 프로그램을 분석하여 괄호(①~②)에 들어갈 알맞은 답을 쓰시오.

```c
#include <stdio.h>
void swap(int* a, int idx1, int idx2) {
    int t = a[idx1];
    a[idx1] = a[idx2];
    a[( ① )] = t;
}

void Usort(int* a, int len) {
    for (int i = 0; i < len - 1; i++)
        for (int j = 0; j < len - 1 - i; j++)
            if (a[j] > a[j + 1])
                swap(a, j, j + 1);
}

main() {
    int a[] = { 85, 75, 50, 100, 95 };
    int nx = 5;
    Usort(a, ( ② ));
}
```

답:
- ①
- ②

---

---

## 2023년 2회 · 문제 1

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 실행시킨 결과가 "43215"일 때, 〈처리조건〉을 참고하여 괄호에 들어갈 알맞은 식을 쓰시오.

```c
#include <stdio.h>
main() {
    int n[] = { 5, 4, 3, 2, 1 };
    for (int i = 0; i < 5; i++)
        printf("%d", (          ));
}
```

〈처리조건〉 괄호의 식에 사용할 문자는 다음으로 제한한다.
- n, i
- +, -, /, *, %
- 0~9, (, ), [, ]

답:

---

---

## 2023년 2회 · 문제 2

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램과 〈처리조건〉을 참고하여 괄호(①~④)에 들어갈 알맞은 식을 쓰시오.

```c
#include <stdio.h>
main() {
    int m = 4620;
    int a = ( ① );
    int b = ( ② );
    int c = ( ③ );
    int d = ( ④ );
    printf("1000원의 개수 : %d\n", a);
    printf("500원의 개수 : %d\n", b);
    printf("100원의 개수 : %d\n", c);
    printf("10원의 개수 : %d\n", d);
}
```

〈처리조건〉 괄호(①~④)의 식에 사용할 문자는 다음으로 제한한다.
- a, b, c, d, m, i, d
- +, -, /, *, %
- 0~9, (, )

답:
- ①
- ②
- ③
- ④

---

---

## 2023년 2회 · 문제 3

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 "홍길동", "김철수", "박영희"를 차례로 입력했을 때 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
char n[30];
char* getname() {
    printf("이름 입력 : ");
    gets(n);
    return n;
}

main() {
    char* n1 = getname();
    char* n2 = getname();
    char* n3 = getname();
    printf("%s\n", n1);
    printf("%s\n", n2);
    printf("%s\n", n3);
}
```

답:

---

---

## 2023년 2회 · 문제 5

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
main() {
    int n[] = { 73, 95, 82 };
    int sum = 0;
    for (int i = 0; i < 3; i++)
        sum += n[i];
    switch (sum / 30) {
        case 10:
        case 9: printf("A");
        case 8: printf("B");
        case 7:
        case 6: printf("C");
        default: printf("D");
    }
}
```

답:

---

---

## 2023년 2회 · 문제 7

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
main() {
    int c = 0;
    for (int i = 1; i <= 2023; i++)
        if (i % 4 == 0)
            c++;
    printf("%d", c);
}
```

답:

---

---

## 2023년 2회 · 문제 9

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
#define MAX_SIZE 10

int isWhat[MAX_SIZE];
int point = -1;

int isEmpty() {
    if (point == -1) return 1;
    return 0;
}

int isFull() {
    if (point == 10) return 1;
    return 0;
}

void into(int num) {
    if (isFull() == 1) printf("Full");
    else isWhat[++point] = num;
}

int take() {
    if (isEmpty() == 1) printf("Empty");
    else return isWhat[point--];
    return 0;
}

main() {
    into(5); into(2);
    while (!isEmpty()) {
        printf("%d", take());
        into(4); into(1); printf("%d", take());
        into(3); printf("%d", take()); printf("%d", take());
        into(6); printf("%d", take()); printf("%d", take());
    }
}
```

답:

---

---

## 2023년 2회 · 문제 18

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음은 데이터를 오름차순으로 정렬하는 선택 정렬 알고리즘을 C 언어 프로그램으로 구현한 것이다. 프로그램을 분석하여 괄호에 들어갈 알맞은 연산자를 쓰시오.

```c
#include <stdio.h>
main() {
    int E[] = { 64, 25, 12, 22, 11 };
    int n = sizeof(E) / sizeof(E[0]);
    int i = 0;
    do {
        int j = i + 1;
        do {
            if (E[i] (      ) E[j]) {
                int tmp = E[i];
                E[i] = E[j];
                E[j] = tmp;
            }
            j++;
        } while (j < n);
        i++;
    } while (i < n - 1);
    for (int i = 0; i <= 4; i++)
        printf("%d ", E[i]);
}
```

〈처리조건〉 괄호의 연산자는 다음으로 제한한다.
- +=, -=, *=, /=
- ==, !=, >, >=, <, <=
- &&, ||

답:

---

---

## 2023년 3회 · 문제 3

- 출처: `2023년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
main() {
    char* p = "KOREA";
    printf("1. %s\n", p);
    printf("2. %s\n", p + 1);
    printf("3. %c\n", *p);
    printf("4. %c\n", *(p + 3));
    printf("5. %c\n", *p + 4);
}
```

답:
- ①
- ②
- ③
- ④
- ⑤

---

---

## 2023년 3회 · 문제 4

- 출처: `2023년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어 프로그램과 그 〈실행결과〉를 분석하여 괄호에 공통으로 들어갈 알맞은 답을 쓰시오.

```c
#include <stdio.h>
struct insa {
    char name[10];
    int age;
    struct insa* impl_a;
    struct insa* impl_b;
};

main() {
    struct insa p1 = { "Kim", 28, NULL, NULL };
    struct insa p2 = { "Lee", 36, NULL, NULL };
    struct insa p3 = { "Park", 41, NULL, NULL };
    p1.impl_a = &p2;
    p2.impl_b = &p3;
    printf("%s\n", p1.impl_a(     )name);
    printf("%d", p2.impl_b(     )age);
}
```

〈실행결과〉
```
Lee
41
```

답:

---

---

## 2023년 3회 · 문제 9

- 출처: `2023년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
int isPerfectNum(int num) {
    int sum = 0;
    for (int i = 1; i < num; i++) {
        if (num % i == 0)
            sum += i;
    }
    if (num == sum) return 1;
    else return 0;
}
main() {
    int r = 0;
    for (int i = 1; i <= 100; i++)
        if (isPerfectNum(i))
            r += i;
    printf("%d", r);
}
```

답:

---

---

## 2023년 3회 · 문제 15

- 출처: `2023년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
int f(int n) {
    if (n <= 1) return 1;
    else return n * f(n - 1);
}
main() {
    printf("%d", f(7));
}
```

답:

---

---

## 2024년 1회 · 문제 1

- 출처: `2024년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)
※ (실제 코드는 C 언어)

```c
#include <stdio.h>
#include <stdlib.h>

main(int argc, char *argv[]) {
    int v1 = 0;
    int v2 = 35;
    int v3 = 29;
    if (v1 > v2 ? v2 : v1)
        v2 = v2 << 2;
    else
        v3 = v3 << 2;
    printf("%d", v2 + v3);
    return 0;
}
```

답:

---

---

## 2024년 1회 · 문제 10

- 출처: `2024년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
#include <string.h>

void inverse(char *str, int len) {
    for(int i = 0, j = len - 1; i < j; i++, j--) {
        char ch = str[i];
        str[i] = str[j];
        str[j] = ch;
    }
}

int main() {
    char str[100] = "ABCDEFGH";
    int len = strlen(str);
    inverse(str, len);
    for(int i = 1; i < len; i += 2) {
        printf("%c", str[i]);
    }
    return 0;
}
```

답:

---

---

## 2024년 1회 · 문제 13

- 출처: `2024년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
#include <ctype.h>

int main( ) {
    char *p = "It is 8";
    char result[100];
    int i;
    for(i = 0; p[i] != '\0'; i++) {
        if(isupper(p[i]))
            result[i] = (p[i] - 'A'+ 5) % 25 + 'A';
        else if(islower(p[i]))
            result[i] = (p[i] - 'a'+ 10) % 26 + 'a';
        else if(isdigit(p[i]))
            result[i] = (p[i] - '0'+ 3) % 10 + '0';
        else if(!(isupper(p[i]) || islower(p[i]) || isdigit(p[i])))
            result[i] = p[i];
    }
    result[i] = '\0';
    printf("변환된 문자열 : %s\n", result);
    return 0;
}
```

답:

---

---

## 2024년 2회 · 문제 5

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
void swap(int a, int b) {
    int t = a;
    a = b;
    b = t;
}

int main( ) {
    int a = 11;
    int b = 19;
    swap(a, b);
    switch(a) {
        case 1:
            b += 1;
        case 11:
            b += 2;
        deafult:
            b += 3;
            break;
    }
    printf("%d", a-b);
}
```

답:

---

---

## 2024년 2회 · 문제 6

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
void func(char *d, char *s) {
    while (*s) {
        *d = *s;
        d++;
        s++;
    }
    *d = '\0';
}

int main( ) {
    char* str1 = "first";
    char str2[50] = "teststring";
    int result = 0;
    func(str2, str1);
    for (int i = 0; str2[i] != '\0'; i++) {
        result += i;
    }
    printf("%d\n", result);
    return 0;
}
```

답:

---

---

## 2024년 2회 · 문제 9

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>

int main( ) {
    int arr[3][3] = {1, 2, 3, 4, 5, 6, 7, 8, 9};
    int* parr[2] = {arr[1], arr[2]};
    printf("%d", parr[1][1] + *(parr[1]+2) + **parr);
}
```

답:

---

---

## 2024년 2회 · 문제 19

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오.

```c
#include <stdio.h>
struct node {
    int data;
    struct node *Next;
};

int main( ) {
    struct node *head = NULL;
    struct node a = {10, 0};
    struct node b = {20, 0};
    struct node c = {30, 0};
    head = &a;
    a.Next = &b;
    b.Next = &c;
    printf("%d", head -> Next -> data);
}
```

답:

---

---

## 2024년 3회 · 문제 6

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
int func( ) {
    static int x = 0;
    x += 2;
    return x;
}
int main( ) {
    int x = 0;
    int sum = 0;
    for(int i = 0; i < 4; i++) {
        x++;
        sum += func( );
    }
    printf("%d", sum);
    return 0;
}
```

답:

---

---

## 2024년 3회 · 문제 10

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
struct Node {
    int value;
    struct Node* next;
};

void func(struct Node* node){
    while(node != NULL && node -> next != NULL) {
        int t = node -> value;
        node -> value = node -> next -> value;
        node -> next -> value = t;
        node = node -> next -> next;
    }
}

int main( ) {
    struct Node n1 = {1, NULL};
    struct Node n2 = {2, NULL};
    struct Node n3 = {3, NULL};
    n1.next = &n3;
    n3.next = &n2;
    func(&n1);
    struct Node* current = &n1;
    while(current != NULL){
        printf("%d", current -> value);
        current = current -> next;
    }
    return 0;
}
```

답:

---

---

## 2024년 3회 · 문제 19

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오.

```c
#include <stdio.h>
void func(int** arr, int size) {
    for(int i = 0; i < size; i++) {
        *(*arr + i) = (*(*arr + i) + i) % size;
    }
}

int main( ){
    int arr[] = {3, 1, 4, 1, 5};
    int* p = arr;
    int** pp = &p;
    int num = 6;
    func(pp, 5);
    num = arr[2];
    printf("%d", num);
    return 0;
}
```

답:

---

---

## 2025년 1회 · 문제 3

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
char Data[5] = {'B', 'A', 'D', 'E'};
char c;

int main( ) {
    int i, temp, temp2;
    c = 'C';
    printf("%d\n", Data[3]-Data[1]);
    for(i = 0; i < 5; ++i) {
        if(Data[i] > c)
            break;
    }

    temp = Data[i];
    Data[i] = c;
    i++;

    for(; i < 5; ++i) {
        temp2 = Data[i];
        Data[i] = temp;
        temp = temp2;
    }

    for(i = 0; i < 5; i++) {
        printf("%c", Data[i]);
    }
}
```

답:

---

---

## 2025년 1회 · 문제 12

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
#include <stdlib.h>
void set(int** arr, int* data, int rows, int cols) {
    for (int i = 0; i < rows * cols; ++i) {
        arr[((i + 1) / rows) % rows][(i + 1) % cols] = data[i];
    }
}

int main( ) {
    int rows = 3, cols = 3, sum = 0;
    int data[] = {5, 2, 7, 4, 1, 8, 3, 6, 9};
    int** arr;
    arr = (int**) malloc(sizeof(int*) * rows);
    for (int i = 0; i < cols; i++) {
        arr[i] = (int*) malloc(sizeof(int) * cols);
    }
    set(arr, data, rows, cols);
    for (int i = 0; i < rows * cols; i++) {
        sum += arr[i / rows][i % cols] * (i % 2 == 0 ? 1 : -1);
    }
    for(int i = 0; i < rows; i++) {
        free(arr[i]);
    }
    free(arr);
    printf("%d", sum);
}
```

답:

---

---

## 2025년 1회 · 문제 14

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음에 제시된 코드를 이용하여 순서도의 번호(①~⑥)에 들어갈 알맞은 코드를 작성하고, 문장 커버리지로 구성할 테스트 케이스를 작성하시오.

〈코드〉
```c
int main(int b[], int m, int x) {
    int a = 0;
    while (a < m || b[a] < x) {
        if (b[a] < 0)
            b[a] = -b[a];
        a++;
    }
    return 1;
}
```

〈순서도〉 (①~⑥ 빈칸)

답:
- ① / ② / ③ / ④ / ⑤ / ⑥
- 문장 커버리지 기준 테스트 케이스 : ① → ② → ( ) → ( ) → ( ) → ( ) → ( )

---

---

## 2025년 1회 · 문제 17

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>

typedef struct student {
    char* name;
    int score[3];
} Student;

int dec(int enc) {
    return enc & 0xA5;
}

int sum(Student* p) {
    return dec(p->score[0]) + dec(p->score[1]) + dec(p->score[2]);
}

int main( ) {
    Student s[2] = { "Kim", {0xA0, 0xA5, 0xDB}, "Lee", {0xA0, 0xED, 0x81} };
    Student* p = s;
    int result = 0;
    for (int i = 0; i < 2; i++) {
        result += sum(&s[i]);
    }
    printf("%d", result);
    return 0;
}
```

답:

---

---

## 2025년 1회 · 문제 20

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
#include <stdlib.h>
typedef struct Data {
    int value;
    struct Data *next;
} Data;

Data* insert(Data* head, int value) {
    Data* new_node = (Data*)malloc(sizeof(Data));
    new_node -> value = value;
    new_node -> next = head;
    return new_node;
}

Data* reconnect(Data* head, int value) {
    if (head == NULL || head -> value == value) return head;
    Data *prev = NULL, *curr = head;
    while (curr != NULL && curr -> value != value) {
        prev = curr;
        curr = curr -> next;
    }
    if (curr != NULL && prev != NULL) {
        prev -> next = curr -> next;
        curr -> next = head;
        head = curr;
    }
    return head;
}

int main( ) {
    Data *head = NULL, *curr;
    for (int i = 1; i <= 5; i++)
        head = insert(head, i);
    head = reconnect(head, 3);
    for (curr = head; curr != NULL; curr = curr -> next)
        printf("%d", curr->value);
    return 0;
}
```

답:

---

# 정답 및 해설 (2025년 1회)

- [문제 1] 세션 하이재킹(Session Hijacking)
- [문제 2] ① 도메인  ② 개체  ③ 참조
- [문제 3] `4` / `BACDE`
  - ※ 주의: 출력값 사이에 공백이나 콤마를 넣으면 오답. 대소문자 구분(소문자 bacde로 쓰면 오답).

---

## 2025년 2회 · 문제 5

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
#include <stdlib.h>
struct node {
    int p;
    struct node* n;
};
int main( ) {
    struct node a = {1, NULL};
    struct node b = {2, NULL};
    struct node c = {3, NULL};
    a.n = &b; b.n = &c; c.n = NULL;
    c.n = &a; a.n = &b; b.n = NULL;
    struct node* head = &c;
    printf("%d %d %d", head -> p, head -> n -> p, head -> n -> n -> p);
    return 0;
}
```

답:

---

---

## 2025년 2회 · 문제 10

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
#define SIZE 3

typedef struct {
    int a[SIZE];
    int front;
    int rear;
} Queue;

void enq(Queue* q, int val) {
    q -> a[q -> rear] = val;
    q -> rear = (q -> rear + 1) % SIZE;
}

int deq(Queue* q) {
    int val = q -> a[q -> front];
    q -> front = (q -> front + 1) % SIZE;
    return val;
}

int main( ) {
    Queue q = {{0}, 0, 0};
    enq(&q, 1);
    enq(&q, 2);
    deq(&q);
    enq(&q, 3);
    printf("%d 그리고 %d", deq(&q), deq(&q));
    return 0;
}
```

답:

---

---

## 2025년 2회 · 문제 16

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>

struct dat {
    int x;
    int y;
};

int main( ) {
    struct dat a[] = {{1, 2}, {3, 4}, {5, 6}};
    struct dat* ptr = a;
    struct dat** pptr = &ptr;
    (*pptr)[1] = (*pptr)[2];
    printf("%d 그리고 %d", a[1].x, a[1].y);
    return 0;
}
```

답:

---

---

## 2025년 2회 · 문제 20

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    char c;
    struct node* p;
};

struct node* func(char* s) {
    struct node* h = NULL, *n;
    while(*s) {
        n = malloc(sizeof(struct node));
        n -> c = *s++;
        n -> p = h;
        h = n;
    }
    return h;
}

int main( ) {
    struct node* n = func("BEST");
    while(n) {
        putchar(n -> c);
        struct node* t = n;
        n = n -> p;
        free(t);
    }
    return 0;
}
```

답:

---

---

## 2025년 3회 · 문제 5

- 출처: `2025년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
struct Test {
    int i;
    const char *g;
};
int main( ) {
    struct Test test[ ] = {{1, "AB"}, {2, "DC"}, {3, "EB"}};
    struct Test *p = &test[1];
    printf("%s", p->g + (p->i - 1));
    return 0;
}
```

답:

---

---

## 2025년 3회 · 문제 16

- 출처: `2025년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
int main(void) {
    char str[ ] = "REPUBLICOFKOREA";
    int a = 0;
    while (str[a] != '\0')
        ++a;
    putchar(str[a-2]);
    return 0;
}
```

답:

---

---

## 2025년 3회 · 문제 17

- 출처: `2025년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
int main( ) {
    int x = 7, y = 4, z;
    z = y % 3 < 3 ? 2 : 1;
    z = z & z >> 1;
    z = x > 5 && z <= 3 ? z * x : z / x;
    printf("%d", z);
    return 0;
}
```

답:

---

---

## 2025년 3회 · 문제 19

- 출처: `2025년_3회.md`
- 분류: 프로그래밍
- 언어: C

다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```c
#include <stdio.h>
struct Node {
    struct Node* next;
    unsigned int x;
};

int main( ) {
    struct Node t1 = {0, 5u};
    struct Node t2 = {0, 7u};
    struct Node t3 = {0, 11u};

    t3.next = &t2;
    t2.next = &t1;

    struct Node* curr = &t3;
    int sum = 0;

    while (curr) {
        sum = sum * 3 + curr->x;
        curr = curr->next;
    }

    sum = (sum ^ 42u) + 100u;
    printf("%u\n", sum);
}
```

답:

---

---

# Java 문제 (32문제)

---

## 2022년 3회 · 문제 4

- 출처: `2022년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Test {
    public static void main(String[] args) {
        int result[] = new int[5];
        int arr[] = { 77, 32, 10, 99, 50 };
        for(int i = 0; i < 5; i++) {
            result[i] = 1;
            for(int j = 0; j < 5; j++)
                if(arr[i] < arr[j])
                    result[i]++;
        }
        for(int k = 0; k < 5; k++)
            System.out.print(result[k]);
    }
}
```

답:

---

---

## 2022년 3회 · 문제 19

- 출처: `2022년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Test {
    static int[] mkarr( ) {
        int[] tmpArr = new int[4];
        for (int i = 0; i < tmpArr.length; i++)
            tmpArr[i] = i;
        return tmpArr;
    }
    public static void main(String[] args) {
        int[] arr;
        arr = mkarr( );
        for (int i = 0; i < arr.length; i++)
            System.out.print(arr[i]);
    }
}
```

답:

---

---

## 2022년 3회 · 문제 20

- 출처: `2022년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Test {
    public static void main(String[] args) {
        int r = 0;
        for (int i = 1; i < 999; i++) {
            if (i % 3 == 0 && i % 2 == 0)
                r = i;
        }
        System.out.print(r);
    }
}
```

답:

---

# 정답 및 해설 (2022년 3회) — 일부

- [문제 1] 배열 〈mines〉 각 칸 값 (지뢰찾기: field에서 1인 위치를 중심으로 3행 3열 범위에 +1):
  - 배열 field:
    ```
    0 1 0 1
    0 0 0 1
    1 1 1 0
    0 1 1 1
    ```

---

## 2023년 1회 · 문제 1

- 출처: `2023년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
class Static {
    public int a = 20;
    static int b = 0;
}
public class Test {
    public static void main(String[] args) {
        int a = 10;
        Static.b = a;
        Static st = new Static();
        System.out.println(Static.b++);
        System.out.println(st.b);
        System.out.println(a);
        System.out.print(st.a);
    }
}
```

답:

---

---

## 2023년 1회 · 문제 17

- 출처: `2023년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
abstract class Vehicle {
    String name;
    abstract public String getName(String val);
    public String getName() {
        return "Vehicle name : " + name;
    }
}

class Car extends Vehicle {
    private String name;
    public Car(String val) {
        name = super.name = val;
    }
    public String getName(String val) {
        return "Car name : " + val;
    }
    public String getName(byte[] val) {
        return "Car name : " + val;
    }
}

public class Test {
    public static void main(String[] args) {
        Vehicle obj = new Car("Spark");
        System.out.print(obj.getName());
    }
}
```

답:

---

---

## 2023년 1회 · 문제 20

- 출처: `2023년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
class Parent {
    int x = 1000;
    Parent() {
        this(3000);
    }
    Parent(int x) {
        this.x = x;
    }
}
class Child extends Parent {
    int x = 4000;
    Child() {
        this(5000);
    }
    Child(int x) {
        this.x = x;
    }
    int getX() {
        return this.x;
    }
}
public class Test {
    public static void main(String[] args) {
        Child c = new Child();
        System.out.println(c.getX());
    }
}
```

답:

---

# 정답 및 해설 (2023년 1회) — 일부

- [문제 1] 실행 결과 (각 줄 출력):
  ```
  10
  11
  10
  20
  ```
  ※ 주의: 출력값 사이에 줄 나눔 없이 쉼표를 넣어 `10, 11, 10, 20`으로 쓰면 오답 처리.

---

## 2023년 2회 · 문제 14

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Test {
    public static void main(String[] args) {
        String str1 = "Programming";
        String str2 = "Programming";
        String str3 = new String("Programming");
        System.out.println(str1==str2);
        System.out.println(str1==str3);
        System.out.println(str1.equals(str3));
        System.out.println(str2.equals(str3));
    }
}
```

답:

---

---

## 2023년 3회 · 문제 1

- 출처: `2023년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
class SuperObject {
    public void draw() {
        System.out.println("A");
        draw();
    }
    public void paint() {
        System.out.print('B');
        draw();
    }
}
class SubObject extends SuperObject {
    public void paint() {
        super.paint();
        System.out.print('C');
        draw();
    }
    public void draw() {
        System.out.print('D');
    }
}
public class Test {
    public static void main(String[] args) {
        SuperObject a = new SubObject();
        a.paint();
        a.draw();
    }
}
```

답:

---

---

## 2023년 3회 · 문제 12

- 출처: `2023년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음은 오류가 발생하는 JAVA 프로그램이다. 프로그램을 분석하여 오류가 발생하는 라인을 쓰시오.

```java
1  class Person {
2      private String name;
3      public Person(String val) {
4          name = val;
5      }
6      public static String get() {
7          return name;
8      }
9      public void print() {
10         System.out.println(name);
11     }
12 }
13 public class Test {
14     public static void main(String[] args) {
15         Person obj = new Person("Kim");
16         obj.print();
17     }
18 }
```

답:

---

---

## 2023년 3회 · 문제 14

- 출처: `2023년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
class P {
    public int calc(int n) {
        if (n <= 1) return n;
        return calc(n - 1) + calc(n - 2);
    }
}
class C extends P {
    public int calc(int n) {
        if (n <= 1) return n;
        return calc(n - 1) + calc(n - 3);
    }
}
public class Test {
    public static void main(String[] args) {
        P obj = new C();
        System.out.print(obj.calc(7));
    }
}
```

답:

---

---

## 2024년 1회 · 문제 5

- 출처: `2024년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
class Connection {
    private static Connection _inst = null;
    private int count = 0;
    public static Connection get() {
        if(_inst == null) {
            _inst = new Connection();
            return _inst;
        }
        return _inst;
    }
    public void count() { count++; }
    public int getCount() { return count; }
}
public class Test {
    public static void main(String[] args) {
        Connection conn1 = Connection.get();
        conn1.count();
        Connection conn2 = Connection.get();
        conn2.count();
        Connection conn3 = Connection.get();
        conn3.count();
        conn1.count();
        System.out.print(conn1.getCount());
    }
}
```

답:

---

---

## 2024년 1회 · 문제 11

- 출처: `2024년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램의 실행 순서를 나열하시오. (단, 같은 번호는 중복해서 작성하지 마시오.)

```java
class Parent {
    int x, y;
①  Parent(int x, int y) {
        this.x = x;
        this.y = y;
    }
②  int getX() {
        return x*y;
    }
}

class Child extends Parent {
    int x;
③  Child(int x) {
        super(x+1, x);
        this.x = x;
    }
④  int getX(int n) {
        return super.getX() + n;
    }
}

public class Main {
⑤  public static void main(String[] args) {
⑥      Parent parent = new Child(10);
⑦      System.out.println(parent.getX());
    }
}
```
(①~⑦은 각 문장의 위치 표시)

답:

---

---

## 2024년 1회 · 문제 18

- 출처: `2024년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
class firstArea {
    int x, y;
    public firstArea(int x, int y) {
        this.x = x;
        this.y = y;
    }
    public void print() {
        System.out.println(x+y);
    }
}

class secondArea extends firstArea {
    int bb = 3;
    public secondArea(int i) {
        super(i, i+1);
    }
    public void print() {
        System.out.println(bb*bb);
    }
}

public class Main {
    public static void main(String[] args) {
        firstArea st = new secondArea(10);
        st.print();
    }
}
```

답:

---

> ※ [문제 19]와 [문제 20]은 한국산업인력공단에서 시험 문제를 공개하지 않아, 수험생의 기억을 토대로 재구성하기에 어려움이 있어 원본 교재에 수록되지 않았습니다.

---

# 정답 및 해설 (2024년 1회) — 일부

- [문제 1] `151`
- [문제 2] OSPF (Open Shortest Path First protocol) ※ 다음 중 하나를 쓰면 됨

---

## 2024년 2회 · 문제 1

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Test {
    public static void main(String[] args) {
        String str = "ITISTESTSTRING";
        String[] result = str.split("T");
        System.out.print(result[3]);
    }
}
```

답:

---

---

## 2024년 2회 · 문제 2

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Test {
    public static void check(int[] x, int[] y) {
        if(x == y) System.out.print("O");
        else System.out.print("N");
    }

    public static void main(String[] args) {
        int a[] = new int[] {1, 2, 3, 4};
        int b[] = new int[] {1, 2, 3, 4};
        int c[] = new int[] {1, 2, 3};
        check(a, b);
        check(b, c);
        check(a, c);
    }
}
```

답:

---

---

## 2024년 2회 · 문제 7

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
interface Number {
    int sum(int[] a, boolean odd);
}

public class Test {
    public static void main(String[] args) {
        int a[] = {1, 2, 3, 4, 5, 6, 7, 8, 9};
        OENumber OE = new OENumber( );
        System.out.print(OE.sum(a, true) + ", " + OE.sum(a, false));
    }
}

class OENumber implements Number {
    public int sum(int[] a, boolean odd) {
        int result = 0;
        for (int i = 0; i < a.length; i++) {
            if ((odd && a[i] % 2 != 0) || (!odd && a[i] % 2 == 0)) {
                result += a[i];
            }
        }
        return result;
    }
}
```

답:

---

---

## 2024년 2회 · 문제 8

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Test {
    public static String rf(String str, int index, boolean[] seen) {
        if(index < 0) return "";
        char c = str.charAt(index);
        String result = rf(str, index-1, seen);
        if(!seen[c]) {
            seen[c] = true;
            return c + result;
        }
        return result;
    }

    public static void main(String[] args) {
        String str = "abacabcd";
        int len = str.length( );
        boolean[] seen = new boolean[256];
        System.out.print(rf(str, len-1, seen));
    }
}
```

답:

---

---

## 2024년 3회 · 문제 1

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 JAVA로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main{
    static String[] x = new String[3];
    static void func(String[] x, int y) {
        for(int i = 1; i < y; i++) {
            if(x[i-1].equals(x[i])) {
                System.out.print("O");
            }
            else {
                System.out.print("N");
            }
        }
        for (String z : x) {
            System.out.print(z);
        }
    }
    public static void main(String[] args) {
        x[0] = "A";
        x[1] = "A";
        x[2] = new String("A");
        func(x, 3);
    }
}
```

답:

---

---

## 2024년 3회 · 문제 14

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main{
    public static void main(String[] args) {
        B a = new D( );
        D b = new D( );
        System.out.print(a.getX( ) + a.x + b.getX( ) + b.x);
    }
}

class B {
    int x = 3;
    int getX( ) {
        return x * 2;
    }
}
class D extends B {
    int x = 7;
    int getX( ) {
        return x * 3;
    }
}
```

답:

---

---

## 2024년 3회 · 문제 17

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    public static void main(String[] args) {
        int sum = 0;
        try {
            func( );
        }
        catch (NullPointerException e) {
            sum = sum + 1;
        }
        catch (Exception e) {
            sum = sum + 10;
        }
        finally {
            sum = sum + 100;
        }
        System.out.print(sum);
    }

    static void func( ) throws Exception {
        throw new NullPointerException( );
    }
}
```

답:

---

---

## 2024년 3회 · 문제 18

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
class Printer {
    void print(Integer a) {
        System.out.print("A" + a);
    }
    void print(Object a) {
        System.out.print("B" + a);
    }
    void print(Number a) {
        System.out.print("C" + a);
    }
}

public class Main {
    public static void main(String[] args) {
        new Collection<>(0).print( );
    }
    public static class Collection<T> {
        T value;
        public Collection(T t) {
            value = t;
        }
        public void print( ) {
            new Printer( ).print(value);
        }
    }
}
```

답:

---

---

## 2025년 1회 · 문제 5

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    public static void main(String[ ] args) {
        int a = 5, b = 0;
        try {
            System.out.print(a/b);
        }
        catch(ArithmeticException e){
            System.out.print("출력1");
        }
        catch(ArrayIndexOutOfBoundsException e) {
            System.out.print("출력2");
        }
        catch(NumberFormatException e) {
            System.out.print("출력3");
        }
        catch(Exception e) {
            System.out.print("출력4");
        }
        finally {
            System.out.print("출력5");
        }
    }
}
```

답:

---

---

## 2025년 1회 · 문제 11

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    public static void main(String[ ] args) {
        new Child( );
        System.out.println(Parent.total);
    }
}

class Parent {
    static int total = 0;
    int v = 1;
    public Parent( ) {
        total += ++v;
        show( );
    }
    public void show( ) {
        total += total;
    }
}

class Child extends Parent {
    int v = 10;
    public Child( ) {
        v += 2;
        total += v++;
        show( );
    }
    @Override
    public void show( ) {
        total += total * 2;
    }
}
```

답:

---

---

## 2025년 1회 · 문제 16

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    public static void main(String[ ] args) {
        System.out.println(calc("5"));
    }
    static int calc(int value) {
        if (value <= 1) return value;
        return calc(value - 1) + calc(value - 2);
    }
    static int calc(String str) {
        int value = Integer.valueOf(str);
        if (value <= 1) return value;
        return calc(value - 1) + calc(value - 3);
    }
}
```

답:

---

---

## 2025년 1회 · 문제 18

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    public static void main(String[ ] args) {
        int[ ] data = {3, 5, 8, 12, 17};
        System.out.println(func(data, 0, data.length - 1));
    }
    static int func(int[ ] a, int st, int end) {
        if (st >= end) return 0;
        int mid = (st + end) / 2;
        return a[mid] + Math.max(func(a, st, mid), func(a, mid + 1, end));
    }
}
```

답:

---

---

## 2025년 2회 · 문제 4

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    public static void change(String[] data, String s){
        data[0] = s;
        s = "Z";
    }
    public static void main(String[] args) {
        String data[] = { "A" };
        String s = "B";
        change(data, s);
        System.out.print(data[0] + s);
    }
}
```

답:

---

---

## 2025년 2회 · 문제 9

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    static interface F {
        int apply(int x) throws Exception;
    }
    public static int run(F f) {
        try {
            return f.apply(3);
        } catch (Exception e) {
            return 7;
        }
    }
    public static void main(String[] args) {
        F f = (x) -> {
            if (x > 2) {
                throw new Exception( );
            }
            return x * 2;
        };
        System.out.print(run(f) + run((int n) -> n + 9));
    }
}
```

답:

---

---

## 2025년 2회 · 문제 18

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    public static class Parent {
        public int x(int i) { return i + 2; }
        public static String id( ) { return "P"; }
    }
    public static class Child extends Parent {
        public int x(int i) { return i + 3; }
        public String x(String s) { return s + "R"; }
        public static String id( ) { return "C"; }
    }
    public static void main(String[] args) {
        Parent ref = new Child( );
        System.out.println(ref.x(2) + ref.id( ));
    }
}
```

답:

---

---

## 2025년 2회 · 문제 19

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
public class Main {
    public static class BO {
        public int v;
        public BO(int v) {
            this.v = v;
        }
    }
    public static void main(String[] args) {
        BO a = new BO(1);
        BO b = new BO(2);
        BO c = new BO(3);
        BO[] arr = {a, b, c};
        BO t = arr[0];
        arr[0] = arr[2];
        arr[2] = t;
        arr[1].v = arr[0].v;
        System.out.println(a.v + "a" + b.v + "b" + c.v);
    }
}
```

답:

---

---

## 2025년 3회 · 문제 6

- 출처: `2025년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```java
enum Tri {
    A("A"), B("AB"), C("ABC");
    private String code;
        Tri(String code) {
    this.code = code;
    }
    public String code( ) {
        return code;
    }
}

public class Main {
    public static void main(String[] args) {
        Tri t = Tri.values( )[Tri.A.name( ).length( )];
        System.out.print(t.code( ));
    }
}
```

답:

---

---

## 2025년 3회 · 문제 10

- 출처: `2025년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 괄호에 들어갈 알맞은 코드를 쓰시오.

```java
interface Cals {
    public void get(int v);
}

class Test ( ) Cals {
    public void get(int v) {
        System.out.print(v*v);
    }
}

public class Main {
    public static void main(String[] args) {
        Cals a = new Test();
        a.get(10);
    }
}
```

답:

---

---

## 2025년 3회 · 문제 18

- 출처: `2025년_3회.md`
- 분류: 프로그래밍
- 언어: Java

다음 Java로 구현된 프로그램을 분석하여 괄호에 들어갈 알맞은 코드를 쓰시오.

```java
class Rectangle {
    int x, y;
    Rectangle(int x, int y) {
        this.x = x;
        this.y = y;
    }
    int getArea( ) {
        return x*y;
    }
}

class Square extends Rectangle {
    Square(int a) {
        (    )(a, a);
    }
    int getSquareArea( ) {
        return x*y;
    }
}

public class Main {
    public static void main(String[] args) {
        Square sq = new Square(10);
        System.out.println(sq.getSquareArea( ));
    }
}
```

답:

---

---

# Python 문제 (11문제)

---

## 2022년 3회 · 문제 9

- 출처: `2022년_3회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
a = [1, 2, 3, 4, 5]
a = list(map(lambda num : num + 100, a))
print(a)
```

답:

---

---

## 2023년 1회 · 문제 15

- 출처: `2023년_1회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
asia = { '한국', '중국', '일본' }
asia.add('베트남')
asia.remove('일본')
asia.update({'한국', '홍콩', '태국'})
print(asia)
```

답:

---

---

## 2023년 2회 · 문제 19

- 출처: `2023년_2회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
a = "engineer information programming"
b = a[:3]
c = a[4:6]
d = a[29:]
e = b + c + d
print(e)
```

답:

---

---

## 2023년 3회 · 문제 16

- 출처: `2023년_3회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python 프로그램과 그 〈실행결과〉를 분석하여 괄호에 들어갈 알맞은 예약어를 쓰시오. (〈실행결과〉 첫 번째 라인의 '5 10'은 입력받은 값에 해당한다.)

```python
x, y = input("x, y의 값을 공백으로 구분하여 입력 : ").(     )(' ')
print("x의 값 :", x)
print("y의 값 :", y)
```

〈실행결과〉
```
x, y의 값을 공백으로 구분하여 입력 : 5 10
x의 값 : 5
y의 값 : 10
```

답:

---

---

## 2024년 1회 · 문제 8

- 출처: `2024년_1회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
a = [ 'Seoul', 'Kyeonggi', 'Incheon', 'Daejeon', 'Daegu', 'Pusan'];
str01 = 'S'
for i in a:
    str01 = str01 + i[1]
print(str01)
```

답:

---

---

## 2024년 2회 · 문제 3

- 출처: `2024년_2회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
def cnt(str, p):
    result = 0;
    for i in range(len(str)):
        sub = str[i:i+len(p)]
        if sub == p:
            result += 1
    return result
str = "abdcabcabca"
p1 = "ca"
p2 = "ab"
print(f'ab{cnt(str, p1)} ca{cnt(str, p2)}')
```

답:

---

---

## 2024년 3회 · 문제 2

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
def func(lst):
    for i in range(len(lst) // 2):
        lst[i], lst[-i-1] = lst[-i-1], lst[i]
lst = [1,2,3,4,5,6]
func(lst)
print(sum(lst[::2]) - sum(lst[1::2]))
```

답:

---

---

## 2024년 3회 · 문제 12

- 출처: `2024년_3회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
def func(value):
    if type(value) == type(100):
        return 100
    elif type(value) == type(""):
        return len(value)
    else:
        return 20
a = "100.0"
b = 100.0
c = (100, 200)
print(func(a) + func(b) + func(c))
```

답:

---

---

## 2025년 1회 · 문제 19

- 출처: `2025년_1회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.children = []

def tree(li):
    nodes = [Node(i) for i in li]
    for i in range(1, len(li)):
        nodes[(i - 1) // 2].children.append(nodes[i])
    return nodes[0]

def calc(node, level=0):
    if node is None:
        return 0
    return (node.value if level % 2 == 1 else 0) + sum(calc(n, level + 1) for n in node.children)

li = [3, 5, 8, 12, 15, 18, 21]
root = tree(li)
print(calc(root))
```

답:

---

---

## 2025년 2회 · 문제 17

- 출처: `2025년_2회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오. (단, 출력문의 출력 서식을 준수하시오.)

```python
lst = [1,2,3]
dst = {i : i* 2 for i in lst}
s = set(dst.values( ))
lst[0] = 99
dst[2] = 7
s.add(99)
print(len(s & set(dst.values( ))))
```

답:

---

---

## 2025년 3회 · 문제 11

- 출처: `2025년_3회.md`
- 분류: 프로그래밍
- 언어: Python

다음 Python으로 구현된 프로그램을 분석하여 출력값(①~⑧)에 들어갈 알맞은 값을 쓰시오.

```python
data = [
    [3, 5, 2, 4, 1],
    [4, 5, 1],
    [4, 4, 1, 5, 4],
    [4, 5]
]
result = { }
for index, lis in enumerate(data):
    list_sum = sum(lis)
    list_len = len(lis)
    result[index] = (list_sum, list_len)
print(result)
```

〈보기〉
{0: (①, ②), 1: (③, ④), 2: (⑤, ⑥), 3: (⑦, ⑧)}

답:
- ① / ② / ③ / ④ / ⑤ / ⑥ / ⑦ / ⑧

---

---
