## URLs for Docker Hub image
- https://hub.docker.com/repository/docker/ahi0925/sa-logic/general
- https://hub.docker.com/repository/docker/ahi0925/sa-webapp/general
- https://hub.docker.com/repository/docker/ahi0925/sa-frontend/general



## Steps to run Sentiment Analyser on Google Kubernetes Engine on GCP
0. Git clone https://github.com/rinormaloku/k8s-mastery
1. Build sa-logic docker
   ```
   build -f Dockerfile -t ahi0925/sa-logic .
   ```
2. Push sa-logic image to docker hub
   ```
   push ahi0925/sa-logic
   ```
3. Pull and tag sa-logic image to GCP and push it to GCP container registry
   ```
   docker pull ahi0925/sa-logic
   docker tag ahi0925/sa-logic gcr.io/starlit-water-413714/ahi0925/sa-logic
   gcr.io/starlit-water-413714/ahi0925/sa-logic
   ```
4. Create cluster
5. From sa-logic container on GCP, deploy and expose the service on the cluster
   
6. Build java webapp project to get jar mvn install
7. In sa-webapp Dockerfile, change SA_LOGIC_API_URL variable to the external IP of sa-logic-service from GCP ( find from Gateways, Services & Ingress )
   ```
   ENV SA_LOGIC_API_URL http://34.75.134.72:5000
   ```
8. Build sa-webapp docker
   ```
   build -f Dockerfile -t ahi0925/sa-webapp .
   ```
9. Push sa-webapp image to docker hub 
   ```
   push ahi0925/sa-webapp
   ```
10. Pull and tag sa-webapp image to GCP and push it to GCP container registry
    ```
    docker pull ahi0925/sa-webapp
    docker tag ahi0925/sa-webapp gcr.io/starlit-water-413714/ahi0925/sa-webapp
    gcr.io/starlit-water-413714/ahi0925/sa-webapp
    ```
11. From sa-webapp container on GCP, deploy and expose the service on the cluster
12. In sa-frontend App.js, change POST URL to the external IP of sa-webapp-service on GCP.
    ```
    http://35.243.242.241:8080/sentiment
    ```    
13. Build sa-frontend using yarn build
    ```
    yarn build
    ```
14. Build sa-fronted docker
    ```
    build -f Dockerfile -t ahi0925/sa-frontend .
    ```
15. Push sa-frontend image to docker hub 
    ```
    push ahi0925/sa-frontend
    ```
16. Pull and tag sa-frontend image to GCP and push it to GCP container registry
    ```
    docker pull ahi0925/sa-frontend
    docker tag ahi0925/sa-frontend gcr.io/starlit-water-413714/ahi0925/sa-frontend
    gcr.io/starlit-water-413714/ahi0925/sa-frontend
    ```
17.  From sa-webapp container on GCP, deploy and expose the service on the cluster
18.  Access the sa-frontend-service from Gateways, Services & Ingress


## demo & code walkthrough/explanation for changes 
https://drive.google.com/drive/folders/17u1VgasJYU12rTp1Q3q6CxIZ31JR5Kre?usp=drive_link
