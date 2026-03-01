🚀 Apply It
kubectl apply -f deployment.yaml
kubectl get deployments
kubectl get rs
kubectl get pods

You’ll see:

1 Deployment

1 ReplicaSet (created automatically)

3 Pods

🧠 Architecture Flow
Deployment
    ↓
ReplicaSet
    ↓
Pods

Deployment manages ReplicaSet.
ReplicaSet manages Pods.

2️⃣ Rolling Update Demo

Now update the image version.

Edit image:

image: nginx:1.26

Apply:

kubectl apply -f deployment.yaml

Watch rollout:

kubectl rollout status deployment nginx-deployment

Watch pods live:

kubectl get pods -w

You will see:

New pod created

One old pod deleted

Controlled replacement

Zero downtime

That is rolling update working.

🔥 Check Deployment History
kubectl rollout history deployment nginx-deployment

You’ll see revision numbers.

3️⃣ Rollback Demo

Now roll back:

kubectl rollout undo deployment nginx-deployment

Or rollback to specific revision:

kubectl rollout undo deployment nginx-deployment --to-revision=1

Check:

kubectl rollout status deployment nginx-deployment

Pods revert to previous version.
<img width="923" height="1043" alt="Screenshot from 2026-03-01 22-39-01" src="https://github.com/user-attachments/assets/1cb31f43-6abc-4102-872b-9e9a8826391a" />

