#include <stdio.h>
int main() {
    int num = 10;// 일반 정수형 변수 선언
    int *ptr;// 정수형을 가리키는 포인터 변수 선언
    ptr = &num;// num 변수의 주소값을 포인터 ptr에 저장
    printf("num의 원래 값: %d\n", num);
    printf("num의 주소값: %p\n", &num);
    printf("ptr이 가리키는 주소값: %p\n", ptr);
    printf("ptr이 가리키는 곳의 값: %d\n\n", *ptr);
    *ptr = 20;// 포인터를 통해 num 변수의 값을 20으로 변경
    printf("변경된 num의 값: %d\n", num);
    return 0;
}
