# notification_service_kubernetes

helm repo add external-dns https://kubernetes-sigs.github.io/external-dns/

helm upgrade --install external-dns external-dns/external-dns --values values.yaml

<!-- helm install external-dns external-dns/external-dns -n kube-system --set clusterName=morgan_eks_cluster --set serviceAccount.create=false --set serviceAccount.name=ebs-external-dns-csi -->

helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=morgan_eks_cluster --set serviceAccount.create=false --set serviceAccount.name=aws-alb-controller

<!-- helm upgrade -i aws-load-balancer-controller eks/aws-load-balancer-controller --set clusterName=morgan_eks_cluster --set serviceAccount.create=false --set region=eu-west-2 --set vpcId=vpc-0d0dd8e9ed97fca5c --set serviceAccount.name=aws-alb-controller -n kube-system -->

helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=<cluster-name> --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
