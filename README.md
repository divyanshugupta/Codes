Codes
=====
#include<stdio.h>

void decode(int counter,char symbol,int flag)
{
  symbol = symbol+counter;
	printf("%c",symbol);
	if(flag == 1)
		printf(" ");
}

int main()
{
	int counter,i,j,flag = 0;
	char sms[50],ch,ans;
	do
	{
		i=0;
		printf("\nEnter the encoded message:");
		gets(sms);
		while(sms[i] != '\0')
		{
			if(sms[i] == '0' || sms[i] == ' ' || sms[i] == '\0')
				j = ++i;
			else
				j = i;
			counter = 0;
			flag = 0;
			ch = '0';
			while(sms[i] == sms[j] && sms[i] != '0' && sms[i] != ' ' && sms[i] != '\0')
			{
				counter++;
				ch = sms[i];
				if(sms[i+1] == '0')
					flag = 1;
				i++;
			}
			switch(ch)
			{
				case '2' : counter = counter%3;
					   if(counter == 0)
						counter = 3;
					   decode(counter,96,flag);
					   break;
				case '3' : counter = counter%3;
					   if(counter == 0)
						counter = 3;
					   decode(counter,99,flag);
					   break;
				case '4' : counter = counter%3;
					   if(counter == 0)
						counter = 3;
					   decode(counter,102,flag);
					   break;
				case '5' : counter = counter%3;
					   if(counter == 0)
						counter = 3;
					   decode(counter,105,flag);
					   break;
				case '6' : counter = counter%3;
					   if(counter == 0)
						counter = 3;
					   decode(counter,108,flag);
					   break;
				case '7' : counter = counter%4;
					   if(counter == 0)
						counter = 4;
					   decode(counter,111,flag);
					   break;
				case '8' : counter = counter%3;
					   if(counter == 0)
						counter = 3;
					   decode(counter,115,flag);
					   break;
				case '9' : counter = counter%4;
					   if(counter == 0)
						counter = 4;
					   decode(counter,118,flag);
					   break;
			}
		}
		printf("\nDo you want to decode another message (y/n):");
		scanf("%s",&ans);
	}while(ans == 'y' || ans == 'Y');
	return 0;
}