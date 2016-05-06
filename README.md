# bowling
/****************************************
 **      볼링 점수 계산 프로그램       **
 **        작성자 : 차윤성             **
 **        작성일 : 2016년 5월 4일     **
 ****************************************/
#include<stdio.h>
int main(void)
{
	int frame=0,trying=1,pin1=0,pin2=-1,ex_pin1=0,ex_pin2=0,ex_pinsum=0,ex2_pin1=0,frame10_sum=0,score=0;
	while(frame<=8){
		frame++;
		trying=1;
		ex2_pin1=ex_pin1;
		ex_pin1=pin1;
		ex_pin2=pin2;
		ex_pinsum=ex_pin1+ex_pin2;
		if(frame<=9){
			printf("%d번째 프레임 %d 번째 처리 핀 수 : ",frame,trying);
			scanf("%d",&pin1);
			if(pin1<=9){
				if(pin2<0){
					score+=pin1;
				}
				if((ex_pinsum==10)&&(pin2>=0)){
					if(ex_pin1!=10){
						score+=pin1*2;
					}
				}
				if((ex_pinsum!=10)&&(pin2>=0)){
					if(ex_pin1==10){
						if(ex2_pin1==10){
							score+=pin1*3;
						}
						else{
							score+=pin1*2;
						}
					}
					else{
						score+=pin1;
					}
				}
				if((ex_pinsum==10)&&(pin2>=0)){
					if(ex_pin1==10){
						if(ex2_pin1==10){
							score+=pin1*3;
						}
						else{
							score+=pin1*2;
						}
					}
				}
				printf("**** 현재까지 점수 : %d\n",score);
				trying++;
				printf("%d번째 프레임 %d 번째 처리 핀 수 : ",frame,trying);
				scanf("%d",&pin2);
				if(ex_pin1==10){
					score+=pin2*2;
				}
				else{
					score+=pin2;
				}
				printf("**** 현재까지 점수 : %d\n",score);
			}
			if(pin1==10){
				if(ex_pinsum==10){
					if(ex_pin1==10){
						if(ex2_pin1==10){
							score+=pin1*3;
						}
						else{
							score+=pin1*2;
						}
					}
					if(ex_pin1!=10){
						score+=pin1*2;
					}
				}
				if(ex_pinsum!=10){
					if(ex_pin1==10){
						if(ex2_pin1==10){
							score+=pin1*3;
						}
						else{
							score+=pin1*2;
						}
					}
					else{
						score+=pin1;
						pin2=0;
					}
				}
				printf("**** 현재까지 점수 : %d\n",score);
			}
		}
	}
	frame=10,trying=1;
	ex2_pin1=ex_pin1;
	ex_pin1=pin1;
	ex_pin2=pin2;
	ex_pinsum=ex_pin1+ex_pin2;
	if(frame==10){
		if(trying==1){
			printf("%d번째 프레임 %d 번째 처리 핀 수 : ",frame,trying);
			scanf("%d",&pin1);
			frame10_sum+=pin1;
			if(pin1<=9){
				if((ex_pinsum==10)&&(ex_pin1!=10)){
					score+=pin1*2;
				}
				if(ex_pinsum!=10){
					score+=pin1;
				}
				if(ex_pin1==10){
					score+=pin1*2;
				}
			}
			if(pin1==10){
				if(ex_pinsum==10){
					if(ex_pin1==10){
						if(ex2_pin1==10){
							score+=pin1*3;
						}
						else{
							score+=pin1*2;
						}
					}
				}
				if((ex_pinsum==10)&&(ex_pin1!=10)){
					score+=pin1*2;
				}
				if(ex_pinsum!=10){
					score+=pin1;
				}
			}
			printf("**** 현재까지 점수 : %d\n",score);
			ex2_pin1=ex_pin1;
			ex_pin1=pin1;
			ex_pin2=pin2;
			ex_pinsum=ex_pin1+ex_pin2;
		}
		trying=2;
		if(trying==2){
			printf("%d번째 프레임 %d 번째 처리 핀 수 : ",frame,trying);
			scanf("%d",&pin1);
			frame10_sum+=pin1;
			if(pin1<=9){
				if(ex2_pin1==10){
					score+=pin1*2;
				}
				else{
					score+=pin1;
				}
			}
			if(pin1==10){
				if(ex2_pin1==10){
					score+=pin1*2;
				}
				if(ex2_pin1!=10){
					score+=pin1;
				}
			}
			if(frame10_sum<10){
				printf("**** 최종점수 : %d\n",score);
			}
			if(frame10_sum>=10){
				trying=3;
				printf("**** 현재까지 점수 : %d\n",score);
			}
		}
		if(trying==3){
			printf("%d번째 프레임 %d 번째 처리 핀 수 : ",frame,trying);
			scanf("%d",&pin1);
			score+=pin1;
			printf("**** 최종 점수 : %d\n",score);
		}
	}	
	return 0;
}
