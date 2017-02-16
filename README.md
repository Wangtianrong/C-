#include<stdio.h>
int main(){
	int K1=0,K2=0;//我就不按题给的100 arries 定义数组！！//根据二更，现在看来不按不行了。。。 
	int m1[100][2]={{0,0},};
	int m2[100][2]={{0,0},};
	int power,coefficient;
 	do{ 
	 	scanf("%d %d",&power,&coefficient);
 		m1[K1][0]=power;
 		m1[K1][1]=coefficient;
 		K1++;
	}while(power!=0);//最后一行一定是零次，零次一定是最后一行 	
 	do{
 		scanf("%d %d",&power,&coefficient);
 		m2[K2][0]=power;
 		m2[K2][1]=coefficient;
 		K2++;
	}while(power!=0);
	int sum[100][2]={{0,0},};//所需肯定小于K1+K2，在后面单独确定好sum的行数太麻烦 
    int i1,i2,max,count=0;
    if(m1[0][0]>=m2[0][0])
	max=m1[0][0];
	else
	max=m2[0][0];
	for(int n=max;n>=0;n--){//对于同一n，下面的两个for循环是相容性可进入的，但各自最多只能进入一次 
		int ret=0;
    	for(i1=0;i1<100;i1++){
    		if(m1[i1][0]==n){
    			sum[count][0]=n;sum[count][1]+=m1[i1][1];
    			ret=1;
			}
		}
		for(i2=0;i2<100;i2++){
    		if(m2[i2][0]==n){
    			sum[count][0]=n;sum[count][1]+=m2[i2][1];
    			ret=1;
			}
		}//等会可以在这里测试一下ret 
		if(ret==1) 
		count++;
		//begin to output			    
	}							//最后一行一定是零次，改！ 
	if(count==1){
		printf("%d",sum[count-1][1]);	
	}
	/*在上面补充数组位数是一位的情况,即count=1的情况*/ 
	else{
		for(int k=0;k<count-2;k++){   //这一个循环把后两个可能出现的特殊的情况排除在外 
			if(sum[k][1]!=0&&sum[k][1]!=1){	 //考虑系数为零的项的输出 
				if(sum[k+1][1]>0) 
				printf("%dx%d+",sum[k][1],sum[k][0]);//考虑对后一项的非正系数的输出 ！！ 
				else 
				printf("%dx%d",sum[k][1],sum[k][0]);
			}
			else if(sum[k][1]==0){
				if(sum[k+1][1]>0) 
				printf("+");//是零的情况考虑对后一项的非正系数的输出 ！！ 
			}
			else{
				if(sum[k+1][1]>0) 
				printf("x%d+",sum[k][0]);//考虑对后一项的非正系数的输出 ！！ 
				else 
				printf(("x%d"),sum[k][0]);
			}
		}
		if(sum[count-2][0]==1){
			if(sum[count-2][1]!=0&&sum[count-2][1]!=1){  //考虑对该项为零的输出 
				if(sum[count-1][1]>0) 
				printf("%dx+",sum[count-2][1]);//考虑对后一项的非正系数的输出 ！！ 
				else
				printf("%dx",sum[count-2][1]);
			}
			else if(sum[count-2][1]==0){
				if(sum[count-1][1]>0) 
				printf("+");//考虑对后一项的非正系数的输出 ！！ 
			}
			else{
				if(sum[count-1][1]>0) 
				printf("x+");//考虑对后一项的非正系数的输出 ！！ 
				else
				printf("x");
			}	
		}	
		else{
			if(sum[count-2][1]!=0&&sum[count-2][1]!=1){
				if(sum[count-1][1]>0) 
				printf("%dx%d+",sum[count-2][1],sum[count-2][0]);//考虑对后一项的非正系数的输出 ！！ 
				else 
				printf("%dx%d",sum[count-2][1],sum[count-2][0]);
			} 
			else if(sum[count-2][1]==0){
				if(sum[count-1][1]>0) 
				printf("+");
			}
			else{
				if(sum[count-1][1]>0) 
				printf("x%d+",sum[count-2][0]);//考虑对后一项的非正系数的输出 ！！ 
				else 
				printf("x%d",sum[count-2][0]);
			}		
		}
		int X=0;
		for(int i=0;i<count;i++){
			if(sum[i][1]!=0)
			X++;
		}
		if(X!=0){
			if(sum[count-1][1]!=0)
			printf("%d",sum[count-1][1]);
		}
		else
		printf("%d",sum[count-1][1]);
	}
	return 0;	     	
} 
/*void input(int m[][2]){
	int power,coefficient;
	scanf("%d %d",&power,&coefficient);
 	int i=0;
 	while(power!=0){
 		m[i][0]=power;
 		m[i][1]=coefficient;
 		scanf("%d %d",&power,&coefficient);
 		i++;
	}
}*///待改进
