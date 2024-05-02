# Mediawiki
Helm chart for mediawiki to deploy on kubernetes

# Pre-requisites 

1.) A Kubernetes cluster on cloud \
2.) Helm \
3.) kubectl \

versions installed on my machine \
kubernetes v1.28.5 \
helm v3.14.4 \
docker image > AKS-MediaWiki/mediawiki \

# How to run 

The repo Contains two charts . \

1.) mediawiki-chart runs mediawiki app \
2.) mediawiki-mariadb-chart runs database for mediawiki app \

To deploy, Run chart and execute below command \ 

helm install chartname /directory \
 
example > helm install mediawiki ./mediawiki-chart and helm install database ./mediawiki-mariadb-chart \
 
The application will be served on the external ip provided by load balancer . \


![image](https://github.com/abhisheksawant52/AKS-MediaWiki/assets/159427690/6beac6a4-442b-4167-b5af-24f68f14c326)

![image](https://github.com/abhisheksawant52/AKS-MediaWiki/assets/159427690/479d0d67-88af-43d7-826e-3c1d6169c1ef)


The database host will be available at database:3306. Set the db root password, username and db name from values file placed inside mediawiki-mariadb-chart . Use the same to configure mediawiki db details page . \

At the end of configuration , LocalSettings.php will be downloaded . The same file need to be placed at /var/www/html inside conatiner . This can be done by removing commented hostmount in deployment.yaml of mediawiki-chart and providing a hostmount path. \

![image](https://github.com/abhisheksawant52/AKS-MediaWiki/assets/159427690/e38c43cf-656a-4c21-a1b7-03317bb6e103)

![image](https://github.com/abhisheksawant52/AKS-MediaWiki/assets/159427690/0c465cf8-789b-4106-898e-d2579389a3a1)



