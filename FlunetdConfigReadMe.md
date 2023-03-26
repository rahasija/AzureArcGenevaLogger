# The log record from business logic pod will looks like this initially
"LogLevel":"INFO","Timestamp":"2023-02-08T13:38:19.517Z","Name":"controllers.VirtualMachine","Message":"resource not found, won't reconcile","resource":"azuremigrate-partnername/kthakwani"}

# the log record after tail command: time, tag,  reord
2023-02-09T12:58:50+05:30	azuremigrate.logfilename 	{"LogLevel":"INFO","Timestamp":"2023-02-08T09:32:45.559Z","Name":"setup","Message":"Using external API for PSSession","PowerShellSessionURL":"localhost:5000","ServiceName":"scvmmextension","ResourceType":"scvmmextension"}

# Kubernetes metadata plugin will transform into this
2023-02-09T12:58:50+05:30	azuremigrate.logfilename
{
  "log": "{\"LogLevel\":\"INFO\",\"Timestamp\":\"2023-02-08T14:49:46.744Z\",\"Name\":\"controllers.VirtualMachine\",\"Message\":\"resource not found, won't reconcile\",\"resource\":\"azuremigrate-partnername/rahasya\"}\n",
  "stream": "stderr",
  "docker": {
    "container_id": "4d9caded5d05b2093d3fcad4893718cd0c0cdcc31d546ae2b92a752d3c1da802"
  },
  "kubernetes": {
    "container_name": "vmm-operator",
    "namespace_name": "azure-vmmoperator",
    "pod_name": "vmm-operator-manager-554cc44d65-86xnz",
    "container_image": "azureprivatecloud.azurecr.io/operators/scvmm/eastus/stable/azure-scvmmoperator:1.0.885",
    "container_image_id": "docker-pullable://azureprivatecloud.azurecr.io/operators/scvmm/eastus/stable/azure-scvmmoperator@sha256:427cb898ff95aa8a8011b988b0e5c548017c2b152172701c448e802b501187a6",
    "pod_id": "5a59ba46-7920-4b3d-99d0-7cc1ef7262b0",
    "host": "docker-desktop",
    "labels": {
      "control-plane": "vmm-operator",
      "pod-template-hash": "554cc44d65"
    },
    "master_url": "https://10.96.0.1:443/api",
    "namespace_id": "dd99f0af-8bdc-4a5d-86bc-583e51579ea6",
    "namespace_labels": {
      "kubernetes_io/metadata_name": "azure-vmmoperator"
    }
  }
}


2023-02-13 15:00:47.398776000 +0530 DiagnosticEvent: 
{
  "level": "info",
  "ts": 1676215742.6387057,
  "msg": "Successfully done discovery of Seed Discovery Entity",
  "controller": "seeddiscoveryentity",
  "controllerGroup": "partnername.azuremigrate.microsoft.com",
  "controllerKind": "SeedDiscoveryEntity",
  "SeedDiscoveryEntity": {
    "name": "seeddiscoveryentity-sample3",
    "namespace": "azuremigrate-partnername"
  },
  "namespace": "azuremigrate-partnername",
  "name": "seeddiscoveryentity-sample3",
  "reconcileID": "a3303dfc-40f4-406d-b813-66d1dcda4f0c",
  "tenantId": "f686d426-8d16-42db-81b7-ab578e110ccd",
  "apiVersion": "2023-01-01-preview",
  "resourceId": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.offazurespringboot/springbootsites/DemoSite0105/springbootservers/testserver-4940",
  "cloudEnvironment": "AzureDogfood",
  "correlationId": "89c637c0-837e-4903-8bd1-12035eff03e0",
  "parentResourceId": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.offazurespringboot/springbootsites/DemoSite0105",
  "customLocation": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.extendedlocation/customlocations/migration-cl",
  "location": "West US",
  "operationId": "44444444-837e-4903-8bd1-12035eff03e0",
  "ServiceEventName": "NonTelemetryEvent",
  "createdBy": "2e19b344-065a-4e3a-a261-387af3256a57",
  "createdByType": "User",
  "createdAt": "2023-01-04T15:58:32.0572527Z",
  "resourceUID": "a2965c72-fe9c-4bf1-a019-f97fb025d042"
}

