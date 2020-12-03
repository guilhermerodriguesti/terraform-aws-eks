terraform init

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

brew install aws-iam-authenticator

terraform plan

terraform apply -auto-approve

aws-iam-authenticator help

kubectl version

aws eks update-kubeconfig --name cluster-eks-app

vim ~/.aws/credentials

vim ~/.aws/config

kubectl get nodes -o wide

kubectl get svc -o wide

kubectl get nodes -o wide

deploy-guestbook.sh

sh deploy-guestbook.sh

kubectl scale deploy frontend --replicas=6

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml

cat <<EOF | kubectl apply -f -\napiVersion: v1\nkind: ServiceAccount\nmetadata:\n  name: admin-user\n  namespace: kubernetes-dashboard\nEOF

cat <<EOF | kubectl apply -f -\napiVersion: rbac.authorization.k8s.io/v1\nkind: ClusterRoleBinding\nmetadata:\n  name: admin-user\nroleRef:\n  apiGroup: rbac.authorization.k8s.io\n  kind: ClusterRole\n  name: cluster-admin\nsubjects:\n- kind: ServiceAccount\n  name: admin-user\n  namespace: kubernetes-dashboard\nEOF

kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')

kubectl proxy
