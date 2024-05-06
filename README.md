# GLDR APIs
## SITES
#### Gets list of sites added to DSCC
GET /disaster-recovery/v1beta1/virtual-sites

Response:
```
{
    "items": [
        {
            "id": "9758fdb9-1be2-4b67-b2f0-f7f071124c85",
            "serialNumber": "b5243c5a-cc95-40fc-9323-88b951884e18",
            "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
            "name": "",
            "platformType": "",
            "networkAddress": "",
            "status": "ACTIVATING",
            "connected": false,
            "updatedAt": "2023-03-13T07:47:44.366986Z",
            "type": "virtual-site",
            "resourceUri": "/api/v1/virtual-sites/9758fdb9-1be2-4b67-b2f0-f7f071124c85",
            "generation": 1,
            "refreshedAt": "2023-03-13T07:47:45.547615Z",
            "createdAt": "2023-03-13T07:47:44.233091Z",
            "version": "10.0.10"
        }
    ],
    "limit": 20000,
    "offset": 0,
    "total": 1
}
```
#### Gets specific sites information
GET {{url}}/disaster-recovery/v1beta1/virtual-sites/{id}

Response:   
```
{
    "id": "9758fdb9-1be2-4b67-b2f0-f7f071124c85",
    "serialNumber": "b5243c5a-cc95-40fc-9323-88b951884e18",
    "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
    "name": "",
    "platformType": "",
    "networkAddress": "",
    "status": "ACTIVATING",
    "connected": false,
    "updatedAt": "2023-03-13T07:47:44.366986Z",
    "type": "virtual-site",
    "resourceUri": "/api/v1/virtual-sites/9758fdb9-1be2-4b67-b2f0-f7f071124c85",
    "generation": 1,
    "refreshedAt": "2023-03-13T07:47:45.547615Z",
    "createdAt": "2023-03-13T07:47:44.233091Z",
    "version": "10.0.10"
}
```
#### Add Site to DSCC
POST /disaster-recovery/v1beta1/virtual-sites

Body:
```
{
    "serialNumber":"{{serialNumber}}"
}
```
Response:
```
{
    "id": "96acb465-b663-4aba-90c8-0b022ccc3e06"
}
```
#### Refresh site
POST /disaster-recovery/v1beta1/virtual-sites/{id}/refresh

Response:
200 OK

#### Delete a site from DSCC
DELETE /disaster-recovery/v1beta1/virtual-sites/{id}

Response:
204 No Content

## VIRTUALIZATION
#### Get list of Virtual-machines for a specific Protection site ID (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/hypervisor-virtual-machines?siteId={siteId}

Response:
```
[
    {
        "lastUpdatedAt": "2023-07-23T07:32:42Z",
        "id": "5553e594-f868-5c60-8f77-d9431df1b0fb",
        "name": "qa_s4v5_dmy_eyalgad",
        "type": "virtual-machine",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "internalId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.vm-1230",
        "siteId": "0e930aa7-3b47-4da2-825b-cde9e08383f4",
        "isAgentInstalled": false,
        "protected": false,
        "virtualDisks": [
            {
                "id": "",
                "internalId": "scsi:0:0"
            },
            {
                "id": "",
                "internalId": "scsi:0:1"
            },
            {
                "id": "",
                "internalId": "scsi:0:2"
            }
        ],
        "networkAdapters": [
            {
                "networkDetails": {
                    "id": "",
                    "internalId": "Network adapter 1"
                }
            },
            {
                "networkDetails": {
                    "id": "",
                    "internalId": "Network adapter 2"
                }
            }
        ]
    }
]
```
#### Protection site ID as param Refresh virtual machines list
POST /disaster-recovery/v1alpha1/virtualization/hypervisor-virtual-machines/refresh

Body:
```
{
    "siteId":"{{ProtectedSiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/01955825-26e1-4130-aae3-2677d465e577"
}
```
#### Get a list of Hypervisor-host (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/hypervisor-hosts?siteId={siteId}