Error Event
2023-02-13 15:00:47.398827600 +0530 ErrorEvent: 
{
  "level": "error",
  "ts": 1676215742.6388516,
  "msg": "Failed to get the invalid object",
  "controller": "seeddiscoveryentity",
  "controllerGroup": "partnername.azuremigrate.microsoft.com",
  "controllerKind": "SeedDiscoveryEntity",
  "SeedDiscoveryEntity": {
    "name": "seeddiscoveryentity-sample3",
    "namespace": "azuremigrate-partnername"
  },
  "namespace": "azuremigrate-partnername",
  "name": "seeddiscoveryentity-sample3",
  "reconcileID": "a3303dfc-40f4-406d-b813-66d1dcda4f0c",
  "tenantId": "f686d426-8d16-42db-81b7-ab578e110ccd",
  "apiVersion": "2023-01-01-preview",
  "resourceId": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.offazurespringboot/springbootsites/DemoSite0105/springbootservers/testserver-4940",
  "cloudEnvironment": "AzureDogfood",
  "correlationId": "89c637c0-837e-4903-8bd1-12035eff03e0",
  "parentResourceId": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.offazurespringboot/springbootsites/DemoSite0105",
  "customLocation": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.extendedlocation/customlocations/migration-cl",
  "location": "West US",
  "operationId": "44444444-837e-4903-8bd1-12035eff03e0",
  "Namespace": "azuremigrate-partnername",
  "Name": "myinvalidresource",
  "error": "SeedDiscoveryEntity.partnername.azuremigrate.microsoft.com \"myinvalidresource\" not found",
  "stacktrace": "partnername.azuremigrate.microsoft.com/controllers.(*SeedDiscoveryEntityReconciler).Reconcile\n\t/workspace/controllers/seeddiscoveryentity_controller.go:90\nsigs.k8s.io/controller-runtime/pkg/internal/controller.(*Controller).Reconcile\n\t/go/pkg/mod/sigs.k8s.io/controller-runtime@v0.13.1/pkg/internal/controller/controller.go:121\nsigs.k8s.io/controller-runtime/pkg/internal/controller.(*Controller).reconcileHandler\n\t/go/pkg/mod/sigs.k8s.io/controller-runtime@v0.13.1/pkg/internal/controller/controller.go:320\nsigs.k8s.io/controller-runtime/pkg/internal/controller.(*Controller).processNextWorkItem\n\t/go/pkg/mod/sigs.k8s.io/controller-runtime@v0.13.1/pkg/internal/controller/controller.go:273\nsigs.k8s.io/controller-runtime/pkg/internal/controller.(*Controller).Start.func2.2\n\t/go/pkg/mod/sigs.k8s.io/controller-runtime@v0.13.1/pkg/internal/controller/controller.go:234",
  "ServiceEventName": "NonTelemetryEvent",
  "createdBy": "2e19b344-065a-4e3a-a261-387af3256a57",
  "createdByType": "User",
  "createdAt": "2023-01-04T15:58:32.0572527Z",
  "resourceUID": "a2965c72-fe9c-4bf1-a019-f97fb025d042"
}

Telemetry Event will look like
2023-02-13 15:00:47.396508200 +0530 TelemetryEvent:
{
  "level": "info",
  "ts": 1676215742.6389265,
  "msg": "Event Created",
  "controller": "seeddiscoveryentity",
  "controllerGroup": "partnername.azuremigrate.microsoft.com",
  "controllerKind": "SeedDiscoveryEntity",
  "SeedDiscoveryEntity": {
    "name": "seeddiscoveryentity-sample3",
    "namespace": "azuremigrate-partnername"
  },
  "namespace": "azuremigrate-partnername",
  "name": "seeddiscoveryentity-sample3",
  "reconcileID": "a3303dfc-40f4-406d-b813-66d1dcda4f0c",
  "tenantId": "f686d426-8d16-42db-81b7-ab578e110ccd",
  "apiVersion": "2023-01-01-preview",
  "resourceId": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.offazurespringboot/springbootsites/DemoSite0105/springbootservers/testserver-4940",
  "cloudEnvironment": "AzureDogfood",
  "correlationId": "89c637c0-837e-4903-8bd1-12035eff03e0",
  "parentResourceId": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.offazurespringboot/springbootsites/DemoSite0105",
  "customLocation": "/subscriptions/88bd94d4-7fb4-45cf-afb7-7047abf6aa26/resourceGroups/migration-demo/providers/microsoft.extendedlocation/customlocations/migration-cl",
  "location": "West US",
  "operationId": "44444444-837e-4903-8bd1-12035eff03e0",
  "ServiceEventName": "TelemetryEvent",
  "key1": "value1",
  "key2": "value2",
  "createdBy": "2e19b344-065a-4e3a-a261-387af3256a57",
  "createdByType": "User",
  "createdAt": "2023-01-04T15:58:32.0572527Z",
  "resourceUID": "a2965c72-fe9c-4bf1-a019-f97fb025d042"
}