#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <Windows.h>       //弹窗头文件 
struct teacher{             //教师信息结构定义
	char name[20];          //姓名
	int num;                //编号
	char title[20];         //职称
	int regular_pay;        //固定工资
	int class_hours;        //当月课时数 
	int salary;             //当月薪水 
	struct teacher*next;
};
struct teacher *Create();                              //新建链表 
struct teacher *Insert(struct teacher *head);          //插入结点，需调用is_exist函数 
struct teacher *Delete(struct teacher *head, int num); //删除结点 
void Print(struct teacher *head);                      //遍历输出
void fprint(struct teacher *head);                     //将链表写入文件 
struct teacher *load();                                //从文件中读取信息并建成链表 
int is_exist(struct teacher *head,int m);              //根据编号判断是否存在
void Revise(struct teacher *head);                     //修改各项属性 
void Search(struct teacher *head);                     //查询教职工信息
void NumSearch(struct teacher *head);                  //按编号查询
void NameSearch(struct teacher *head);                 //按姓名查询
void TitleSearch(struct teacher *head);                //按职称查询

int main(void)
{
	struct teacher *head=NULL, *p;
	int choice1,choice2,num,x=1,y=1,c,c1=123456;  //num：删除操作中的教师编号属性 choice1：登录界面选择 choice2：操作界面选择 
	char s,t,a,b[10],b1[10]="admin";              //a:验证失败登录界面选择 b[10]:用户输入密码 t添加功能switch语句 s新建功能switch语句 
	char name[20];
	while(y){
		system("cls");
		printf("\n\n\n"); 
		printf("                                  ==========★★★欢迎光临★★★==========\n\n\n");
		printf("                        ----------------------教职工信息管理系统----------------------\n\n\n");
		printf("                                                 1.用户登录\n");
		printf("                                                 2.退出系统\n\n");
		printf("                                              请输入您的选择: ");
		scanf("%d",&choice1);
		printf("\n\n");
		getchar();
		switch(choice1){
		case 2:
			y=0;
			break;
		case 1: 
			printf("          请输入您的用户名:");
        	gets(b);
	    	printf("\n");
	    	printf("          请输入您的密码:");
	    	scanf("%d",&c);
	   	 	printf("\n");
	    	if(strcmp(b,b1)!=0||c!=c1){
	        	printf("          验证失败,请按Enter键重新输入\n");
		   		scanf("%c",&a);
	       		getchar();
	       		system("cls");
			}
			else{
				printf("          验证通过,请按Enter键进入主菜单\n");
		    	scanf("%c",&a);
		    	getchar();
		    	while(x){
		    		system("cls"); 
		    		printf("\n\n\n");
		    		printf("                            ================ ★★★教职工信息管理系统★★★================\n\n\n\n");
		    		printf("                                                   ------主菜单------                            \n\n\n"); 
		    		printf("                              < 1.查询信息 >                                 < 2.修改信息 >\n");
		    		printf("                              < 3.添加信息 >                                 < 4.删除信息 >\n");
		    		printf("                              < 5.新建列表 >                                 < 6.输出列表 >\n");
		    		printf("                              < 7.退出系统 >\n\n\n"); 
					printf("                      请输入你的选择: ");
					scanf("%d",&choice2);
	            	getchar();
    	        	system("cls");
	            	switch(choice2){
	            		case 7:
	            			x=0;
							break;
		        		case 1:
		        			head=load();
		        			if(head==NULL){
				         		printf("\n文件为空,请先录入数据!\n");
				         		getchar();
				         		break;
					 		}
				     		else{
					     		Search(head);
					     		getchar();
					 		}
				     		break;
		        		case 2:
		        			head=load();
		        			if(head==NULL){
				       			printf("\n文件为空,请先录入数据!\n");
				       			getchar();
				       			break;
				   			}
				   			else{
					   			Revise(head);
					   			getchar();
                       			break;
				  			}
				   			break;
		        		case 3:
		        			head=load();
		        			if(head==NULL){
				      			printf("文件为空,请先新建列表录入数据!\n");
				      			getchar();
				      			break;
				  			}
			      			else{
				     			head=Insert(head);
				     			printf("\n添加成功!\n");
                     			printf("\n是否将新信息保存到文件?(y/n)\n");
                     			scanf("\n%c",&t);
				     			getchar();
				     			switch(t){
				     				case 'n':
					     				break;
				     				case 'y':
				         				fprint(head);
					     				printf("\n保存成功!\n");
					     				getchar();
				         				break;
					 			}
				     			break;
							}
		        		case 4:
		        			head=load();
                 			if(head==NULL){
				    			printf("文件为空,请先录入数据!\n");
				     			getchar();
				     			break;
				 			}else{
				 				printf("请输入删除的教职工编号： \n");
		        				scanf("%d", &num);
		        				head=Delete(head, num);
							} 
		        			break; 
		        		case 5:
							printf("\n注意:输入序号为0时停止录入教职工信息!\n\n");
                     		head=Create();
                     		printf("\n是否将输入的信息保存到文件，覆盖已存在的信息?(y/n)\n\n");
                     		getchar();
				     		scanf("\n%c",&s);
				     		getchar();
					 		switch(s){
					 			case 'n':
					     			break;
				     			case 'y':
				         			fprint(head);
					     			printf("\n保存成功!\n");
					     			getchar();
					     			break;
					 		}
                     		break;
                     	case 6:
                     		head=load();
						 	if(head==NULL){
				     			printf("\n文件为空,请先录入数据!\n");
				     			getchar();
				     			break;
				 			}
			     			else{
				     			Print(head);
				     			getchar();
				     			break;
				 			} 
		        		default:
		        			printf("\n您的输入有误,请重新输入!\n");
			       			getchar();
			       			break;
		        	}
		        
				}
			} 
		break;
		default:
			printf("                您的输入有误,请重新输入!\n");
			getchar();
			break;
		}
	} 
	return 0;
 }
