# roundrobin_withpriority
round robin scheduling with respect to priority.
#include<stdio.h>
#include<conio.h>
struct process
{
	int at,bt,priority,tat,wt,ct;
	char name[1000];
};
void print(struct process job)
{
	    printf("\n");
    	printf("%s  \t\t\t", job.name);
        printf("%d \t\t", job.at);
        printf("%d \t\t", job.bt);
        printf("%d \t", job.priority);
}
struct process insert()
{
	    struct process job;
	    printf("enter the process name \t :");
		scanf("%s",&job.name);
		printf("enter the arrival time  of process %s \t :",job.name);
		scanf("%d",&job.at);
		printf("enter the burst time of process  %s \t :",job.name);
		scanf("%d",&job.bt);	
		printf("enter the priority of the process %s \t :",job.name);
		scanf("%d",&job.priority);
		return job;
}
int main()
{
	int n,i,j;
	printf("enter number of process");
	scanf("%d",&n);
	struct process job[1000]={{}},temp;
		printf("hello %s",job[0].name);
	if(job[0].name==NULL)
	{
		printf("sandyyyyyyy");
	}

	for(i=0;i<n;i++)
	{
       job[i]=insert();
	}
	for(i=0;i<n;i++)
	{
		for(j=0;j<n-i-1;j++)
		{
			if(job[j].at>job[j+1].at)
			{
				temp=job[j];
				job[j]=job[i+1];
				job[i+1]=temp;
			}
			if(job[j].at==job[j+1].at)
			{
			   if(job[j].priority<job[j+1].priority)
			   {
			   	temp=job[j];
				job[j]=job[i+1];
				job[i+1]=temp;
			   }
			}
		}
	}

	for(i=0;i<n;i++)
	{
	print(job[i]);
	}
}
