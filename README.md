Descrizione


Di seguito gli oggetti che verranno creati attraverso kustomize.


- CronJobJavaDiag
  - README.md
  - cronJob.yaml
  - kustomization.yaml
  - pvc.yaml
  - role.yaml
  - roleBinding.yaml
  - serviceAccount.yaml
  - ubi8.yaml

CronJobJavaDiag dovrà essere in esecuzione all'interno dello stesso namespace del workload da analizzare.
Valorizzare di conseguenza ogni manifest con il namespace target al post del placeholder attualmente impostato.

Il cronjob attuale riporta un esempio di esecuzione con il tool jcmd, ma questo può essere sostituito con qualsiasi altro tool presente all'interno del pod in esecuzione.

- oc exec ex-aao-ss-0 -- jcmd 1 Thread.print > /tmp/Thread

Nel comando vengono indicati il pod target (ex-aaa-ss-0), il tool (jcmd) e infine il path in cui depositare l'output (/tmp).



Installazione CronJobJavaDiag


Eseguire questo comando per creare gli oggetti attraverso kustomize ( eseguire dal path superiore rispetto la dir CronJobJavaDiag).

- oc create -k CronJobJavaDiag

Acceedere al pod ubi8 per verificare l'output dei tools diagnostici esegiti dal cronjob.

- oc rsh ubi8

Gli output verranno depositati all'interno della /tmp.
Una volta all'interno del pod verficare nel path /tmp.

Se si desidera eseguire ulteriori tools disponibili nel pod, richiamarli all'interno del cronjob aggiungendoli o sostituendoli al comando attuamente utilizzato.

Eseguire questo comando per eliminare tutti gli oggetti:

- oc delete -k CronJobJavaDiag