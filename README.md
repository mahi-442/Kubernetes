# Kubernetes

aws s3 mb s3://practice.in.k8s --region ap-south-1

export KOPS_CLUSTER_NAME=practice.in
export KOPS_STATE_STORE=s3://practice.in.k8s

kops create cluster \
--state=${KOPS_STATE_STORE} \
--node-count=2 \
--master-size=t2.micro \
--node-size=t2.micro \
--zones=ap-south-1a,ap-south-1b \
--name=${KOPS_CLUSTER_NAME} \
--dns private \
--master-count 1

kops update cluster --yes --admin

kops validate cluster