//将新链表写入文件中

void fprint(struct teacher *head)
{
	FILE *fp;
	char ch='1';
	struct teacher *p1;
	if((fp=fopen("f1.txt","w"))==NULL){
		printf("File open error!\n");
		exit(0);
	}
	fputc(ch,fp);
	for(p1=head;p1;p1=p1->next){
		fprintf(fp,"%d %s %s %d %d %d\n",p1->num,p1->name,p1->title,p1->regular_pay,p1->class_hours,p1->salary);
	}
	fclose(fp);
} 
//从文件中读取教职工信息并建成链表 
struct teacher *load()
{
	FILE *fp;
	char ch;
	struct teacher *head,*tail,*p1;
	head=tail=NULL;
	while((fp=fopen("f1.txt","r"))==NULL){//如果找不到文件返回错误 
		printf("File open error!\n");
		exit(0);
	}
	ch=fgetc(fp);
	if(ch=='1'){
		while(!feof(fp)){//feof函数如果遇到文件结束，函数值为非零值，文件没结束函数值为0。
		    p1=(struct teacher *)malloc(sizeof(struct teacher));
		    fscanf(fp,"%d%s%s%d%d%d\n",&p1->num,p1->name,p1->title,&p1->regular_pay,&p1->class_hours,&p1->salary);
		    if(head==NULL)
			    head=p1;
		    else
			    tail->next=p1;
		    tail=p1;
		}
	    tail->next=NULL;
	    fclose(fp);
        return head;
	}
	else
		return NULL;
}

