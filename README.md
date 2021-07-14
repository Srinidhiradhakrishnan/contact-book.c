# contact-book.c

#include<stdio.h>
#include<string.h>
struct dict{
	char name[50];
	long int num;
	char mail[100];
}contact[100];

int main()
{
    int entries=0, i;
	int choice,loop=1;
	printf("================WELCOME TO CONTACT BOOK============\n");
    while(loop)
    {
    printf("1=>DISPLAY CONTACTS\n2=>ADD CONTACT\n3=>DELETE CONTACT\n4=>FIND CONTACT\n5=>EDIT CONTACT");
    printf("\nENTER YOUR CHOICE : ");
    scanf("%d",&choice);
    switch(choice){
        case 1:
        {
            if(entries == 0){
                printf("\nNo contact found");
                break;
            }
            printf("\nNAME\tNUMBER\tEMAIL :\n");
            for(i=0;i<entries;i++)
			{
				printf("\n%s\t%ld\t%s",contact[i].name,contact[i].num,contact[i].mail);
			}
			break;
        }
        case 2:
        {
            char name[50],mail[100];
            long int num=0;
            int name_len=0,mail_len=0;
            long int min=999999999, max=10000000000;
			printf("\nENTER DETAILS OF THE PERSON : ");
			while(!name_len || name_len>50){
			  printf("\nEnter name : ");
			  scanf("%s",name);  
			  name_len=strlen(name);
			}
			while(num<=min || num>=max){
			  printf("\nEnter number : ");
			  scanf("%ld",&num); 
			}
			while(!mail_len || mail_len>100){
			  printf("\nEnter mail : ");
			  scanf("%s",mail);
			  mail_len=strlen(mail);
			}
			  printf("\nSaving contact");
			  strcpy(contact[entries].name,name);
			  contact[entries].num=num;
			  strcpy(contact[entries].mail,mail);
			  entries++;  
			  printf("\nAFTER ADDING\n");
			  printf("NAME\tNUMBER\tEMAIL :");
			  for(i=0;i<entries;i++)
			  {
				printf("\n%s\t%ld\t%s",contact[i].name,contact[i].num,contact[i].mail);
			  }
			break;
        }
        case 3:
        {
            if(entries == 0){
                printf("\nNo contact found");
                break;
            }
            printf("\nENTER THE NAME TO REMOVE CONTACT :\n ");
            char name[100];
            int found=0;
			scanf("%s",name);
				for(i=0;i<entries;i++)
				{
				    if(!strcmp(name, contact[i].name))
				    {
				        found++;
				        break;
				    }
				}
                for(;i<entries;i++)
                {
                    contact[i] = contact[i+1]; 
                }
                if(found){
                    entries--;
                }
                for(i=0;i<entries;i++)
			    {
					printf("\n%s\t%ld\t%s",contact[i].name,contact[i].num,contact[i].mail);
			    }
				 break;
        }
        case 4:
        {
            char name[100];
            long int num;
            int found=0,search=0;
            if(entries == 0){
                printf("\nNo contact found");
                break;
            }
            printf("\n Search by 1.Name 2.Contact");
            scanf("%d",&search);
            switch(search){
                case 1:{
                    printf("\nENTER NAME OF THE PERSON : ");
			        scanf("%s",name);
			        for(i=0;i<entries;i++){
			        if(!strcmp(name,contact[i].name)){
			            found++;
			            printf("\nName   : %s",contact[i].name);
			            printf("\nNumber : %ld",contact[i].num);
			            printf("\nMail   : %s",contact[i].mail);
			        }
			        }
			        break;
                }
                case 2:{
                    printf("\n Enter phone number :");
                    scanf("%ld",&num);
                    for(i=0;i<entries;i++){
                    if(num == contact[i].num){
			            found++;
			            printf("\nName   : %s",contact[i].name);
			            printf("\nNumber : %ld",contact[i].num);
			            printf("\nMail   : %s",contact[i].mail);
			        }
			        }
                    break;
                }
                default:
                printf("\nEnter valid option");
                break;
            }
			if(!found){
			    printf("\n Contact detail not found");
			}
            break;	
        }
        case 5:{
            char name[50],mail[100],edit_name[50];
            int found=0,edit=0;
            int name_len=0,mail_len=0;
            long int num=0;
            long int min=999999999, max=10000000000;
            if(entries == 0){
                printf("\nNo contact found");
                break;
            }
            printf("\nENTER NAME OF THE PERSON : ");
			scanf("%s",edit_name);
			for(i=0;i<entries;i++){
			    if(!strcmp(edit_name,contact[i].name)){
			        found++;
			        printf("\n Person's current detail :");
			        printf("\nName   : %s",contact[i].name);
			        printf("\nNumber : %ld",contact[i].num);
			        printf("\nMail   : %s",contact[i].mail);
			        printf("\n Do you want to edit phone number?(1/0)");
			        scanf("%d",&edit);
			        if(edit){
			            while(!name_len || name_len>50){
			            printf("\nEnter name : ");
			            scanf("%s",name);  
			            name_len=strlen(name);
			            }
			            while(num<=min || num>=max){
			            printf("\nEnter number : ");
			            scanf("%ld",&num); 
			            }
			            while(!mail_len || mail_len>100){
			            printf("\nEnter mail : ");
			            scanf("%s",mail);
			            mail_len=strlen(mail);
			            }
			            printf("\nSaving contact");
			            strcpy(contact[i].name,name);
			            contact[i].num=num;
			            strcpy(contact[i].mail,mail);
			            printf("contact saved");
			            printf("\nName   : %s",contact[i].name);
			            printf("\nNumber : %ld",contact[i].num);
			            printf("\nMail   : %s",contact[i].mail);
			        }
			    }
			}
			if(!found){
			    printf("\n Contact detail not found");
			}
            break;
        }
        default:
        printf("Enter valid option\n");
        break;
    }
    printf("\nPRESS 1 TO CONTINUE  0 TO EXIT\n");
	scanf("%d",&loop);
}
}




