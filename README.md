# IBM APP CONNECT & OPENSHIFT PIPELINE (TEKTON) - INTEGRACI�N

## 1. CONTEXTO:
Este DEMO trabajado permite la INTEGRACI�N entre IBM APP CONNECT 12 & OPENSHIFT PIPELINE (TEKTON), con el objetivo de brindar una AUTOMATIZACI�N para despliegues de MICROSERVICIOS creados en ACE12, sobre: INTEGRATION SERVERs & INTEGRATION RUNTIMEs.


## 2. ARQUITECTURA:
![alt text](https://github.com/maktup/dummy-tekton-ace/blob/main/images/Arquitectura.jpg?raw=true)


## 3. DIRECTORIOS:
| NOMBRE |  DETALLE  |
| ------------ | ------------ |
| dummy_csm_microservice | consiste en el DIRECTORIO del proyecto de ACE12, con las FUENTES del MICROSERVICIO. |
| scripts | contiene los scripts YAML para ser instalados ORDENADAMENTE, para la construcci�n del flujo DEVOPs con TEKTON. |
| apis | contiene las APIs Swagger & OpenAPI que se pueden utilizar para construir el MICROSERVICIO en ACE12. |
| doc | contiene el DOCUMENTO paso a paso (PDF) para utilizar. |


## 4. SCRIPTs (YAML):
| NOMBRE | DETALLE |
| ------------ | ------------ |
| 0_dummy-appconnect-tekton-dashboard.yaml   |  Script YAML utilizado para la instalaci�n del DASHBOARD de TEKTON. |
| 1_dummy-appconnect-requerimientos.yaml  | Script YAML utilizado para la instalaci�n de TODOS los REQUERIMIENTOS previos al manejo de OPENSHIFT PIPELINE (acceso, seguridad, etc). |
| 2_dummy-appconnect-pipeline.yaml | Script YAML utilizado para la instalaci�n del RECURSO con la estructura de PIPELINE. |
| 3_dummy-appconnect-task.yaml | Script YAML utilizado para la instalaci�n de los RECURSOS de tipo TASK con la L�GICA de flujo (+ IMPORTANTE). |
| 4_dummy-appconnect-trigger.yaml  | Script YAML utilizado para la instalaci�n de los RECURSOS para la AUTOMATIZACI�N deldespliegue. |
| 5_dummy-appconect-ejecucion.yaml | Script YAML utilizado para el TEST por medio del PIPILINE RUN. |


## 5. INSTALACI�N:
El NAMESPACE BASE que se utilizar� para la DEMO ser�: dummy-tekton-appconnect.

$ oc create ns dummy-tekton-appconnect

**//Creaci�n REQUERIMIENTOS:**

$ oc create -f https://raw.githubusercontent.com/maktup/dummy-tekton-ace/main/scripts/1_dummy-appconnect-requerimientos.yaml

**//Creaci�n PERMISOS:**

$ oc adm policy add-scc-to-user privileged -z pipeline -n dummy-tekton-appconnect
$ oc adm policy add-role-to-user edit -z pipeline -n dummy-tekton-appconnect

**//Creaci�n de PIPELINE:**

$ oc create -f https://raw.githubusercontent.com/maktup/dummy-tekton-ace/main/scripts/2_dummy-appconnect-pipeline.yaml

**//Creaci�n de TASKs:**

$ oc create -f https://raw.githubusercontent.com/maktup/dummy-tekton-ace/main/scripts/3_dummy-appconnect-task.yaml

**//Creaci�n de TRIGGERs:**

$ oc create -f https://raw.githubusercontent.com/maktup/dummy-tekton-ace/main/scripts/4_dummy-appconnect-trigger.yaml


## 6. TESTING:
![alt text](https://github.com/maktup/dummy-tekton-ace/blob/main/images/Testing.jpg?raw=true)
