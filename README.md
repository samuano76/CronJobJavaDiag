Di seguito la struttura degli oggeti che vengono create attraverso kustomize.


|-- CronJobJavaDiag
|   |-- README.md
|   |-- cronJob.yaml
|   |-- kustomization.yaml
|   |-- pvc.yaml
|   |-- role.yaml
|   |-- roleBinding.yaml
|   |-- serviceAccount.yaml
|   `-- ubi8.yaml

Valorizzare i manifest con il namespace target.

Eseguire questo comando per creare gli oggetti attraverso kustomize 

- oc create -k CronJobJavaDiag

Acceedere al pod ubi8 per verificare l'output dei tools diagnostici esegiti dal cronjob oc rsh ubi8

Gli output verranno depositati all'interno della /tmp

Se si desidera eseguire ulteriori tools disponibili nella ubi8, richiamarli all'interno del cronjob aggiungendoli o sostituendoli al comando attuamente utilizzato.
