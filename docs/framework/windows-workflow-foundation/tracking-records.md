---
title: Controlando registros
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: 46b52f6b774d1d692c0e7dec400d369428a9607e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699845"
---
# <a name="tracking-records"></a>Controlando registros
O tempo de execução de fluxo de trabalho é instrumentado para emitir registros de controle para siga a execução de uma instância de fluxo de trabalho.  
  
## <a name="tracking-records"></a>Controlando registros  
 A tabela a seguir detalha os registros de rastreamento que o tempo de execução de fluxo de trabalho se emite.  
  
|Controlando o registro|Descrição|  
|---------------------|-----------------|  
|Registros de ciclo de vida de fluxo de trabalho|Emitido durante vários estágios do ciclo de vida de instância de fluxo de trabalho. Por exemplo, um registro é emitida quando o fluxo de trabalho inicia ou termina.|  
|Registros de ciclo de vida de atividades|Detalha a execução da atividade. Esses registros indicam o estado de uma atividade de fluxo de trabalho como quando uma atividade é agendada, quando a atividade concluir, ou quando ocorre uma falha.|  
|Registros de ressunção do indexador|Emitido sempre que um marcador em uma instância de fluxo de trabalho que é.|  
|Registros de rastreamento personalizadas|Um autor de fluxo de trabalho pode criar registros personalizados de rastreamento e emitir os dentro de uma atividade personalizado.|  
  
 Todos os registros relacionados acompanhamento- emissores de tempo de execução de WF derivam da classe base <xref:System.Activities.Tracking.TrackingRecord>, que contém a comum definida de dados. Controlando registros mostrar o ciclo de vida para um fluxo de trabalho simples. Cada registro de rastreamento contém detalhes sobre o evento associado de rastreamento, como <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>, e o específico de informações adicionais para o tipo de registro de rastreamento.  
  
 Os seguintes tipos de objetos de <xref:System.Activities.Tracking.TrackingRecord> são emitidas em tempo de execução de fluxo de trabalho:  
  
- **WorkflowInstanceRecord** - este <xref:System.Activities.Tracking.TrackingRecord> descreve o ciclo de vida da instância do fluxo de trabalho. Por exemplo, um registro é emitida quando inicia o fluxo de trabalho ou terminar, e contém o estado da instância de fluxo de trabalho. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
- **WorkflowInstanceAbortedRecord** - este <xref:System.Activities.Tracking.TrackingRecord> é emitido quando uma instância de fluxo de trabalho será anulada. O registro contém a razão para a instância de fluxo de trabalho que está sendo aborted. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
- **WorkflowInstanceUnhandledExceptionRecord** - este <xref:System.Activities.Tracking.TrackingRecord> é emitida se uma exceção ocorre na instância do fluxo de trabalho e não é tratada por nenhuma atividade. O registro contém os detalhes de exceção. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
- **WorkflowInstanceSuspendedRecord** - este <xref:System.Activities.Tracking.TrackingRecord> é emitido sempre que uma instância de fluxo de trabalho é suspensa. O registro contém a razão para a instância de fluxo de trabalho que está sendo suspendida. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
- **WorkflowInstanceTerminatedRecord** - este <xref:System.Activities.Tracking.TrackingRecord> é emitido sempre que uma instância de fluxo de trabalho é encerrada. O registro contém a razão para a instância de fluxo de trabalho que está sendo finalizada. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
- **ActivityStateRecord** - este <xref:System.Activities.Tracking.TrackingRecord> é emitido quando uma atividade dentro de um fluxo de trabalho é executado. Esses registros indicam o estado da atividade dentro de instância de fluxo de trabalho. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
- **ActivityScheduledRecord** - este <xref:System.Activities.Tracking.TrackingRecord> é emitida quando agendas de atividade uma atividade filho. Esse registro contém detalhes para atividades pai (atividade de programação) e a atividade filho agendada. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
- **{1&gt;faultpropagationrecord&lt;1** - este <xref:System.Activities.Tracking.TrackingRecord> é emitido para cada manipulador que parece no registro até que ele seja manipulado. É usado para denotar o caminho que recebe uma falha na instância de fluxo de trabalho. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
- **{1&gt;cancelrequestedrecord&lt;1** - este <xref:System.Activities.Tracking.TrackingRecord> é emitido sempre que uma atividade tenta cancelar uma atividade filho. Esse registro contém detalhes para atividades a atividade pai e filho que está sendo cancelada. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
- **BookmarkResumptionRecord** - este <xref:System.Activities.Tracking.TrackingRecord> rastreia qualquer marcador que é continuado com êxito. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
- **CustomTrackingRecord** - este <xref:System.Activities.Tracking.TrackingRecord> é criado e emitido por um autor de fluxo de trabalho dentro de uma atividade de fluxo de trabalho personalizado. Os registros personalizados de rastreamento podem ser preenchidos com os dados a serem emitidos juntamente com os registros. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Por exemplo, pode haver uma atividade simples de <xref:System.Activities.Statements.Sequence> que contém uma operação de <xref:System.Activities.Statements.WriteLine> com os registros de rastreamento emissores na seguinte ordem:  
  
1. <xref:System.Activities.Tracking.WorkflowInstanceRecord> indica que o fluxo de trabalho está sendo.  
  
2. <xref:System.Activities.Tracking.ActivityScheduledRecord> indica que uma atividade foi agendada. Nesse caso é uma atividade de <xref:System.Activities.Statements.Sequence> .  
  
3. <xref:System.Activities.Tracking.ActivityScheduledRecord> representa a atividade de <xref:System.Activities.Statements.WriteLine> .  
  
4. Há dois registros de <xref:System.Activities.Tracking.ActivityStateRecord> que representam concluir de duas atividades.  
  
5. <xref:System.Activities.Tracking.WorkflowInstanceRecord> indica que o fluxo de trabalho está concluir.  
  
## <a name="see-also"></a>Consulte também

- [Monitoramento do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitoramento de aplicativos com a malha de aplicativos](https://go.microsoft.com/fwlink/?LinkId=201275)
