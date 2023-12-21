build une image docker dans api-gateway
la push sur duckerhub
./initialize_submission.sh
lancer cluster.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
docker-compose up
lancer api-gateway.yaml
