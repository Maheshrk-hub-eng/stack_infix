n=input()
stack1=[]
stack2=[]
a=[]
def find(p):
    if p=='+' or p=='-':
        return 1
    else:
        return 2
for i in range(len(n)):
    if (n[i]<='9'and n[i]>='0'):
        stack1.append(int(n[i]))
    else:
        p=find(n[i])
        if len(a)==0 or a[len(a)-1]<=p:
            stack2.append(n[i])
            a.append(p)
        else:
            v1=stack1.pop()
            v2=stack1.pop()
            w=stack2.pop()
            if w=='+':
                stack1.append(v2+v1)
            elif w=='-':
                stack1.append(v2-v1)
            elif w=='*':
                stack1.append(v2*v1)
            elif w=='/':
                stack1.append(v2//v1) 
            stack2.append(n[i]) 
            a.append(p)
while len(stack2)!=0:
    v1=stack1.pop()
    v2=stack1.pop()
    w=stack2.pop()
    if w=='+':
        stack1.append(v2+v1) 
    elif w=='-':
        stack1.append(v2-v1)
    elif w=='*':
        stack1.append(v2*v1)
    elif w=='/':
        stack1.append(v2//v1)  
          
print(*stack1)
