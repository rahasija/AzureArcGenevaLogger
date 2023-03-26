

----------------------------------------------------------------------------------------------------------------------------------------------------------------


Once AzureExtensionIdentity CR is created.
AzureClusterIdentityRequests will be created/renewed/deleted periodically by azure-arc agentry.
This CR  will contain reference to token which is of type opaque seecret.
This token can be used for authenticating cluster extension instance identity to geneva service endpoint.

------------------Getting Identity requests CR.-------------------------------
PS C:\Users\rahasija\k8sprojects\azm-operator-template> kubectl get azureclusteridentityrequests
NAME                                                                                AGE
identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d   77m
identity-request-7ffbf41f7d5feb1927669eb6e497a68d696faf113da12bc2f8643ae169118a78   77m

-------------------Getting DaemonSet pods--------------------------------------
PS C:\Users\rahasija\k8sprojects\azm-operator-template> kubectl get pods
NAME                     READY   STATUS    RESTARTS   AGE
geneva-daemonset-jpmr9   3/3     Running   0          77m

-----------------------Getting logs of msi adapter container.--------------------
PS C:\Users\rahasija\k8sprojects\azm-operator-template> kubectl logs geneva-daemonset-jpmr9 msi-adapter
I0203 11:06:51.150542       1 main.go:45] Successfully adding rules to iptables: iptables -t nat -A OUTPUT -p tcp -d %v --dport %v -j DNAT --to-destination %v:%v; iptables -t nat -A PREROUTING -p tcp -d %v --dport %v -j DNAT --to-destination %v:%v.169.254.169.25480127.0.0.18421169.254.169.25480127.0.0.18421
I0203 11:06:51.150767       1 readinessProbe.go:57] Starting Health Server
I0203 11:06:51.150805       1 types.go:26] Getting Status for Identity Object: [azuremigrate-partnername-system/identity-request-7ffbf41f7d5feb1927669eb6e497a68d696faf113da12bc2f8643ae169118a78]
E0203 11:06:51.247124       1 types.go:29] get token from status error: [azureclusteridentityrequests.clusterconfig.azure.com "identity-request-7ffbf41f7d5feb1927669eb6e497a68d696faf113da12bc2f8643ae169118a78" not found]
I0203 11:06:51.247144       1 types.go:26] init get token: is token nil? ([%!b(bool=true) %!b(bool=false)]) is token empty? (%!b(MISSING))
I0203 11:06:51.247155       1 types.go:26] Creating or renewing the identity Object: [identity-request-7ffbf41f7d5feb1927669eb6e497a68d696faf113da12bc2f8643ae169118a78 azuremigrate-partnername-system] , namespace: %!s(MISSING)
I0203 11:06:51.249551       1 types.go:26] Object Found : [false]
I0203 11:06:51.263026       1 types.go:26] Getting Status for Identity Object: [azuremigrate-partnername-system/identity-request-7ffbf41f7d5feb1927669eb6e497a68d696faf113da12bc2f8643ae169118a78]
E0203 11:06:51.349080       1 types.go:29] In clusterIdentityCRDInteraction [status not populated]
I0203 11:06:54.547944       1 types.go:26] Getting Status for Identity Object: [azuremigrate-partnername-system/identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d]
E0203 11:06:54.549945       1 types.go:29] get token from status error: [azureclusteridentityrequests.clusterconfig.azure.com "identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d" not found]
I0203 11:06:54.549977       1 types.go:26] init get token: is token nil? ([%!b(bool=true) %!b(bool=false)]) is token empty? (%!b(MISSING))
I0203 11:06:54.549988       1 types.go:26] Creating or renewing the identity Object: [identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d azuremigrate-partnername-system] , namespace: %!s(MISSING)
I0203 11:06:54.551771       1 types.go:26] Object Found : [false]
I0203 11:06:54.578566       1 types.go:26] Getting Status for Identity Object: [azuremigrate-partnername-system/identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d]
E0203 11:06:54.580579       1 types.go:29] In clusterIdentityCRDInteraction [status not populated]
I0203 11:07:04.051692       1 types.go:26] Getting Status for Identity Object: [azuremigrate-partnername-system/identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d]
E0203 11:07:04.057241       1 types.go:29] In clusterIdentityCRDInteraction [status not populated]
E0203 11:07:04.057282       1 types.go:29] get token from status error: [status not populated]
I0203 11:07:04.057291       1 types.go:26] init get token: is token nil? ([%!b(bool=true) %!b(bool=false)]) is token empty? (%!b(MISSING))
I0203 11:07:04.057304       1 types.go:26] Creating or renewing the identity Object: [identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d azuremigrate-partnername-system] , namespace: %!s(MISSING)

---------------------------------------Describing Identity request object-----------------------------
Since we have directly installed helm in kube system, token reference is set to null in below CR status.

PS C:\Users\rahasija\k8sprojects\azm-operator-template> kubectl describe azureclusteridentityrequests identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d
Name:         identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d
Namespace:    azuremigrate-partnername-system
Labels:       <none>
Annotations:  <none>
API Version:  clusterconfig.azure.com/v1beta1
Kind:         AzureClusterIdentityRequest
Metadata:
  Creation Timestamp:  2023-02-03T11:06:54Z
  Generation:          1
  Managed Fields:
    API Version:  clusterconfig.azure.com/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:spec:
        .:
        f:audience:
    Manager:      msi-adapter
    Operation:    Update
    Time:         2023-02-03T11:06:54Z
    API Version:  clusterconfig.azure.com/v1beta1
    Fields Type:  FieldsV1
    fieldsV1:
      f:status:
        .:
        f:tokenReference:
    Manager:         msi-adapter
    Operation:       Update
    Subresource:     status
    Time:            2023-02-03T11:07:04Z
  Resource Version:  432062
  UID:               106647bf-4269-4d89-8fdf-68e3772f8cac
Spec:
  Audience:  https://monitor.core.windows.net/
Status:
  Token Reference:
Events:  <none>

----------------------------------------------------------------------------------------------------------------------------------------------------------------


------------------------Adding token of scvmm in cluster identity-----------------------------------------------

rahasija@rahasijaMS:~/.kube$ kubectl edit-status AzureClusterIdentityRequest identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d
rahasija@rahasijaMS:~/.kube$ kubectl get  AzureClusterIdentityRequest identity-request-05e155524155ca6873c61d3772af056b04a936f99f0776287afdff30c04cd01d -o yaml

----------------------------Installing Cluster extension with system identity.------------------------------