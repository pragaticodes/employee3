# employee3


#include<stdio.h>
#include<conio.h>
int main()
{
struct {
int code;
char name[20];
float bp,da;
float ns;
}emp;
char ch,choice;
FILE *fp ,*ft;
int op;
int  n;


b:printf("*******\t\t\t\tMAIN MENU\t\t\t\t*******");
printf("\n\t\t1. To create file");
printf("\n\t\t2. To read file");
printf("\n\t\t 3.To append file");
printf("\n \t\t4.To delete record");
printf("\n\t\t 5.To modify record");
printf("\n \t\t6.Exit");
printf("\nEnter your choice : ");
scanf("%d",&op);
switch(op)
{
case 1:
fp = fopen("emp.dat", "w");

a:do
{
printf("Enter emp code, name ,basic pay, DA ");
scanf("%d %s %f %f",&emp.code,emp.name, &emp.bp,&emp.da);
emp.ns=emp.bp+ emp.da;
fprintf(fp,"\n%d\t %s\t %f\t %f\t%f",emp.code,emp.name,emp.bp,emp.da,emp.ns);
printf("\nAny more data [Y/N]");
scanf("\n%c",&ch);
}while(ch =='y' || ch =='Y');
fclose(fp);
break;
case 2://reading
fp = fopen("emp.dat", "r");
while (feof(fp)==0){
fscanf(fp,"%d %s %f %f %f",&emp.code,emp.name,&emp.bp,&emp.da,&emp.ns );
printf("\n%d\t %s\t %f\t %f \t%f",emp.code,emp.name,emp.bp,emp.da,emp.ns );

}
fclose(fp);
break;
case 3: // Appending
fp = fopen("emp.dat", "a");
goto a;
break;
case 4: // Deleting a record
fp = fopen("emp.dat", "r");
ft = fopen("temp.dat", "w");
printf("Enter the code for deleting");
scanf("%d", &n);
while(feof(fp)==0)
{
fscanf(fp,"\n%d %s %f %f %f",&emp.code,emp.name,&emp.bp,&emp.da,&emp.ns );
if(emp.code != n)
fprintf(ft, "\n%d\t %s\t %f\t %f \t%f",emp.code,emp.name,emp.bp,emp.da,emp.ns );
}
fclose(fp);
fclose(ft);
remove("emp.dat");
rename("temp.dat", "emp.dat");
break;
case 5: // Modifying a record
fp = fopen("emp.dat", "r");
ft = fopen("temp.dat", "w");
printf("Enter the code to modify");
scanf("%d", &n);
while(feof(fp)==0)
{
fscanf(fp,"%d %s %f %f %f",&emp.code,emp.name,&emp.bp,&emp.da,&emp.ns );
if(emp.code == n)
{
printf("Enter name and rate of item");
scanf(" %s %f %f %f",emp.name,&emp.bp,&emp.da );
emp.ns=emp.bp+ emp.da;}


fprintf(ft, "\n%d\t %s\t %f\t %f\t %f",emp.code,emp.name,emp.bp,emp.da,emp.ns );}

fclose(fp);
fclose(ft);
remove("temp.dat");
rename("emp.dat", "temp.dat");
break;
case 6 : // Exit
break;
} //Closing brace for switch
printf("Do You want more[y/n] :");
scanf("\n%c",&choice);
if (choice=='y'|| choice=='Y')
goto b;
}

 // Closing brace for main

