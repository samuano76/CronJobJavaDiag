


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

Valorizzare ogni manifest con il namespace target al post di <namespace>
Il namespace target dovrà essere lo stesso del workload da analizzare.
Nel comando da eseguire all'interno del cronjob dovrà essere indicato il pod target dell'analisi.

Il cronjob attuale riporta un esempio di esecuzione con jcmd, ma questo può essere sostituito con qualsiasi altro tool presente all'interno della ubi8 in esecuzione.

- oc exec ex-aao-ss-0 -n amqbroker -- jcmd 1 Thread.print > /tmp/Thread

Nel comando vengono indicati il pod target (ex-aaa-ss-0), il tool (jcmd) e infine il path in cui depositare l'output (/tmp)


Installazione CronJobJavaDiag

Eseguire questo comando per creare gli oggetti attraverso kustomize ( eseguire dal path superiore rispetto la dir CronJobJavaDiag)

- oc create -k CronJobJavaDiag

Acceedere al pod ubi8 per verificare l'output dei tools diagnostici esegiti dal cronjob 

- oc rsh ubi8

Gli output verranno depositati all'interno della /tmp
Una volta all'interno del pod verficare nel path /tmp

Se si desidera eseguire ulteriori tools disponibili nella ubi8, richiamarli all'interno del cronjob aggiungendoli o sostituendoli al comando attuamente utilizzato.