Response:
```
[
 {
        "lastUpdatedAt": "2023-07-23T07:36:46Z",
        "id": "a78daa49-00fe-3568-bed1-e88305233f8b",
        "name": "10.171.34.11",
        "type": "hypervisor-host",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "88a1703c-359e-4c0e-af66-45dd88c9fcc7",
        "internalId": "f46575fd-ad26-4b5a-b969-233dfaea0df8.host-464",
        "vraInstalled": false,
        "owningHostCluster": null,
        "associatedDatastoresClusters": null,
        "associatedDatastores": [
            {
                "id": "64b0c03a-f861-320e-a12f-21cdb7f217c4",
                "name": "inf_QANested1063_DS4",
                "owningDatastoreCluster": null
            },
            {
                "id": "d1e8bcee-9fc9-301a-987e-5f2a93e9a0cf",
                "name": "inf_QANested1063_DS5",
                "owningDatastoreCluster": null
            }
        ]
    }
]
```
#### Recovery site ID as param recovery site Refresh Hypervisor-host list
POST /disaster-recovery/v1alpha1/virtualization/hypervisor-hosts/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/e977ed03-ece3-4ed0-839b-a993725d4c4c"
}
```
#### Get a list of Hypervisor-clusters (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/hypervisor-clusters?siteId={siteId}

Response:
```
[
     {
        "lastUpdatedAt": "2023-07-23T07:36:47Z",
        "id": "6068d627-8fca-384e-928b-8fb1ecf8e92b",
        "name": "ClusterH125H126",
        "type": "hypervisor-cluster",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "88a1703c-359e-4c0e-af66-45dd88c9fcc7",
        "internalId": "f46575fd-ad26-4b5a-b969-233dfaea0df8.domain-c8",
        "associatedDatastoresClusters": [
            {
                "id": "e8361c91-017b-30d0-81c5-0816d7081ec2",
                "name": "DatastoreClusteH125H126"
            }
        ],
        "associatedDatastores": [
            {
                "id": "64b0c03a-f861-320e-a12f-21cdb7f217c4",
                "name": "inf_QANested1063_DS4",
                "owningDatastoreCluster": null
            },
            {
                "id": "8501b19c-4908-37c1-a0ec-d985eb4c0ac4",
                "name": "inf_QANest1063_DS3",
                "owningDatastoreCluster": {
                    "id": "e8361c91-017b-30d0-81c5-0816d7081ec2",
                    "name": "DatastoreClusteH125H126"
                }
            },
            {
                "id": "d1e8bcee-9fc9-301a-987e-5f2a93e9a0cf",
                "name": "inf_QANested1063_DS5",
                "owningDatastoreCluster": null
            },
            {
                "id": "ed40b6f7-ffd9-36fa-adc9-44c0830869ff",
                "name": "inf_QANest1063_DS2",
                "owningDatastoreCluster": {
                    "id": "e8361c91-017b-30d0-81c5-0816d7081ec2",
                    "name": "DatastoreClusteH125H126"
                }
            },
            {
                "id": "4893820e-db8b-3aa5-b5f7-9b668f60ee6e",
                "name": "inf_QANested1063_DS1",
                "owningDatastoreCluster": null
            }
        ],
        "associatedNetworks": [
            {
                "id": "3c4a4234-2813-3d8a-a3d3-86196c11bd2d",
                "name": "VM Network"
            },
            {
                "id": "d6de39d3-5a73-360b-9627-7f317814a480",
                "name": "TO 1710"
            }
        ]
    }
]
```
#### Recovery site ID as param recovery site Refresh Hypervisor-cluster list
POST /disaster-recovery/v1alpha1/virtualization/hypervisor-clusters/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/e5d2d1f7-f3c6-44cf-92f1-a2854b40dba7"
}
```
#### Get a list of hypervisor-datastores (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/hypervisor-datastores?siteId={siteId}

```
[
   {
        "lastUpdatedAt": "2023-07-23T07:46:47Z",
        "id": "64b0c03a-f861-320e-a12f-21cdb7f217c4",
        "name": "inf_QANested1063_DS4",
        "type": "hypervisor-datastore",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "88a1703c-359e-4c0e-af66-45dd88c9fcc7",
        "internalId": "f46575fd-ad26-4b5a-b969-233dfaea0df8.datastore-1037",
        "owningDatastoreCluster": null
    }
]
```
#### Recovery site ID as param recovery site Refresh hypervisor-datastores list
POST /disaster-recovery/v1alpha1/virtualization/hypervisor-datastores/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/3a02bf03-ebf7-42c7-81d6-656d28863730"
}
```
#### Get a list of hypervisor-networks (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/hypervisor-networks?siteId={siteId}

Response:
```
[
    {
        "lastUpdatedAt": "2023-07-23T07:42:45Z",
        "id": "0f1d14d7-cbf4-3af2-9589-37bdbbb61196",
        "name": "NET1_vr02_changed",
        "type": "hypervisor-network",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "0e930aa7-3b47-4da2-825b-cde9e08383f4",
        "internalId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.network-1172"
    }
]
```
#### Recovery site ID as param recovery siteRefresh hypervisor-networks list
POST /disaster-recovery/v1alpha1/virtualization/hypervisor-networks/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/a360908d-c407-45fb-9dee-6818b0d98c88"
}
```
#### Get a list of hypervisor-folders (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/hypervisor-folders?siteId={siteId}

Response:
```
[
    {
        "lastUpdatedAt": "2023-07-23T07:46:47Z",
        "id": "0bf8bbb6-beca-3ba0-9ec2-9b2a22f2d2c6",
        "name": "/",
        "type": "hypervisor-folder",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "88a1703c-359e-4c0e-af66-45dd88c9fcc7",
        "internalId": "f46575fd-ad26-4b5a-b969-233dfaea0df8.group-v4"
    }
]
```
#### Recovery site ID as param recovery siteRefresh hypervisor-folders list
POST /disaster-recovery/v1alpha1/virtualization/hypervisor-folders/refresh

