# Lab-2
SDA
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#define N 5

int main(){
    int **M1;
    int *list;
    list=(int *)malloc(N*N * sizeof(int));

    M1 = (int **)malloc(N * sizeof(int *));
    for(int i=0; i<N; i++){
        M1[i] = (int *)malloc(N * sizeof(int));
        for(int j=0;j<N;j++){
            //scanf("%d",M1[i]+j);
            M1[i][j]=rand()%50+1;
        }
    }

    for(int i=0;i<N;i++){
        for(int j=0;j<N;j++){
            printf("%2d ", M1[i][j]);
        }printf("\n");
    }printf("\n");

    int i,j,dir,k;
    i=0;j=0;dir=0;k=0;

    list[k++]=M1[i][j];
    while(i!=N-1 || j!=N-1){
        if(dir==0){
            while(j>0 && i<N-1){
                i++;
                j--;
                list[k++]=M1[i][j];
            }
            if(i==N-1){
                j++;
            }else{
                i++;
            }
            list[k++]=M1[i][j];
            dir=1;
        }else if(dir==1){
            while(i>0 && j<N-1){
                i--;
                j++;
                list[k++]=M1[i][j];
            }
            if(j==N-1){
                i++;
            }else{
                j++;
            }
            list[k++]=M1[i][j];
            dir=0;
        }
    }
    list[k++]=M1[i][j];

    int *q,*swp;
    q=(int *)malloc(sizeof(int));
    *q=1;
    while(*q){
        *q=0;
        for(int i=0;i<N*N-1;i++){
            if(list[i]>list[i+1]){
                *q=list[i];
                list[i]=list[i+1];
                list[i+1]=*q;
                *q=1;
            }
        }
    }

    i=0;j=0;dir=0;k=0;

    M1[i][j]=list[k];k++;
    while(i!=N-1 || j!=N-1){
        if(dir==0){
            while(j>0 && i<N-1){
                i++;
                j--;
                M1[i][j]=list[k];k++;
            }
            if(i==N-1){
                j++;
            }else{
                i++;
            }
            M1[i][j]=list[k];k++;
            dir=1;
        }else if(dir==1){
            while(i>0 && j<N-1){
                i--;
                j++;
                M1[i][j]=list[k];k++;
            }
            if(j==N-1){
                i++;
            }else{
                j++;
            }
            M1[i][j]=list[k];k++;
            dir=0;
        }
    }
    M1[i][j]=list[N*N-1];

    for(int i=0;i<N;i++){
        for(int j=0;j<N;j++){
            printf("%2d ", M1[i][j]);
        }printf("\n");
    }printf("\n");

    return 0;
}
