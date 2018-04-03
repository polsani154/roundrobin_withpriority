# roundrobin_withpriority
round robin scheduling with respect to priority.
print("************* welcome to the roundrobin schduling****************");
print("enter number of processes ");
a=int(input());
job=[];
tq=2;
for i in range(0,a):
    p=[];
    print("enter proess name")
    p.append(input());
    print("enter "+ p[0]+" arrival time ") 
    p.append(int(input()));
    print("enter "+ p[0]+" burst time ")
    p.append(int(input()));
    job.append(p);
print("process name \tarrival time \tburst time")
for i in range(0,a):
    print(job[i][0]+"\t\t",job[i][1],"\t   \t",job[i][2])   
job.sort(key=lambda x:x[1])
print(job)
ready=[]
run=[]
ct=[]
dup=[]
time=0
n=tq
k=a
i=0
while (len(job)!=0 or len(ready)!=0 or len(run)!=0 and i<50):
    k=0
    print("hai")
    if(len(job)!=0):
        while(len(job)!=0 and job[0][1]==time):
            ready.append(job.pop(0))
            print(job)
            print("hai1")
    if(n==0 and run[0][2]!=0):
        ready.append(run[0])
        run.pop(0)
        print(run)
        print("hai42")
        n=tq
    print("this is ready at")
    print(ready)
    print("\n")
    while(len(run)==0 and len(ready)!=0):
        run.append(ready.pop(0))
        print(run)
        print(len(run))
                    
    if(len(run)!=0 and run[0][2]!=0):
        run[0][2]=run[0][2]-1
        print("hai4")
        n=n-1


    if(len(run)!=0 and run[0][2]==0):
        print("hai3")
        ct.append(run[0])
        ct[ct.index(run[0])].append(time+1)
        run.pop(0)
        n=tq
    time=time+1
    i=i+1
for i in range(0,a):
    for j in range(0,4):
        if(j!=2):
            print(ct[i][j])
            print("\t")
