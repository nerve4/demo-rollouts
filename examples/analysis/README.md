# Rollouts: "Analysis" Deployment

Same play:
```
sed -i 's/demo:blue/demo:green/g' bluegreen_rollout.yaml
```

and at the same time:
```
kubectl get po --watch

NAME                             READY   STATUS    RESTARTS   AGE
demo-analysis-54b7f6675f-2zkpc   1/1     Running   0          2m58s
demo-analysis-54b7f6675f-ctxvw   1/1     Running   0          2m58s
demo-analysis-54b7f6675f-ncb8t   1/1     Running   0          2m58s
demo-analysis-67898c7758-2cx28   1/1     Running   0          4s
demo-analysis-54b7f6675f-ncb8t   1/1     Terminating   0          3m17s
demo-analysis-67898c7758-9pkrq   0/1     Pending       0          0s
demo-analysis-67898c7758-9pkrq   0/1     Pending       0          0s
demo-analysis-67898c7758-9pkrq   0/1     ContainerCreating   0          0s
demo-analysis-67898c7758-9pkrq   0/1     ContainerCreating   0          0s
demo-analysis-67898c7758-9pkrq   1/1     Running             0          2s
demo-analysis-54b7f6675f-2zkpc   1/1     Terminating         0          3m19s
demo-analysis-67898c7758-2l6nl   0/1     Pending             0          0s
demo-analysis-67898c7758-2l6nl   0/1     Pending             0          0s
demo-analysis-67898c7758-2l6nl   0/1     ContainerCreating   0          0s
demo-analysis-67898c7758-2l6nl   0/1     ContainerCreating   0          0s
demo-analysis-67898c7758-2l6nl   1/1     Running             0          2s
demo-analysis-54b7f6675f-ctxvw   1/1     Terminating         0          3m21s
demo-analysis-54b7f6675f-ncb8t   1/1     Terminating         0          3m27s
demo-analysis-54b7f6675f-ncb8t   0/1     Terminating         0          3m27s
demo-analysis-54b7f6675f-ncb8t   0/1     Terminating         0          3m28s
demo-analysis-54b7f6675f-ncb8t   0/1     Terminating         0          3m28s
demo-analysis-54b7f6675f-ncb8t   0/1     Terminating         0          3m28s
demo-analysis-54b7f6675f-2zkpc   1/1     Terminating         0          3m29s
demo-analysis-54b7f6675f-2zkpc   0/1     Terminating         0          3m29s
demo-analysis-54b7f6675f-2zkpc   0/1     Terminating         0          3m30s
demo-analysis-54b7f6675f-2zkpc   0/1     Terminating         0          3m30s
demo-analysis-54b7f6675f-2zkpc   0/1     Terminating         0          3m30s
demo-analysis-54b7f6675f-ctxvw   1/1     Terminating         0          3m31s
demo-analysis-54b7f6675f-ctxvw   0/1     Terminating         0          3m31s
demo-analysis-54b7f6675f-ctxvw   0/1     Terminating         0          3m32s
demo-analysis-54b7f6675f-ctxvw   0/1     Terminating         0          3m32s
demo-analysis-54b7f6675f-ctxvw   0/1     Terminating         0          3m32s
```

and the results:
```
kubectl get po

NAME                             READY   STATUS    RESTARTS   AGE
demo-analysis-67898c7758-2cx28   1/1     Running   0          55s
demo-analysis-67898c7758-2l6nl   1/1     Running   0          30s
demo-analysis-67898c7758-9pkrq   1/1     Running   0          32s
```