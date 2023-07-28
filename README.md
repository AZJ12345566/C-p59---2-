# C-p59---2-
C语言学习笔记 p59 自定义数据类型-枚举和共用体(2)
#include<stdio.h>
union Un
{
    int a;//4
    char arr[5];//5
};
int main()
{
    union Un u;
    printf("%d\n",sizeof(u));
    return 0;
}//联合体的大小至少是最大值的大小，联合体大小要对齐到最大对齐数的整数倍，因此，输出为8



C语言学习笔记 p62动态内存分配(1)
//栈区：局部变量，函数的形式参数
//堆区：动态内存的分配
//静态区：全局变量，静态变量，static
struct S
{
    char name[20];
    int age
};
int main()
{
    struct S arr[50];//50个struct S类型的数组
    //30-浪费
    //60-不够
    return 0;
}
//malloc
//free
//calloc
//realloc

//库函数参数原型：void* malloc(size_t size);
#include<stdlib.h>
#include<string.h>
#include<errno.h>
int main()
{
    //向内存申请10个整形空间
    int* p=(int*)malloc(10*sizeof(int));
    if(p==NULL)
    {
        //打印错误原因的方式
        printf("%s\n",strerror(errno));
    }
    else
    {
        //正常使用空间
        int i=0;
        for(i=0;i<10;i++)
        {
            *(p+i)=i;
        }
        for(i=0;i<10;i++)
        {
            printf("%d",*(p+i));
        }
    }
    //当动态申请的空间不再使用的时候
    //将内存还给操作系统
    free(p)；//释放空间
    p=NULL;//主动赋值空指针，防止p指针被别人拿出来乱用
    return 0;
}
