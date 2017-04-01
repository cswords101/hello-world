# hello-world
Various code worked on during first year of computer science in NUIG

#include "stdafx.h"
#include "stdio.h"
#include "stdlib.h"
#define NUMACCOUNTS 15

int main()
{
	char IDs[NUMACCOUNTS][6];
	double balances[NUMACCOUNTS];
	int i = 0;
	double randomBalance;
	int numAccounts = 0;

	FILE * fptr;

	fptr = fopen( "c:\\users\\o_molloy\\numbers.txt", "w" );

	for (i=0;i<NUMACCOUNTS;i++)
	{
		randomBalance = rand() - 10000.00;
		fprintf(fptr, "%05d\t%10.2lf\n", i, randomBalance);
	}

	fclose(fptr);

	fptr =  fopen( "c:\\users\\o_molloy\\numbers.txt", "r" );

	i = 1;

	fscanf(fptr, "%s\t%lf\n", IDs[i], &balances[i]);
	printf("%s\t%10.2lf\n", IDs[i], balances[i]);
			
	i++;

	while (!feof(fptr))
	{
		fscanf(fptr, "%s\t%lf\n", IDs[i], &balances[i]);
		printf("%s\t%10.2lf\n", IDs[i], balances[i]);
		i++;
	}
	numAccounts = i;

	fclose(fptr);

	printf ("\n\nACCOUNTS WITH A NEGATIVE BALANCE\n");
	printf("------------------------------------------------\n");
	for(i=0;i<numAccounts; i++)
	{
		if (balances[i] < 0.0)
		{
			printf("%s\t%10.2lf\n", IDs[i], balances[i]);
		}
	}

	return 0;
}
