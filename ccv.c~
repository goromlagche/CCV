#include<stdio.h>
#include<stdlib.h>


int traverse(int ,int ,int ,int,int (*y)[256]);
char Assign(int );
int search(int ,int *,int);

int main()
{
	int x,x1,value1,a1=0,f1,g1,b,i,j,value,a=0,c=0,d=0,f,g;
	int alpha[26],beta[26],m=0,n=0;
	int *arr;
	int MaxAssign=50,MaxAssign1=50;
	int val[100],val1[100];				
	int y[256][256];
	int clr1[100],clr2[100],clr3[100],clr4[100],clr5[100];
	
	typedef struct 
	{
		int label;
		int color;
		int length;
	}ccv;
	 ccv *size;
	FILE *pFile;


							// Check For Number Of Loops
		
			//scan from database
    	pFile = fopen("database/619 bplane.txt", "r");

	for(i=0;i<255;i++)
	{
	 for(j=0;j<255;j++)
	 {
		fscanf(pFile,"%d*[ ]\n", &y[i][j]);

	 }

	}
	
			// coherent and incoherent part creation

	for(i=0;i<255;i++)
	{
	 for(j=0;j<255;j++)
	 {
		x=y[i][j];
		if (x>25)
		{
			continue;
		}
		else
		{
			 if (search(x,val,a))
		 {

		 	y[i][j]=MaxAssign+1;
			MaxAssign=MaxAssign+1;
			value=y[i][j];
			
			g=traverse(i,j,x,value,y);
			
		 }
		 	else
		 {
			val[a]=x;
			a=a+1;
			
			y[i][j]=x+25;
			value=y[i][j];
			g=traverse(i,j,x,value,y);

		 }
		}
		
		c++;
	 }
	}


	size=(ccv*)malloc(c*sizeof(ccv));
	arr=(int*)malloc(c*sizeof(int));
	
		//redo of scan for database
    	pFile = fopen("database/619 bplane.txt", "r");

	for(i=0;i<255;i++)
	{
	 for(j=0;j<255;j++)
	 {
		fscanf(pFile,"%d*[ ]\n", &y[i][j]);

	 }

	}
	fclose(pFile);

			//redo of coherent and noncoherent part creation and storing them into an struct
	for(i=0;i<255;i++)
	{
	 for(j=0;j<255;j++)
	 {
		x1=y[i][j];
		
		size[d].color=x1;
		if (x1>25)
		{
			continue;
		}
		else
		{
			 if (search(x1,val1,a1))
		 {

		 	y[i][j]=MaxAssign1+1;
			MaxAssign1=MaxAssign1+1;
			value1=y[i][j];
			
			f1=traverse(i,j,x1,value1,y);
			
		 }
		 	else
		 {
			val1[a1]=x1;
			a1=a1+1;
			
			y[i][j]=x1+25;
			value1=y[i][j];
			f1=traverse(i,j,x1,value1,y);

		 }
			
		}
		size[d].label=value1;
		arr[d]=f1;
		if(d==0)
			size[0].length=f1-g+1;
		else if(d>0)
			size[d].length=f1-arr[d-1]+1;
		
		d++;
	 }
	}
	
			//suming up the coherent and noncoherent part


	for(i=0;i<=25;i++)
	{
		alpha[i]=0;
		beta[i]=0;
	}

	for(i=0;i<c;i++)
	{
		for(j=0;j<=25;j++)
		{
			if (j==size[i].color)
			{
				if(size[i].length>4)
					alpha[size[i].color]+=size[i].length;
				else
					beta[size[i].color]+=size[i].length;	
					
			}
			
		}
		
	}
			// store it in a file
	pFile = fopen("ccv_new_dat_bplane.txt", "w+");

	for(i=0;i<=25;i++)
	{
		fprintf(pFile,"\n  %d   %d    %d  \n",i,alpha[i],beta[i]);
	}
	fclose(pFile);
	
}


int search(int x,int *z,int a)
{
	int i;
	for(i=0;i<=a;i++)
	{
		if (z[i]==x)
		{
			return 1;
	 	}
	}

	return 0;
}
int traverse(int i,int j,int x,int value,int (*y)[256])
{
	static int e=1;
	
	if((i+1)>=0&&(j>=0))
		if (x==y[i+1][j])
		{
			e++;
			y[i+1][j]=value;
			traverse(i+1,j,x,value,y);
			
		}
	if((i+1)>=0&&(j+1)>=0)
		if (x==y[i+1][j+1])
		{
			e++;
			y[i+1][j+1]=value;
			traverse(i+1,j+1,x,value,y);
			
		}
	if((i+1)>=0&&(j-1)>=0)
		if (x==y[i+1][j-1])
		{
			e++;
			y[i+1][j-1]=value;
			traverse(i+1,j-1,x,value,y);
			
		}
	if(i>=0&&(j+1)>=0)
		if (x==y[i][j+1])
		{
			e++;
			y[i][j+1]=value;
			traverse(i,j+1,x,value,y);
					
		}
	return (int)e;

}












