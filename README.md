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

![image](https://github.com/abhisheksawant52/AKS-MediaWiki/assets/159427690/66af0775-16d6-49e0-80ec-1a7bab309ce6)

![image](https://github.com/abhisheksawant52/AKS-MediaWiki/assets/159427690/659898d9-2964-4737-a430-6f531499415c)

The database host will be available at database:3306. Set the db root password, username and db name from values file placed inside mediawiki-mariadb-chart . Use the same to configure mediawiki db details page . \

At the end of configuration , LocalSettings.php will be downloaded . The same file need to be placed at /var/www/html inside conatiner . This can be done by removing commented hostmount in deployment.yaml of mediawiki-chart and providing a hostmount path. \

![image](https://github.com/abhisheksawant52/AKS-MediaWiki/assets/159427690/9571b8c9-7ac4-4146-9fdf-8e1fbbe7aa42)

![image](https://github.com/abhisheksawant52/AKS-MediaWiki/assets/159427690/3fc27bc1-dc6c-441d-9628-ccb671e57b1d)



