---
title: Controlando registros
ms.date: 03/30/2017
ms.assetid: 51adbda3-bd8b-4892-a8ea-d343186472d2
ms.openlocfilehash: d59db7e4c90b3cffe523c89de093f58f3e520bde
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837604"
---
# <a name="tracking-records"></a>Controlando registros
O runtime de fluxo de trabalho é instrumentado para emitir registros de controle para siga a execução de uma instância de fluxo de trabalho.  
  
## <a name="tracking-records"></a>Controlando registros  
 A tabela a seguir detalha os registros de rastreamento que o runtime de fluxo de trabalho se emite.  
  
|Controlando o registro|Descrição|  
|---------------------|-----------------|  
|Registros de ciclo de vida de fluxo de trabalho|Emitido durante vários estágios do ciclo de vida de instância de fluxo de trabalho. Por exemplo, um registro é emitida quando o fluxo de trabalho inicia ou termina.|  
|Registros de ciclo de vida de atividades|Detalha a execução da atividade. Esses registros indicam o estado de uma atividade de fluxo de trabalho como quando uma atividade é agendada, quando a atividade concluir, ou quando ocorre uma falha.|  
|Registros de ressunção do indexador|Emitido sempre que um marcador em uma instância de fluxo de trabalho que é.|  
|Registros de rastreamento personalizadas|Um autor de fluxo de trabalho pode criar registros personalizados de rastreamento e emitir os dentro de uma atividade personalizado.|  
  
 Todos os registros relacionados acompanhamento- emissores de runtime de WF derivam da classe base <xref:System.Activities.Tracking.TrackingRecord>, que contém a comum definida de dados. Controlando registros mostrar o ciclo de vida para um fluxo de trabalho simples. Cada registro de rastreamento contém detalhes sobre o evento associado de rastreamento, como <xref:System.Activities.Tracking.TrackingRecord.InstanceId%2A>, <xref:System.Activities.Tracking.TrackingRecord.RecordNumber%2A>, e o específico de informações adicionais para o tipo de registro de rastreamento.  
  
 Os seguintes tipos de objetos de <xref:System.Activities.Tracking.TrackingRecord> são emitidas em runtime de fluxo de trabalho:  
  
- **WorkflowInstanceRecord** -este <xref:System.Activities.Tracking.TrackingRecord> descreve o ciclo de vida da instância de fluxo de trabalho. Por exemplo, um registro é emitida quando inicia o fluxo de trabalho ou terminar, e contém o estado da instância de fluxo de trabalho. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceRecord>.  
  
- **WorkflowInstanceAbortedRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> é emitida quando uma instância de fluxo de trabalho é anulada. O registro contém a razão para a instância de fluxo de trabalho que está sendo aborted. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>.  
  
- **WorkflowInstanceUnhandledExceptionRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> será emitida se ocorrer uma exceção na instância do fluxo de trabalho e não for manipulada por nenhuma atividade. O registro contém os detalhes de exceção. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>.  
  
- **WorkflowInstanceSuspendedRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> é emitida sempre que uma instância de fluxo de trabalho é suspensa. O registro contém a razão para a instância de fluxo de trabalho que está sendo suspendida. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>.  
  
- **WorkflowInstanceTerminatedRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> é emitida sempre que uma instância de fluxo de trabalho é encerrada. O registro contém a razão para a instância de fluxo de trabalho que está sendo finalizada. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>.  
  
- **ActivityStateRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> é emitida quando uma atividade em um fluxo de trabalho é executada. Esses registros indicam o estado da atividade dentro de instância de fluxo de trabalho. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.ActivityStateRecord>.  
  
- **ActivityScheduledRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> é emitida quando uma atividade agenda uma atividade filho. Esse registro contém detalhes para atividades pai (atividade de programação) e a atividade filho agendada. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.ActivityScheduledRecord>.  
  
- **FaultPropagationRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> é emitida para cada manipulador que examina o registro até que seja manipulado. É usado para denotar o caminho que recebe uma falha na instância de fluxo de trabalho. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.FaultPropagationRecord>.  
  
- **CancelRequestedRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> é emitida sempre que uma atividade tenta cancelar uma atividade filho. Esse registro contém detalhes para atividades a atividade pai e filho que está sendo cancelada. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.CancelRequestedRecord>.  
  
- **BookmarkResumptionRecord** -este <xref:System.Activities.Tracking.TrackingRecord> rastreia qualquer indicador retomado com êxito. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.BookmarkResumptionRecord>.  
  
- **CustomTrackingRecord** -essa <xref:System.Activities.Tracking.TrackingRecord> é criada e emitida por um autor de fluxo de trabalho dentro de uma atividade de fluxo de trabalho personalizada. Os registros personalizados de rastreamento podem ser preenchidos com os dados a serem emitidos juntamente com os registros. Os detalhes desse registro podem ser encontrados em <xref:System.Activities.Tracking.CustomTrackingRecord>.  
  
 Por exemplo, pode haver uma atividade simples de <xref:System.Activities.Statements.Sequence> que contém uma operação de <xref:System.Activities.Statements.WriteLine> com os registros de rastreamento emissores na seguinte ordem:  
  
1. <xref:System.Activities.Tracking.WorkflowInstanceRecord> indica que o fluxo de trabalho está sendo.  
  
2. <xref:System.Activities.Tracking.ActivityScheduledRecord> indica que uma atividade foi agendada. Nesse caso é uma atividade de <xref:System.Activities.Statements.Sequence> .  
  
3. <xref:System.Activities.Tracking.ActivityScheduledRecord> representa a atividade de <xref:System.Activities.Statements.WriteLine> .  
  
4. Há dois registros de <xref:System.Activities.Tracking.ActivityStateRecord> que representam concluir de duas atividades.  
  
5. <xref:System.Activities.Tracking.WorkflowInstanceRecord> indica que o fluxo de trabalho está concluir.  
  
## <a name="see-also"></a>Consulte também

- [Monitoramento do Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorando aplicativos com o app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
