# C-
终于决定用中文了，给自己留下了继续用github的余地hahaha
#include<stdio.h>
int main(){
	int m1[][2];
	int m2[][2];
	int sum[][2];
    input(m1);
    input(m2);
    int i1,i2,max,count=0;
    max=max(m1[0][0],m2[0][0]);
	for(int n=max;n>=0;n--){
		int ret=0;
    	for(i1=sizeof(m1)/sizeof(m1[0][0]);i1>=0;i1--){
    		if(m1[i1][0]==n){
    			sum[count][0]=n;sum[count][1]+=m1[i1][1];
    			ret=1;
			}
		}
		for(i1=sizeof(m2)/sizeof(m2[0][0]);i2>=0;i2--){
    		if(m1[i2][0]==n){
    			sum[count][0]=n;sum[count][1]+=m1[i2][1];
    			ret=1;
			}
		}//等会可以在这里测试一下ret 
		if(ret==1) 
		count++;
		//begin to output			    
	}
	for(int k=0;k<count-2;k++){   //这一个循环把后两个可能出现的特殊的情况排除在外 
		printf("%dx%d+",sum[k][1],sum[k][0]);
	}
	if(sum[count-2][0]==1)
	printf("%dx+",sum[count-2][1]);
	else
	printf("%dx%d+",sum[count-2][1],sum[count-2][0]);
	if(sum[count-1][0]==1)
	printf("%d",sum[count-1][1]);
	else
	printf("%dx%d+",sum[count-1][1],sum[count-1][0]);
	return 0;	     	
} 
void input(int m[][2]){
	int power,coefficient;
	scanf("%n %n",&power,&coefficient);
 	int i=0;
 	while(power!=0){
 		m[i][0]=power;
 		m[i][1]=coefficient;
 		scanf("%n %n",&power,&coefficient);
 		i++;
	}
}
