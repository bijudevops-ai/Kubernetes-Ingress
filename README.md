# DNS setup example for a Flask CRUD application running in Minikube, using a free DNS provider (like nip.io or sslip.io) for local testing.
![image](https://github.com/user-attachments/assets/f5accbe9-405d-4731-8532-eef2bb2a5c36)


1. Run  below commands from powershell admin mode
2. minikube start
3. minikube addons enable ingress
4. minikube tunnel
5. Add ingress.yaml to project  ![image](https://github.com/user-attachments/assets/a2279f59-dd2a-4987-b88a-6df0f1233b2d)

6.   kubectl apply -f k8s/ingress.yaml
7.   kubectl describe ingress flask-crud-ingress  ![image](https://github.com/user-attachments/assets/f8071520-5a70-44ec-bd73-58fc5e9706a0)
8.   PS D:\Projects\Kubernetes\Flask-Postgress-K8S> kubectl get pods -n ingress-nginx
NAME                                       READY   STATUS      RESTARTS      AGE 
ingress-nginx-admission-create-lrp8h       0/1     Completed   0             115m
ingress-nginx-admission-patch-f4zmp        0/1     Completed   1             115m
ingress-nginx-controller-67c5cb88f-496p4   1/1     Running     2 (30m ago)   115m
PS D:\Projects\Kubernetes\Flask-Postgress-K8S>

9. ![image](https://github.com/user-attachments/assets/c0f4fe2d-9a08-4837-bb96-97e98523524f)
10. I faced few issues to map with Minikube IP, but I resolved it by running below command
11. PS D:\Projects\Kubernetes\Flask-Postgress-K8S> kubectl patch svc ingress-nginx-controller -n ingress-nginx -p '{"spec": {"type": "LoadBalancer"}}'  ![image](https://github.com/user-attachments/assets/78716a96-03cc-4a5a-a5a7-0fbab261297a)
12. Tested service using postman
    ![image](https://github.com/user-attachments/assets/01f304fb-1ce0-41ad-9787-9fec8b19d418)

13. Refer implementation Flask based API in below medium article  https://medium.com/@bijumathewt/kubernetes-for-beginners-flask-microservice-with-postgres-argo-cd-and-prometheus-94df202e606a


