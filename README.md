# notification_service_kubernetes

helm repo add external-dns https://kubernetes-sigs.github.io/external-dns/

helm upgrade --install external-dns external-dns/external-dns --values values.yaml

<!-- helm install external-dns external-dns/external-dns -n kube-system --set clusterName=morgan_eks_cluster --set serviceAccount.create=false --set serviceAccount.name=ebs-external-dns-csi -->

helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=morgan_eks_cluster --set serviceAccount.create=false --set serviceAccount.name=aws-alb-controller

<!-- helm upgrade -i aws-load-balancer-controller eks/aws-load-balancer-controller --set clusterName=morgan_eks_cluster --set serviceAccount.create=false --set region=eu-west-2 --set vpcId=vpc-0d0dd8e9ed97fca5c --set serviceAccount.name=aws-alb-controller -n kube-system -->

1. aws eks update-kubeconfig --name "morgan_eks_cluster" --region "eu-west-2"
2. kubectl create namespace notification-service-app
3. helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=morgan_eks_cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
 - maybe wait a bit?
4. helm upgrade -i external-dns external-dns/external-dns --values values.yaml -n notification-service-app
5. kubectl apply -f ./

shutdwown:
1. kubectl delete namespace notification-service-app
2. kubectl delete deployment aws-load-balancer-controller -n kube-system 

notification-service-app
<!-- helm upgrade -i aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=morgan_eks_cluster --set serviceAccount.create=false --set serviceAccount.name=aws-alb-controller -->

<!-- helm upgrade -i external-dns external-dns/external-dns --values values.yaml -n notification-service-app -->
