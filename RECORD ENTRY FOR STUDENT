#include <stdio.h>
typedef struct
{
    int id;
    char name[25];
    int m1,m2,m3;
}STD;
STD s;
void display(FILE *);
int search(FILE *,int);
void main()
{
    int i,n,id_key,opn;
    FILE *fp;
    printf(" How many Records do you want? ");
    scanf("%d",&n);
    fp=fopen("stud.dat","w");
    for(i=0;i<n;i++)
    {
        printf("Read the Info for Student: %d (Id,name,marks1,marks2,marks3) \n",i+1);
        scanf("%d%s%d%d%d",&s.id,s.name,&s.m1,&s.m2,&s.m3);
        fwrite(&s,sizeof(s),1,fp);
    }
    fclose(fp);
    fp=fopen("stud.dat","r");
    do
    {
        printf("\nPress :: \n 1- Display\n 2- Search\n 3- Exit\n Your Option ? ");
        scanf("%d",&opn);
        switch(opn)
        {
        case 1: printf("\n Student Records in the File \n");
            display(fp);
            break;
        case 2: printf(" Read the ID of the student to be searched ?");
            scanf("%d",&id_key);
            if(search(fp,id_key))
            {
                printf("Success ! Record found in the file\n");
                printf("%d\t%s\t%d\t%d\t%d\n",s.id,s.name,s.m1,s.m2,s.m3);
            }
            else
                printf(" Failure!! Record with id %d not found\n",id_key);
            break;
        case 3:  printf(" Exit!! Press a key . . .");
            getch();
            break;
        default:  printf(" Invalid Option!!! Try again !!!\n");
            break;
        }
    }while(opn != 3);
    fclose(fp);
}
   /* End of main() */


void display(FILE *fp)
{
    rewind(fp);
    printf("ID\tName\tMarks1\tMarks2\tMarks3\n");
    while(fread(&s,sizeof(s),1,fp))

        printf("%d\t%s\t%d\t%d\t%d\n",s.id,s.name,s.m1,s.m2,s.m3);
}
int search(FILE *fp, int id_key)
{
    rewind(fp);
    while(fread(&s,sizeof(s),1,fp))
        if( s.id == id_key) return 1;
    return 0;
}
