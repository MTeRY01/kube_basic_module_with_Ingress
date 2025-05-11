# kube_basic_module

Cluster Configuration
# Backup existing kubeconfig
mv ~/.kube/config ~/.kube/config_backup

# Apply Terraform outputs
terraform output kube_config > ~/.kube/config
chmod 600 ~/.kube/config

# Verify access
kubectl get nodes

Deployment Management
# Force restart deployments (if patches fail)
kubectl rollout restart deployment -n trainer-portal --all

# Monitor rollout progress
kubectl rollout status deployment/backend-deploy -n trainer-portal

Ingress Verification
# Check ingress controller
kubectl get pods,svc -n ingress-nginx

# Get external IP
kubectl get ingress -n trainer-portal