//新建链表
struct teacher *Create()
{
	struct teacher *head,*p,*tail;
	int num,realnum=1,regular_pay,class_hours,salary;
	char name[20],title[20];	
	char title1[10]= "教授";
	char title2[10]="副教授";
	char title3[10]="讲师";
	char title4[10]="助教";
	char title5[20]="实验室人员";
	char title6[20]="办公室人员"; 
	int size=sizeof(struct teacher);
	head=NULL;
	printf("请输入教职工序号：");
	scanf("%d",&num); 
	printf("\n请输入教职工姓名: ");
    scanf("%s",name);
	getchar();
    printf("\n请输入职称(教授/副教授/讲师/助教/实验室人员/办公室人员): ");
    scanf("%s",title);
	getchar();
	while(strcmp(title,title1)!=0&&strcmp(title,title2)!=0&&strcmp(title,title3)!=0&&strcmp(title,title4)!=0&&strcmp(title,title5)!=0&&strcmp(title,title6)!=0)
	{
		printf("\n输入有误请重新输入\n\n"); 
		printf("请输入职称(教授/副教授/讲师/助教/实验室人员/办公室人员): ");
    	scanf("%s",title);
		getchar();
	}
    printf("\n请输入固定工资: ");
    scanf("%d",&regular_pay);
	getchar();
    printf("\n请输入当月课时数: ");
    scanf("%d",&class_hours);
	getchar();
	while(1){
		p=(struct teacher*)malloc(size);
		p->num=realnum++;
		strcpy(p->name,name);
		strcpy(p->title,title);
		p->regular_pay=regular_pay;
		p->class_hours=class_hours;
		if (strcmp(title,title1)==0){//根据职称计算工资 
			p->salary=p->regular_pay+30*class_hours;
		}else if(strcmp(title,title2)==0){
			p->salary=p->regular_pay+25*class_hours;
		}else if(strcmp(title,title3)==0||strcmp(title,title4)==0){
			p->salary=p->regular_pay+20*class_hours;
		}else if(strcmp(title,title5)==0){
			p->salary=p->regular_pay+10*class_hours;
		}else{
			p->salary=p->regular_pay;
		}
		p->next=NULL;
		if(head==NULL)
			head=p;
		else
			tail->next=p;
		tail=p;
		printf("\n请输入教职工序号: ");
	    scanf("%d",&num);
	    if(num==0)break;
	    else{
			printf("\n请输入教职工姓名: ");
    		scanf("%s",name);
			getchar();
    		printf("\n请输入职称(教授/副教授/讲师/助教/实验室人员/办公室人员): ");
    		scanf("%s",title);
			getchar();
			while(strcmp(title,title1)!=0&&strcmp(title,title2)!=0&&strcmp(title,title3)!=0&&strcmp(title,title4)!=0&&strcmp(title,title5)!=0&&strcmp(title,title6)!=0)
			{
				printf("\n输入有误请重新输入\n\n"); 
				printf("\n请输入职称(教授/副教授/讲师/助教/实验室人员/办公室人员): ");
    			scanf("%s",title);
				getchar();
			}
    		printf("\n请输入固定工资: ");
    		scanf("%d",&regular_pay);
			getchar();
    		printf("\n请输入当月课时数: ");
    		scanf("%d",&class_hours);
			getchar();
		}
		
	}
	return head;
}