Bosy:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/31f8dd6c-a924-4098-b4cb-a5d668bd51c1"
}
```
#### Get a list of hypervisor-datastore-clusters (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/hypervisor-datastore-clusters?siteId={siteId}

Response:
```
[
     {
        "lastUpdatedAt": "2023-07-23T07:42:44Z",
        "id": "a1f3b582-7d1c-3635-8935-d4f5398b3118",
        "name": "DatastoreClusterH100H122_changed",
        "type": "hypervisor-datastore-cluster",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "siteId": "0e930aa7-3b47-4da2-825b-cde9e08383f4",
        "internalId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.group-p417"
    }
]
```
#### Recovery site ID as param recovery siteRefresh hypervisor-datastore-clusters list
POST /disaster-recovery/v1alpha1/virtualization/hypervisor-datastore-clusters/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Get a list of csp-machine-instance (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/csp-machine-instances?siteId={siteId}

Response:
```
[
    {
        "lastUpdatedAt": "2023-07-23T07:32:42Z",
        "id": "5553e594-f868-5c60-8f77-d9431df1b0fb",
        "name": "qa_s4v5_dmy_eyalgad",
        "type": "csp-machine-instances",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "cspId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.vm-1230",
        "isAgentInstalled": false,
        "protected": false,
        "virtualDisks": [
            {
                "id": "",
                "internalId": "scsi:0:0"
            },
            {
                "id": "",
                "internalId": "scsi:0:1"
            },
            {
                "id": "",
                "internalId": "scsi:0:2"
            }
        ],
        "networkAdapters": [
            {
                "networkDetails": {
                    "id": "",
                    "internalId": "Network adapter 1"
                }
            },
            {
                "networkDetails": {
                    "id": "",
                    "internalId": "Network adapter 2"
                }
            }
        ]
    }
]
```
#### Recovery site ID as param recovery siteRefresh csp-machine-instances list
POST /disaster-recovery/v1alpha1/virtualization/csp-machine-instances/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Get a list of csp-security-groups (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/csp-security-groups?siteId={siteId}

Response:
```
[
     {
        "lastUpdatedAt": "2023-07-23T07:42:44Z",
        "id": "a1f3b582-7d1c-3635-8935-d4f5398b3118",
        "name": "DatastoreClusterH100H122_changed",
        "type": "csp-security-groups",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "cspId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.group-p417"
    }
]
```
#### Recovery site ID as param recovery siteRefresh csp-security-groups list
POST /disaster-recovery/v1alpha1/virtualization/csp-security-groups/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Get a list of csp-subnets (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/csp-subnets?siteId={siteId}

Response:
```
[
     {
        "lastUpdatedAt": "2023-07-23T07:42:44Z",
        "id": "a1f3b582-7d1c-3635-8935-d4f5398b3118",
        "name": "DatastoreClusterH100H122_changed",
        "type": "csp-subnets",
        "customerId": "fe0d3faa-ae9f-11ec-a437-ea9dc4f11500",
        "cspId": "0c363daf-b9fd-4647-b99e-50332d1a5ba6.group-p417"
        "virtualNetworkId": "0e9323a7-3b47-4da2-825b-cde9e08383f4"
        "ipRange": ""
    }
]
```
#### Recovery site ID as param recovery siteRefresh csp-subnets list
POST /disaster-recovery/v1alpha1/virtualization/csp-subnets/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Get a list of csp-vpcs (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/csp-vpcs?siteId={siteId}

Response:
```
[
    {
        "id": "ecaa9b14-8943-357a-b264-70191d4287b4",
        "name": "SG4",
        "type": "csp-vpcs",
        "lastUpdatedAt": "2022-06-14T13:12:36Z",
        "customerId": "ac535f94eaec11ecbabefab33ff4092c",
        "cspId": "02ed58e0-ad7b-4f35-ad5a-9d5fe4ab5017.group-p494"
    }
]
```
#### Recovery site ID as param recovery siteRefresh csp-vpcs list
POST /disaster-recovery/v1alpha1/virtualization/csp-vpcs/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Get a list of csp-machine-instance-types (remove everything after the question mark (including) - to get  for all customer sites)
GET /disaster-recovery/v1alpha1/virtualization/csp-machine-instance-types?siteId={siteId}

Response:
```
[
    {
        "type": "csp-machine-instance-types",
        "lastUpdatedAt": "2022-06-14T13:12:36Z",
        "customerId": "ac535f94eaec11ecbabefab33ff4092c",
        "vmInstanceType": "string",
        "description": "string"
        "vmSeries": "string"
        "isPremiumSupported": "boolean"
    }
]
```
#### Recovery site ID as param recovery siteRefresh csp-machine-instance-types list
POST /disaster-recovery/v1alpha1/virtualization/csp-machine-instance-types/refresh

Body:
```
{
    "siteId":"{{RecoverySiteIdentifier}}"
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
## Protection
#### Create Protection Group
POST /disaster-recovery/v1beta1/virtual-continuous-protection-groups

Body:
```
{
  "name":"PM_DEMO_LIOR10",
  "protectedSite": "{{ProtectedSiteIdentifier}}",
  "recoverySite": "{{RecoverySiteIdentifier}}",
  "history": {
                "configuredDays": 0,
                "unlimited": true,
                "configuredMaxSizeGb":"0"
            },
  "recoveryVcenter":{ 
    "host":"{{HostIdentifier}}",
    "cluster":"{{ClusterIdenitifier}}",
    "datastore":"{{DatastoreIdentifier}}",
    "datastoreCluster":"{{DatastoreClusterIdentifier}}",
    "folder":"{{FolderIdentifier}}",
    "network":"{{NetworkIdentifier}}",
    "testNetwork":"{{NetworkIdentifier}}",
"nicOverrides": [
          {
            "name": "<string>",
            "vmIdentifier": "string",
            "failover": {
              "ipConfig": {
                "staticIp": "<string>",
                "isDhcp": "<bool>",
                "subnetMask": "<string>",
                "gateway": "<string>",
                "primaryDns": "<string>",
                "secondaryDns": "<string>",
                "dnsSuffix": "<string>"
              },
              "networkId": "<uuid>",
              "shouldReplaceMacAddress": "<bool>"
            },
            "test": {
              "ipConfig": {
                "staticIp": "<string>",
                "isDhcp": "<bool>",
                "subnetMask": "<string>",
                "gateway": "<string>",
                "primaryDns": "<string>",
                "secondaryDns": "<string>",
                "dnsSuffix": "<string>"
              },
              "networkId": "<uuid>",
              "shouldReplaceMacAddress": "<bool>"
            }
          }
        ],
    },
    "recoveryAzure": {
        "settings": {
            "virtualnetwork": "<uuid>",
            "subnet": "<uuid>",
            "securityGroup": "<uuid>",
            "azureDiskType": "enum",
            "vmInstance": "string",
        },
        "testSettings": {
            "virtualnetwork": "<uuid>",
            "subnet": "<uuid>",
            "securityGroup": "<uuid>",
            "azureDiskType": "enum",
            "vmInstance": "string"
        },
        "nicOverrides": [
          {
            "name": "<string>",
            "vmIdentifier": "string",
            "failover": {
                "subnet": "<string>",
                "securityGroup": "<string>",
                "isPrimary": "<bool>",
                "ipAddress": "<string>",
            },
            "test": {
                "subnet": "<string>",
                "securityGroup": "<string>",
                "isPrimary": "<bool>",
                "ipAddress": "<string>",
            }
          }
        ]
    }
   "protectedEntities": {
                "items": [
                   {
                    "id": "e31b6c64-4224-5c98-a94f-a6b580e10eaf"
                   }
                 ]
    }

}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/e977ed03-ece3-4ed0-839b-a993725d4c4c"
}
```
#### Get all protection groups data
GET /disaster-recovery/v1beta1/virtual-continuous-protection-groups

Response:
```
{
    "items": [
        {
            "id": "de6e12e3-696b-4375-8787-3e5b6b7b5038",
            "status": "READY",
            "name": "4cluster",
            "protectedSite": {
                "id": "b036184b-8b90-4b0d-b05f-7128f724ef3e",
                "name": "MK ZVML4"
            },
            "recoverySite": {
                "id": "b036184b-8b90-4b0d-b05f-7128f724ef3e",
                "name": "MK ZVML4"
            },
            "history": {
                    "configuredDays": 0,
                    "unlimited": true,
                    "configuredMaxSizeGb": 0
            },
            "recoveryVcenter": {
                "host": "8f9e3662-3d78-338a-b9b0-6a5d1e445a83",
                "datastore": "7a62201b-a7fe-3817-8a47-af390e7dfe69",
                "cluster": "",
                "datastoreCluster": "",
                "folder": "fb07de53-eb63-318a-8345-99640f74a6b5",
                "network": "d81a880b-ac06-3689-9565-5440040d5378",
                "testNetwork": "d81a880b-ac06-3689-9565-5440040d5378" ,
                 "nicOverrides": [
                  {
                    "name": "<string>",
                    "vmIdentifier": "string",
                    "failover": {
                      "ipConfig": {
                        "staticIp": "<string>",
                        "isDhcp": "<bool>",
                        "subnetMask": "<string>",
                        "gateway": "<string>",
                        "primaryDns": "<string>",
                        "secondaryDns": "<string>",
                        "dnsSuffix": "<string>"
                      },
                      "networkId": "<uuid>",
                      "shouldReplaceMacAddress": "<bool>"
                    },
                    "test": {
                      "ipConfig": {
                        "staticIp": "<string>",
                        "isDhcp": "<bool>",
                        "subnetMask": "<string>",
                        "gateway": "<string>",
                        "primaryDns": "<string>",
                        "secondaryDns": "<string>",
                        "dnsSuffix": "<string>"
                      },
                      "networkId": "<uuid>",
                      "shouldReplaceMacAddress": "<bool>"
                    }
                  }
                ]
            }
            "protectedEntities": {
                "entityType": "CSP/VCENTER",
                "items": [
                   {
                    "id": "e31b6c64-4224-5c98-a94f-a6b580e10eaf"
                   }
                 ]
            }
            "type": "virtual-continuous-protection-group",
            "resourceUri": "/disaster-recovery/v1beta1/virtual-continuous-protection-groups/de6e12e3-696b-4375-8787-3e5b6b7b5038",
            "customerId": "8e2e3348-c176-11ed-8dc9-9a78dd92b82f",
            "generation": 14,
            "updatedAt": "2023-09-06T04:38:03.475607Z",
            "createdAt": "2023-09-05T15:32:33.770914Z"
        },
    ],
    "limit": 20000,
    "offset": 0,
    "total": 1
}
```
#### Get data for specific protection group
GET /disaster-recovery/v1beta1/virtual-continuous-protection-groups/{id}

Response:
```
{
    "id": "ea8b7d07-10f3-49cf-84a8-7d6f81f940b5",
    "status": "ready",
    "name": "vpg-4b99425",
    "protectedSite": {
        "id": "cfa2cc63-e43b-4f6e-82fb-b6737fce029b",
        "name": "accusamus"
    },
    "recoverySite": {
        "id": "cfa2cc63-e43b-4f6e-82fb-b6737fce029b",
        "name": "accusamus"
    },
    "history": {
         "configuredDays": 0,
         "unlimited": true,
         "configuredMaxSizeGb": 0
    },
    "protectedEntities": {
    "entityType": "CSP/VCENTER",
    "items": [
        {
            "id": "uuid"
        }
      ]
    },
    "recoveryVcenter": {
        "host": "5ecdbc67-0bd9-321f-8cc6-03fb2c2da6b7",
        "datastore": "be556441-a07f-3ad0-998f-4288a2f09ec2",
        "cluster": "",
        "datastoreCluster": "",
        "folder": "a4a37624-f274-30a2-b1e0-16e76e758ad9",
        "network": "e3965e6a-9c8f-3c6e-81ae-543bfe8d0e8f",
        "testNetwork": "e3965e6a-9c8f-3c6e-81ae-543bfe8d0e8f",
        "nicOverrides": [
          {
            "name": "<string>",
            "vmIdentifier": "string",
            "failover": {
              "ipConfig": {
                "staticIp": "<string>",
                "isDhcp": "<bool>",
                "subnetMask": "<string>",
                "gateway": "<string>",
                "primaryDns": "<string>",
                "secondaryDns": "<string>",
                "dnsSuffix": "<string>"
              },
              "networkId": "<uuid>",
              "shouldReplaceMacAddress": "<bool>"
            },
            "test": {
              "ipConfig": {
                "staticIp": "<string>",
                "isDhcp": "<bool>",
                "subnetMask": "<string>",
                "gateway": "<string>",
                "primaryDns": "<string>",
                "secondaryDns": "<string>",
                "dnsSuffix": "<string>"
              },
              "networkId": "<uuid>",
              "shouldReplaceMacAddress": "<bool>"
            }
          }
        ]
    },
    "recoveryAzure": {
        "settings": {
            "virtualnetwork": "<uuid>",
            "subnet": "<uuid>",
            "securityGroup": "<uuid>",
            "azureDiskType": "enum",
            "vmSeries": "string",
            "vmInstance": "string",
        }
        "testSettings": {
            "virtualnetwork": "<uuid>",
            "subnet": "<uuid>",
            "securityGroup": "<uuid>",
            "azureDiskType": "enum",
            "vmSeries": "string",
            "vmInstance": "string"
        },
      "nicOverrides": [
        {
            "name": "<string>",
            "vmIdentifier": "string",
            "failover": {
                "subnet": "<string>",
                "securityGroup": "<string>",
                "isPrimary": "<bool>",
                "ipAddress": "<string>",
            },
            "test": {
                "subnet": "<string>",
                "securityGroup": "<string>",
                "isPrimary": "<bool>",
                "ipAddress": "<string>",
            }
        }
      ]
    }
    "type": "virtual-continuous-protection-group",
    "resourceUri": "/disaster-recovery/v1beta1/virtual-continuous-protection-groups/95d4e310-39a1-11ed-8051-56e786f00957",
    "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
    "generation": 2,
    "updatedAt": "2023-03-13T08:11:21.489807Z",
    "createdAt": "2023-03-13T08:11:21.489807Z"
}
```
#### Refresh protection group data from ZVM
POST /disaster-recovery/v1beta1/virtual-continuous-protection-groups/refresh/

Response:
202 Accepted
#### Update VPG
PUT /disaster-recovery/v1beta1/virtual-continuous-protection-groups/{vpgId}

Body:
```
{
    "name": "S4EGS3_v1" ,
    "protectedEntities": {
    "items": [
      {
        "id": "uuid"
      }
    ]
  },
      "history": {
        "configuredDays": 0,
        "unlimited": true,
        "configuredMaxSizeGb": 0
    },
    "recoveryVcenter":{ 
        "host":"{{tmp_vpg_host}}",
        "cluster":"{{tmp_vpg_cluster}}",
        "datastore":"{{tmp_vpg_datastore}}",
        "datastoreCluster":"{{tmp_vpg_datastoreCluster}}",
        "folder":"{{tmp_vpg_folder}}",
        "network":"{{tmp_vpg_network}}",
        "testNetwork":"{{tmp_vpg_testNetwork}}"
         "nicOverrides": [
          {
            "name": "<string>",
            "vmIdentifier": "string",
            "failover": {
              "ipConfig": {
                "staticIp": "<string>",
                "isDhcp": "<bool>",
                "subnetMask": "<string>",
                "gateway": "<string>",
                "primaryDns": "<string>",
                "secondaryDns": "<string>",
                "dnsSuffix": "<string>"
              },
              "networkId": "<uuid>",
              "shouldReplaceMacAddress": "<bool>"
            },
            "test": {
              "ipConfig": {
                "staticIp": "<string>",
                "isDhcp": "<bool>",
                "subnetMask": "<string>",
                "gateway": "<string>",
                "primaryDns": "<string>",
                "secondaryDns": "<string>",
                "dnsSuffix": "<string>"
              },
              "networkId": "<uuid>",
              "shouldReplaceMacAddress": "<bool>"
            }
          }
        ]
    },
    "recoveryAzure": {
        "settings": {
            "virtualnetwork": "<uuid>",
            "subnet": "<uuid>",
            "securityGroup": "<uuid>",
            "azureDiskType": "enum",
            "vmInstance": "string",
        }
        "testSettings": {
            "virtualnetwork": "<uuid>",
            "subnet": "<uuid>",
            "securityGroup": "<uuid>",
            "azureDiskType": "enum",
            "vmInstance": "string"
        },
        "nicOverrides": [
          {
            "name": "<string>",
            "vmIdentifier": "string",
            "failover": {
                "subnet": "<string>",
                "securityGroup": "<string>",
                "isPrimary": "<bool>",
                "ipAddress": "<string>",
            },
            "test": {
                "subnet": "<string>",
                "securityGroup": "<string>",
                "isPrimary": "<bool>",
                "ipAddress": "<string>",
            }
          }
        ]
    }
   
    
    
}


```
Response:
```
{
    "taskUri": "/api/v1/tasks/87831e92-b402-4e92-b60f-4be8e995ceac"
}
```

#### Delete a protection group
DELETE /disaster-recovery/v1beta1/virtual-continuous-protection-groups/{{DSCC_VPG_UDID}}

Response:
```
{
    "taskUri": "/api/v1/tasks/e977ed03-ece3-4ed0-839b-a993725d4c4c"
}
```

## REPLICATION
#### Get all replication groups data
GET /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/

Response:
```
{
    "items": [
        {
            "id": "a1d7ed4d-8c0d-4876-80cd-dc17ed2569a8",
            "name": "vpg-71bf908",
            "slaStatus": "MEETING_SLA",
            "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
            "healthStatus": "OK",
            "rpo": {
                "configuredSeconds": 300,
                "actualSeconds": 5,
                "status": "OK"
            },
            "history": {
                "actualMinutes": 0,
                "actualSizeMb":0
            },
            "type": "virtual-continuous-protection-replica",
            "resourceUri": "/disaster-recovery/v1beta1/virtual-continuous-protection-replicas/a1d7ed4d-8c0d-4876-80cd-dc17ed2569a8",
            "generation": 2,
            "updatedAt": "2023-03-13T07:55:00.69804Z",
            "createdAt": "2023-03-13T07:55:00.413094Z"
        }
    ],
    "limit": 20000,
    "offset": 0,
    "total": 1
}
```
#### Get data for specific replication group
GET /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/{{DSCC_VPG_UDID}}

Response:
```
{
    "id": "a1d7ed4d-8c0d-4876-80cd-dc17ed2569a8",
    "name": "vpg-71bf908",
    "slaStatus": "MEETING_SLA",
    "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
    "healthStatus": "OK",
    "rpo": {
        "configuredSeconds": 300,
        "actualSeconds": 5,
        "status": "OK"
    },
    "history": {
        "actualMinutes": 0,
        "actualSizeMb": 0
    },
    "type": "virtual-continuous-protection-replica",
    "resourceUri": "/disaster-recovery/v1beta1/virtual-continuous-protection-replicas/virtual-continuous-protection-replicas/a1d7ed4d-8c0d-4876-80cd-dc17ed2569a8",
    "generation": 2,
    "updatedAt": "2023-03-13T07:55:00.69804Z",
    "createdAt": "2023-03-13T07:55:00.413094Z"
}
```
#### Get checkpoints for specific replica VPG
GET /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/:vpgid/checkpoints

Response:
```
Replications : Get checkpoints for specific replica VPG - response should be : 

{

    "items": [
        {

            "id": "31",

            "tag": "",

            "timestamp": "2023-07-24T10:41:43Z",

            "customerId": "26ddc1fa-2016-11ee-974b-eaee3c8a2752"

        }
    ],

    "limit": 20000,

    "offset": 0,

    "total": 30,

    "createdAt": "2023-07-24T10:41:47.126752Z",

    "updatedAt": "2023-07-24T10:41:47.126752Z",

    "refreshedAt": "2023-07-24T10:41:47.126752Z"

}
```
#### Refresh checkpoint data for specific vpg
POST /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/:vpgid/checkpoints/refresh

Response:
202 Accepted

#### Refresh replication data from ZVM
POST /disaster-recovery/v1beta1/virtual-continuous-protection-replicas/refresh

Body:
```
{    "recoverySiteId": "8c15b12c-818f-498a-bcb3-573088bc285b"}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```

## RECOVERY

#### Get all recovery groups data
GET /disaster-recovery/v1beta1/virtual-continuous-protection-recovery/

Response:
```
 {

    "items": [

        {

            "id": "505e224a-18ff-46ba-9ab3-562b5f8f2232",

            "name": "hjr6uy5u6",

            "type": "virtual-continuous-protection-recovery",

            "status": "READY",

            "customerId": "26ddc1fa-2016-11ee-974b-eaee3c8a2752",

            "actions": [

                {

                    "name": "test",

                    "enabled": true,

                    "reason": ""

                },

                {

                    "name": "stop",

                    "enabled": false,

                    "reason": ""

                },

                {

                    "name": "failover",

                    "enabled": true,

                    "reason": ""

                },

                {

                    "name": "move",

                    "enabled": false,

                    "reason": ""

                },

                {

                    "name": "rollback",

                    "enabled": false,

                    "reason": ""

                },

                {

                    "name": "commit",

                    "enabled": false,

                    "reason": ""

                }

            ],

            "resourceUri": "/disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/505e224a-18ff-46ba-9ab3-562b5f8f2232",

            "createdAt": "2023-07-24T10:39:09.141799Z",

            "updatedAt": "2023-07-24T10:39:09.141799Z",

            "generation": 1,

            "lastTestedAt": "",
            "recoveryArguments": {
                 "isReverseSettings": false
             }

        }

    ],

    "limit": 20000,

    "offset": 0,

    "total": 1

}
```
#### Get data for specific recovery group
GET /disaster-recovery/v1beta1/virtual-continuous-protection-recovery/{{DSCC_VPG_UDID}}

Response:
```
   {
    "id": "ea8b7d07-10f3-49cf-84a8-7d6f81f940b5",
    "name": "vpg-4b99425",
    "type": "virtual-continuous-protection-recovery",
    "status": "READY",
    "customerId": "95d4e310-39a1-11ed-8051-56e786f00957",
    "actions": [
        {
            "name": "test",
            "enabled": true,
            "reason": ""
        },
        {
            "name": "stop",
            "enabled": false,
            "reason": ""
        },
        {
            "name": "failover",
            "enabled": true,
            "reason": ""
        },
        {
            "name": "move",
            "enabled": false,
            "reason": ""
        },
        {
            "name": "rollback",
            "enabled": false,
            "reason": ""
        },
        {
            "name": "commit",
            "enabled": false,
            "reason": ""
        }
    ],
    "resourceUri": "/api/v1/virtual-continuous-protection-recoveries/ea8b7d07-10f3-49cf-84a8-7d6f81f940b5",
    "createdAt": "2023-03-13T08:11:40.975818Z",
    "updatedAt": "2023-03-13T08:11:40.975818Z",
    "generation": 1,
    "recoveryArguments": {
         "isReverseSettings": false
 }
}  
```
#### Initiate Failover Live Operation
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recovery/{{DSCC_VPG_UDID}}/Failover

Body:
```
{
    "checkpointIdentifier": "45d7324d-b880-41e8-8247-fc68efcdb752",
    "isReverseSettings": false
}
```

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Initiate Failover Live-Commit  Operation
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/:DsccVpgId/FailoverCommit

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Initiate Failover Live-Rollback Operation
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/:DsccVpgId/FailoverRollback

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Initiate Failover Test Operation
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/{{VpgId}}/FailoverTest

Body:
```
{
    "checkpointIdentifier": "45d7324d-b880-41e8-8247-fc68efcdb752"
}
```

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
#### Initiate Failover Test-Stop Operation
POST /disaster-recovery/v1beta1/virtual-continuous-protection-recoveries/{{VpgId}}/FailoverTestStop

Response:
```
{
    "taskUri": "/api/v1/tasks/0ea06a97-41d6-4b68-8eec-fc753de4eae7"
}
```
## REPORTS
#### post
POST /disaster-recovery/api/v1/virtual-continuous-protection-reports - with
Body :
```
{

"siteId":"{{dsccSiteId}}",

"reportType":"recovery",

"startDate":"2022-11-05T11:04:05Z",

"endDate":"2023-09-20T15:04:05Z",

"recoveryOperation":["FailoverTest","Failover"],

"protectionGroup":["{{wrkVPGID}}"],

"state":""

}
```


Response : Status 202 Accepted - body :
```
{

    "taskUri": "/api/v1/tasks/76730514-af9e-4913-b3f2-75db02e1988f"

}
```

#### Get
GET /disaster-recovery/api/v1/virtual-continuous-protection-reports


Response : status 200 OK - body :
```
[

    {

        "id": "02243f39-2b1c-4f8d-b040-556789bbb198",

        "timeCreated": "2023-06-01T05:52:50.739817Z",

        "downloaded": false

    }
]

```
#### Get
GET /disaster-recovery/api/v1/virtual-continuous-protection-reports/:repID

Response:
```
<FILE>
```


## HOSTS
#### GET Host data
GET /disaster-recovery/v1beta1/virtual-continuous-host-protectors/

Response:
```
{
    "items":
    [
        {
            "id": "d7cf09d2-16db-35e3-b552-e43dcfe4d974",
            "customerId": "d293d71c-0b4b-11ee-ab1f-9a4e6a06796a",
            "address": "soluta",
            "clusterId": "",
            "version": "",
            "associatedSite": {
                "id": "a54a5a61-2cc6-42cc-8468-8094d0595326",
                "resourceUri": "/disaster-recovery/v1beta1/virtual-sites/a54a5a61-2cc6-42cc-8468-8094d0595326"
            },
            "associatedVra": {
                "name": "Z-VRA-soluta",
                "ipAddress": "86.132.122.254",
                "version": "8.0.10",
                "status": "READY"
            },
            "vraConfiguration": {
                "network": "37e1c5a5-2f9f-3be6-b786-dab1885ed62f",
                "datastore": "52353a60-1b30-3a8a-9f4b-f6faa60333d2",
                "setHostPassword": false,
                "ipType": "Static",
                "ipAddress": "10.171.39.14",
                "subnetMask": "255.255.240.0",
                "defaultGateway": "10.171.47.254",
                "memoryInGb": 3,
                "numOfVcpus": 1
            },
            "createdAt": "2023-11-09T10:32:30.441178Z",
            "updatedAt": "2023-11-09T10:32:36.241597Z",
            "refreshedAt": "2023-11-09T10:41:23.770379Z",
            "type": "virtual-continuous-host-protector",
            "resourceUri": "/disaster-recovery/v1beta1/virtual-continuous-host-protectors/d7cf09d2-16db-35e3-b552-e43dcfe4d974",
            "generation": 3
        }
    ],
    "count": 1,
    "offset": 0,
    "total": 1
}
```

#### GET Cluster Data
GET /disaster-recovery/v1beta1/virtual-continuous-cluster-protectors/

Response:
```
{
    "items": [
        {
            "id": "4a0c21ea-cb8d-3132-a9c5-69b6fbf8709d",
            "customerId": "d293d71c-0b4b-11ee-ab1f-9a4e6a06796a",
            "name": "sed",
            "associatedSite": {
                "id": "09abb7ba-8d22-417e-afdc-be5155d08793",
                "resourceUri": "/disaster-recovery/v1beta1/virtual-sites/09abb7ba-8d22-417e-afdc-be5155d08793"
            },
            "defaultVraConfiguration": {
                "network": "aebb692a-834e-3a15-a734-f6674e40b44e",
                "datastore": "61463f8f-1dc1-3d2e-a6d0-f622bf0e82aa",
                "setHostPassword": false,
                "ipType": "Static",
                "ipRangeStart": "1.1.1.1",
                "ipRangeEnd": "1.1.1.3",
                "subnetMask": "255.255.240.0",
                "defaultGateway": "1.1.1.254",
                "memoryInGb": 3,
                "numOfVcpus": 1
            },
            "createdAt": "2023-12-05T12:11:32.280046Z",
            "updatedAt": "2023-12-05T12:15:39.504083Z",
            "refreshedAt": "2023-12-05T12:15:39.504083Z",
            "type": "virtual-continuous-cluster-protector",
            "resourceUri": "/disaster-recovery/v1beta1/virtual-continuous-cluster-protectors/4a0c21ea-cb8d-3132-a9c5-69b6fbf8709d",
            "generation": 2
        }
    ],
    "count": 1,
    "offset": 0,
    "total": 1
}
```

#### Deploy VRA (Host)
POST /disaster-recovery/v1beta1/virtual-continuous-host-protectors/{hostID}/deploy

Body:
```
{
    "network": "c65d935a-9a6c-335e-a01a-48f55012701e",
    "datastore": "1a789dda-3b60-307d-8f77-e3c3d9ab28cd",
    "setHostPassword": true,
    "hostRootPassword": "Password123", --> not mandatory and depend on the set above 
    "ipType": "Static",
    "ipAddress": "10.171.11.27",
    "subnetMask": "255.255.240.0",
    "defaultGateway": "10.171.15.254",
    "memoryInGb": 3,
    "numOfVcpus": 1
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/27126c1a-4fc9-4f6b-9a67-373567f70e73"
}
```

#### Deploy VRA (Cluster)
POST /disaster-recovery/v1beta1/virtual-continuous-cluster-protectors/{clusterID}/deploy

Body:
```
{
    "network": "uuid",
    "datastore": "uuid",
    "setHostPassword": "bool",
    "hostRootPassword": "string", 
    "ipType": "string",--> Static
    "ipRangeStart": "string",
    "ipRangeEnd": "string",
    "subnetMask": "string",
    "defaultGateway": "string",
    "setAsDefaultConfiguration": "bool",
    "memoryInGb": 3,
    "numOfVcpus": 1
}
```
Response:
```
{
    "taskUri": "/api/v1/tasks/1d58c8ab-a318-4591-9b48-b8909c2dff7d"
}
```

#### Edit VRA (Host)
PUT /disaster-recovery/v1beta1/virtual-continuous-host-protectors/{hostID}

Body:
```
{
    "setHostPassword": "bool",
    "hostRootPassword": "string",
    "ipType": "string",--> Static,
    "ipAddress": "string",
    "subnetMask": "string",
    "defaultGateway": "string",
    "memoryInGb": 3,
    "numOfVcpus": 1
}
```

Response:
```
{
    "taskUri": "/api/v1/tasks/e63b3f81-5ada-40b5-82ad-420af30715ed"
}
```


#### Delete VRA (Host)
POST /disaster-recovery/v1beta1/virtual-continuous-host-protectors/{hostID}/remove

Response:
```
{
    "taskUri": "/api/v1/tasks/5d3c8ed0-e8cb-406a-996f-0518493edc2e"
}
```

#### Delete VRA (Cluster)
POST /disaster-recovery/v1beta1/virtual-continuous-cluster-protectors/{clusterID}/remove

Response:
```
{
    "taskUri": "/api/v1/tasks/4c538768-86b2-4196-8352-06f1bf06edf6"
}
```

#### Upgrade VRA (Host)
POST /disaster-recovery/v1beta1/virtual-continuous-host-protectors/{hostID}/upgrade

Response:
```
{
    "taskUri": "/api/v1/tasks/040eee1f-7930-445a-916a-d484a249fbea"
}
```

#### Upgrade VRA (Cluster)
POST /disaster-recovery/v1beta1/virtual-continuous-cluster-protectors/{clusterID}/upgrade

Response:
```
{
    "taskUri": "/api/v1/tasks/52a54a16-e748-4f84-b4c6-62afca249447"
}
```

#### Refresh
POST /disaster-recovery/v1beta1/virtual-continuous-host-protectors/refresh

Body:
```
{
    "siteId":"512b5370-26e5-42f3-b21d-398db98de4bd"
}
```

