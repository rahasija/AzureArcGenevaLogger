# AzureArcGenevaLogger
Azure ARC Geneva logger for untrusted environment

# Create helm and push it to ACR
In powershell 

cd reporoot/helm
$genevaloggerversion="03.25.1639"
$ACR_NAME="micrsoftazuremigratecontainerregistry"
$namespace="azure-"

rm .\azurearc-genevalogger*.tgz
helm package --version $genevaloggerversion --destination . helm

# helm uninstall azurearc-genevalogger
# helm install  azurearc-genevalogger azurearc-genevalogger-$genevaloggerversion.tgz  --create-namespace  --namespace=#namespace
# kubectl get pods
# kubectl logs 

# helm upgrade --install  azuremigrate-genevalogger .\azuremigrate-genevalogger-$genevaloggerversion.tgz  --create-namespace  --namespace=azuremigrate-partnername -f .\discovery-operator\samplehelmvalues.yaml

## Login to helm if not already done
 $USER_NAME="00000000-0000-0000-0000-000000000000"
 $PASSWORD=$(az acr login --name $ACR_NAME --expose-token --output tsv --query accessToken)
 helm registry login "$ACR_NAME.azurecr.io"  --username $USER_NAME  --password $PASSWORD

# pushing it to helm registry with helm 3.11 version
 helm push azurearc-genevalogger-$genevaloggerversion.tgz oci://micrsoftazuremigratecontainerregistry.azurecr.io/azurearc-genevalogger-repo
 