//添加教职工信息 
struct teacher *Insert(struct teacher *head)
{
	struct teacher *ptr,*p1,*p2,*p;
	int num,time,regular_pay,class_hours,salary,n=1;
	char name[20],title[20];	
	char title1[10]= "教授";
	char title2[10]="副教授";
	char title3[10]="讲师";
	char title4[10]="助教";
	char title5[20]="实验室人员";
	char title6[20]="办公室人员"; 
	int size=sizeof(struct teacher);
	do{
        printf("请输入教师编号:");
	    scanf("%d",&num);
		n=is_exist(head,num); 
		if(n==0)
			break;
		else
			printf("您输入的编号已存在,请重新输入!\n");
	}while(1);
	printf("\n请输入教职工姓名: ");
    scanf("%s",name);
	getchar();
    printf("\n请输入职称(教授/副教授/讲师/助教/实验室人员/办公室人员): ");
    scanf("%s",title);
	getchar();
	while(strcmp(title,title1)!=0&&strcmp(title,title2)!=0&&strcmp(title,title3)!=0&&strcmp(title,title4)!=0&&strcmp(title,title5)!=0&&strcmp(title,title6)!=0)
	{
		printf("\n输入有误请重新输入\n\n"); 
		printf("\n请输入职称(教授/副教授/讲师/助教/实验室人员/办公室人员): ");
    	scanf("%s",title);
		getchar();
	}
    printf("\n请输入固定工资: ");
    scanf("%d",&regular_pay);
	getchar();
    printf("\n请输入当月课时数: ");
    scanf("%d",&class_hours);
	getchar();
	p=(struct teacher*)malloc(size);
	p->num=num;
	strcpy(p->name,name);
	strcpy(p->title,title);
	p->regular_pay=regular_pay;
	p->class_hours=class_hours;
	if (strcmp(title,title1)==0){
		p->salary=p->regular_pay+30*class_hours;
	}else if(strcmp(title,title2)==0){
		p->salary=p->regular_pay+25*class_hours;
	}else if(strcmp(title,title3)==0||strcmp(title,title4)==0){
		p->salary=p->regular_pay+20*class_hours;
	}else if(strcmp(title,title5)==0){
		p->salary=p->regular_pay+10*class_hours;
	}else{
		p->salary=p->regular_pay;
	}
	p2=head;
	ptr=p;
	while((ptr->num>p2->num)&&(p2->next!=NULL)){
		p1=p2;
		p2=p2->next;
	}
	if(ptr->num<=p2->num){
		if(head==p2)
			head=ptr;
		else{
			p1->next=ptr;
		    p->next=p2;
		}
	}
	else{
		p2->next=ptr;
		p->next=NULL;
	}
	return head;
} 
//验证添加的编号是否已存在
int is_exist(struct teacher *head,int m)
{
	struct teacher *p;
	p=head;
	while(p!=NULL){
		if(p->num==m)
			break;
		p=p->next;
	}
	if(p==NULL)
		return 0;
	else
		return 1;
}
//遍历链表 
void Print(struct teacher *head)
{
	struct teacher *ptr;
	while(head==NULL){
		printf("\n没有信息!\n");
		break;
	}
	printf("                                                           \n教职工信息如下\n");
	printf("----------------------------------------------------------------------\n");
	printf("编号         姓名        职称        固定工资   当月课时数   当月薪水   \n\n");
	for(ptr=head;ptr;ptr=ptr->next)
		printf(" %d           %s         %s         %d           %d         %d\n\n",ptr->num,ptr->name,ptr->title,ptr->regular_pay,ptr->class_hours,ptr->salary);
	printf("======================================================================\n");
}
//给出一个序号删除教师信息  
struct teacher *Delete(struct teacher *head, int num)
{
	struct teacher *ptr1, *ptr2;
	int i=2,a;
	char b,ch='1';//b是选择保存文件的参数 
	FILE *fp;
	ptr1=head;
	if(ptr1->num==num&&ptr1->next==NULL){ //对于文件中只有一组数据
		i=MessageBox (NULL,TEXT("确定要删除吗？"), TEXT("问题"),MB_ICONQUESTION|MB_OKCANCEL);
		switch(i){
			case 2:
				break;
			case 1:
				if((fp=fopen("f1.txt","w"))==NULL){
		        	printf("File open error!\n");
		        	exit(0);
				}
            	fclose(fp);
				printf("文件已清空!\n");
		}
	}//MB_OKCANCEL  有“确定”和“取消”选项在里面  MB_ICONQUESTION 一个问题标记图标
	else{
        while(ptr1->num!=num&&ptr1->next!=NULL){
		    ptr2=ptr1;
		    ptr1=ptr1->next;
		}
		if(ptr1->next==NULL){
	        if(ptr1->num==num){
		        ptr2->next=NULL;
                i=MessageBox (NULL,TEXT("确定要删除吗？"), TEXT("问题"),MB_ICONQUESTION|MB_OKCANCEL);
				switch(i){
		        	case 2:
			       		break;
	            	case 1:
		           		fprint(head);
		           		printf("删除成功!\n");
	               		getchar();
	               		break;
				}
			}
			else{
		       printf("没有找到要删除的数据!\n");
		       getchar();
			}
		}else if(ptr1==head){
		    head=ptr1->next;
            i=MessageBox (NULL,TEXT("确定要删除吗？"), TEXT("问题"),MB_ICONQUESTION|MB_OKCANCEL);
			switch(i){
		    	case 2:
  	             	break;
	        	case 1:
		         	fprint(head);
	             	printf("删除成功!\n");
                 	getchar();
		         	break;
			}
		}else{
		    ptr2->next=ptr1->next;
            i=MessageBox (NULL,TEXT("确定要删除吗？"), TEXT("问题"),MB_ICONQUESTION|MB_OKCANCEL);
			switch(i){
		    	case 2:
  	            	break;
	        	case 1:
		         	fprint(head);
	             	printf("删除成功!\n");
                 	getchar();
		         	break;
			}
		}
	}
}
//修改 
void Revise(struct teacher *head)
{
	int a,b;
	char x;//用于是否保存switch语句 
	char title1[10]="教授";
	char title2[10]="副教授";
	char title3[10]="讲师";
	char title4[10]="助教";
	char title5[20]="实验室人员";
	char title6[20]="办公室人员"; 
	struct teacher *p;
	printf("\n请输入要修改的教职工编号: ");
	scanf("%d",&a);
	p=head;
	while(p!=NULL){
		if(p->num==a)
			break;
		p=p->next;
	}
	if(p==NULL){
		printf("\n没有找到该编号的教职工\n");
		getchar();
	}
	else{//月薪应随着固定工资和课时数变化不能单独改
		printf("\n              ---------------------------------------------------\n"); 
		printf("              **  1-编号                   2-姓名             **\n");
		printf("              **  3-职称                   4-固定工资         **\n");
		printf("              **  5-当月课时数             6-放弃修改         **\n");
		printf("              ---------------------------------------------------\n");
		printf("\n请选择你要修改的信息编号: ");
		scanf("%d",&b);
		getchar();
		switch(b){
		case 1:
			printf("\n请输入新编号: ");
			scanf("%d",&p->num);
			printf("\n修改成功!\n");
			getchar();
			break;
		case 2:
			printf("\n请输入新教职工姓名: ");
			gets(p->name);
			printf("\n修改成功!\n");
			break;
		case 3:
			printf("\n请输入新职称(教授/副教授/讲师/助教/实验室人员/办公室人员): ");
			gets(p->title);
			printf("\n修改成功!\n");
			break;
		case 4:
			printf("请输入新固定工资: ");
			scanf("%d",&p->regular_pay);
			getchar(); 
			if (strcmp(p->title,title1)==0){
				p->salary=p->regular_pay+30*p->class_hours;
			}else if(strcmp(p->title,title2)==0){
				p->salary=p->regular_pay+25*p->class_hours;
			}else if(strcmp(p->title,title3)==0||strcmp(p->title,title4)==0){
				p->salary=p->regular_pay+20*p->class_hours;
			}else if(strcmp(p->title,title5)==0){ 
				p->salary=p->regular_pay+10*p->class_hours;
			}else{
				p->salary=p->regular_pay;
			}
			break;
		case 5:
			printf("\n请输入新当月课时数:");
			scanf("%d",&p->class_hours);
			getchar();
			if (strcmp(p->title,title1)==0){
				p->salary=p->regular_pay+30*p->class_hours;
			}else if(strcmp(p->title,title2)==0){
				p->salary=p->regular_pay+25*p->class_hours;
			}else if(strcmp(p->title,title3)==0||strcmp(p->title,title4)==0){
				p->salary=p->regular_pay+20*p->class_hours;
			}else if(strcmp(p->title,title5)==0){ 
				p->salary=p->regular_pay+10*p->class_hours;
			}else{
				p->salary=p->regular_pay;
			}
			printf("\n修改成功!\n");
			break;
		case 6:
			break;
		default :
			printf("\n输入有误请重新输入\n");
			break;
		}
		printf("\n是否将修改后的信息保存到文件中?(y/n)\n");
        scanf("%c",&x);
        getchar();
	    switch(x){
		    case 'n':
			    break;
		    case 'y':
		        fprint(head);
			    printf("\n保存成功!\n");
			    getchar();
			    break;
		}

		
       
	}
}

