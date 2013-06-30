#include<stdio.h>
#include<stdlib.h>

int main (void)
{
	int i,y[520][3],x=0,y1[26][3],y2[520][3],j,y3[26][3],g,a[20],b[20],h,g1,h1;
	FILE *pFile;
	
		//open database
	
	pFile = fopen("ccv_dat_bplane.txt", "r");
	for(i=0;i<520;i++)
	{
	 for(j=0;j<3;j++)
	 {
		fscanf(pFile,"%d*[ ]\n", &y[i][j]);

	 }
	}
	fclose(pFile);
	
		//open dataset of new image
	
	pFile = fopen("ccv_new_dat_bplane.txt", "r");
	for(i=0;i<26;i++)
	{
	 for(j=0;j<3;j++)
	 {
		fscanf(pFile,"%d*[ ]\n", &y1[i][j]);

	 }
	}
	fclose(pFile);
	
		//check diatance
	
	for(i=0;i<520;i++)
	{
				
			
			y2[i][1]=y[i][1]-y1[i%26][1];
			y2[i][2]=y[i][2]-y1[i%26][2];
			if(y2[i][1]<0)
				y2[i][1]=y2[i][1]*(-1);
			if(y2[i][2]<0)
				y2[i][2]=y2[i][2]*(-1);
			printf("%d   %d \n",y2[i][1],y2[i][2]);
		
		
	}
		//print distance in a file
	pFile = fopen("rank.txt", "w");
	for(i=0;i<520;i++)
		fprintf(pFile,"%d   %d   %d \n",y[i][0],y2[i][1],y2[i][2]);
	fclose(pFile);



	


		// free array
	
	for(i=0;i<26;i++)
	{
		y1[i][1]=0;
		y1[i][2]=0;
	}
	
		//sum of the coherent and inchorent part
	
	for(i=0;i<520;i++)
	{	
		y1[i/26][1]+=y2[i][1];
		y1[i/26][2]+=y2[i][2];
	}
	
		// sorting coherent part
	
	for(j=0;j<20;j++)
	{
		for(i=0;i<20;i++)
		{
			if (y1[i+1][1]>y1[i][1])
			{
				g=y1[i][1]; 		h=y1[i][0];
				y1[i][1]=y1[i+1][1]; 	y1[i][0]=y1[i+1][0]; 
				y1[i+1][1]=g; 		y1[i+1][0]=h;
				
			}
		}
	}
	
		//print rank_coherent in a file

	
	pFile = fopen("rank_alpha.txt", "w");
	for(i=0;i<20;i++)
	{
		fprintf(pFile,"%d   %d \n \n \n \n",y1[i][0],y1[i][1]);
	}
	fclose(pFile);
		
		
		// sorting incoherent part
	
	for(j=0;j<20;j++)
	{
		for(i=0;i<20;i++)
		{
			if (y1[i+1][2]>y1[i][2])
			{
				g1=y1[i][2]; 		h1=y1[i][0];
				y1[i][2]=y1[i+1][2]; 	y1[i][0]=y1[i+1][0]; 
				y1[i+1][2]=g1; 		y1[i+1][0]=h1;
				
			}
		}
	}
	
		//print rank_incoherent in a file

	
	pFile = fopen("rank_beta.txt", "w");
	for(i=0;i<20;i++)
	{
		fprintf(pFile,"%d   %d \n \n \n \n",y1[i][0],y1[i][2]);
	}
	fclose(pFile);
		
		


	
}





























