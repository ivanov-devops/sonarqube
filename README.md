## Usage
this repository is a fork from official repository
https://github.com/SonarSource/sonarqube

install git \
download the repository \
`git clone https://github.com/ivanov-devops/sonarqube.git`

edit the `values.yaml` to match your configuration



[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

  helm repo add sonarqube-dce https://ivanov-devops.github.io/sonarqube/
  or make your own Build: \
  `helm create sonarqube`
  `ls sonarqube`

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run `helm search repo
sonarqube` to see the charts.

you have to define

`JWT_SECRET=$(echo -n "your_secret" | openssl dgst -sha256 -hmac "your_key" -binary | base64)`
To install the sonarqube chart:
`helm install sonarqube sonarqubesonarqube --values sonarqube/values.yaml`

or use the default \
`
helm repo add sonarqube https://ivanov-devops.github.io/sonarqube/
helm repo update

kubectl create namespace sonarqube-dce --dry-run=client -o yaml | kubectl apply -f -
export JWT_SECRET=${{ secrets.JWT_SECRET }}
helm upgrade --install -n sonarqube-dce sonarqube sonarqube/sonarqube-dce --set ApplicationNodes.jwtSecret=$JWT_SECRET
`
To uninstall the chart:

    helm delete my-sonarqube