//查询教职工信息 
void Search(struct teacher *head)
{
	int a;
	printf("\n\n\n                          ★★★     教职工信息查询界面     ★★★        \n\n    ");
	printf("           --------------------------------------------------------------\n\n");
	printf("                ==== 1-编号查询 ====                     ==== 2-姓名查询 ====\n\n\n");
	printf("                ==== 3-职称查询 ====                     ==== 4-退出查询 ====\n\n");
	printf("               --------------------------------------------------------------\n\n");
	printf("请输入你要查询的编号: ");
	scanf("%d",&a);
	getchar();
	switch(a){
	case 4:
		break;
	case 1:
		NumSearch(head);
		break;
	case 2:
		NameSearch(head);
		break;
	case 3:
		TitleSearch(head);
		break;
	default:
		printf("输入有误请重新输入\n");
		break;
	}
} 
//按编号查询
void NumSearch(struct teacher *head)
{
	int a;
	struct teacher *p;
	printf("\n请输入要查询的教职工编号: ");
	scanf("%d",&a);
	getchar();
	p=head;
    while(p!=NULL){
		if(p->num==a)
			break;
		p=p->next;
	}

	if(p==NULL){
		printf("\n没有找到该编号的教职工!\n");
	}
	else{
		system("cls");
		printf("                                                           \n教职工信息如下\n");
	printf("----------------------------------------------------------------------\n");
	printf("编号         姓名        职称        固定工资   当月课时数   当月薪水   \n\n");
		printf(" %d           %s         %s         %d           %d         %d\n\n",p->num,p->name,p->title,p->regular_pay,p->class_hours,p->salary);
		printf("======================================================================\n");
	}
}
//按姓名查询
void NameSearch(struct teacher *head)
{
	char a[50];
	int flag=0;
	struct teacher *p;
	printf("请输入您要查询教职工姓名: ");
	gets(a);
	p=head;
	while(p!=NULL){
		if(strcmp(p->name,a)==0){
			flag=1;
			break;
		}
		p=p->next;
	}
    if(flag==0){
		printf("\n没有找到该教职工!\n");

	}
	else{
		system("cls");
    	printf("                                                           \n教职工信息如下\n");
	printf("----------------------------------------------------------------------\n");
	printf("编号         姓名        职称        固定工资   当月课时数   当月薪水   \n\n");
    	while(p!=NULL){
			if(strcmp(p->name,a)==0){
				printf(" %d           %s         %s         %d           %d         %d\n\n",p->num,p->name,p->title,p->regular_pay,p->class_hours,p->salary);
			}
    	p=p->next;
		}
    	printf("======================================================================\n");
	}

}
//按职称查询
void TitleSearch(struct teacher *head)
{
	char a[50];
	int flag=0;
	struct teacher *p;
	printf("请输入您要查询的教职工职称: ");
	gets(a);
	p=head;
    while(p!=NULL){
		if(strcmp(p->title,a)==0){
			flag=1;
			break;
		}
		p=p->next;
	}
    if(flag==0){
		printf("\n没有找到该教职工\n");

	}
	else{
	system("cls"); 
    printf("                                                           \n教职工信息如下\n");
	printf("----------------------------------------------------------------------\n");
	printf("编号         姓名        职称        固定工资   当月课时数   当月薪水   \n\n");
    while(p!=NULL){
		if(strcmp(p->title,a)==0){
				printf(" %d           %s         %s         %d           %d         %d\n\n",p->num,p->name,p->title,p->regular_pay,p->class_hours,p->salary);
				flag=1;
		}
    p=p->next;
	}
    printf("======================================================================\n");
	}
}
