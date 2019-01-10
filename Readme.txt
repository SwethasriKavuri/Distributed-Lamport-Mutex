1. Modified Lamport Algorithm -- lamu.da
2. Ans:
Assume that the request queue in both processes looks like [Tm=1:Pi=1,Tm=2:Pi=2,Tm=3:Pi=1]
When a Process Pi removing 'any' request, Tm:Pi , it is possible that a newer timestamped request message is deleted instead of the request for which the critical section wass executed.
In the above case if Tm=3:Pi=1 is removed by Process P1, and Process P2, when sent a release by Process P1, it deletes Tm=1:Pi=1
Now the request queue in both processes look like 
for P1 -> [Tm=1:Pi=1,Tm=2:Pi=2]
for P2 -> [Tm=2:Pi=2,Tm=3:Pi=1]
So, in such scenario, both the processes think that their is at the front of the queue. Hence they ll both execute critical section at the same time.This will cause a safety violation.

Consider a case where P1 removes Tm=1:Pi=1 and Process P2, when sent a release by Process P1 deletes Tm=3:Pi=1. In this case , both processes assume that the otherr process has request at the front of the queue. Hence they will both wait indefinitely causing a deadlock which is a liveness violation. 
3) I have created main.da file, that will run monitor process on the 3 algorithms
