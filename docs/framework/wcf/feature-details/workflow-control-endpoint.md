---
title: Ponto de extremidade de controle de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: 40fec2902598daed178e070b02c1067c308507c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929708"
---
# <a name="workflow-control-endpoint"></a>Ponto de extremidade de controle de fluxo de trabalho
O ponto de extremidade de controle de fluxo de trabalho permite aos desenvolvedores chamar as operações de controle para controlar remotamente as instâncias de fluxo de trabalho hospedadas usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Esse recurso pode ser usado para executar operações de controle, como suspender, retomar e terminar de forma programática.  
  
> [!WARNING]
>  Se usar o ponto de extremidade de controle de fluxo de trabalho dentro de uma transação e o fluxo de trabalho que está sendo controlado contiver um <xref:System.Activities.Statements.Persist> atividade, a instância de fluxo de trabalho permanecerá lá até que a transação de tempo limite.  
  
## <a name="workflow-instance-management"></a>Gerenciamento de instância de fluxo de trabalho  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] define um contrato novo chamado <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Este contrato define uma série de controle de operações que permitem que você remotamente controlam instâncias de fluxo de trabalho hospedadas pelo <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> é um ponto de extremidade padrão que fornece uma implementação do <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contrato. <xref:System.ServiceModel.Activities.WorkflowControlClient> é uma classe que é usada para enviar as operações de controle para o <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 Instâncias de fluxo de trabalho podem estar em um dos seguintes estados:  
  
 Ativo  
 O estado de uma instância de fluxo de trabalho antes de atingir o estado concluído e quando não está no estado suspenso. Nesse estado, a instância de fluxo de trabalho é executado e processa mensagens do aplicativo.  
  
 Suspenso  
 Nesse estado, a instância de fluxo de trabalho não é executado, mesmo se houver atividades que não iniciaram a execução ou executaram parcialmente.  
  
 Concluído  
 O estado final de uma instância de fluxo de trabalho. A instância de fluxo de trabalho não pode executar depois de atingir o estado concluído.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 O <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> interface define um conjunto de operações de controle com as versões síncronas e assíncronas. As versões transacionadas exigem o uso de uma associação que reconhece a transação. A tabela a seguir lista as operações de controle com suporte.  
  
|Operação de controle|Descrição|  
|-----------------------|-----------------|  
|Anular|Modo forçado para a execução da instância do fluxo de trabalho.|  
|Cancelar|Faz a transição de uma instância de fluxo de trabalho do estado de suspensão ou Active Directory para o estado concluído.|  
|Executar|Fornece a oportunidade de executar a uma instância de fluxo de trabalho.|  
|Suspender|Faz a transição de uma instância de fluxo de trabalho de estado ativo para o estado suspenso.|  
|Terminate|Faz a transição de uma instância de fluxo de trabalho do estado de suspensão ou Active Directory para o estado concluído.|  
|Cancelamento de suspensão|Faz a transição de uma instância de fluxo de trabalho do estado suspenso para o estado ativo.|  
|TransactedCancel|Executa a operação de cancelamento em uma transação (flui do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
|TransactedRun|Executa a operação de execução em uma transação (flui do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
|TransactedSuspend|Executa a operação de suspensão em uma transação (flui do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
|TransactedTerminate|Executa a operação de encerramento sob uma transação (flui do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
|TransactedUnsuspend|Executa a operação Cancelar suspensão em uma transação (flui do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
  
 O <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contrato não fornece um meio para criar uma nova instância de fluxo de trabalho, apenas para gerenciar instâncias de fluxo de trabalho existentes. Para obter mais informações sobre como criar remotamente uma nova instância de fluxo de trabalho, consulte [extensibilidade de Host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> é um ponto de extremidade padrão com um contrato fixo, <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Quando adicionado a um <xref:System.ServiceModel.Activities.WorkflowServiceHost> da instância, esse ponto de extremidade pode então ser usado para enviar as operações de comando em qualquer instância de fluxo de trabalho hospedada pela instância de host. Para obter mais informações sobre pontos de extremidade padrão, consulte [pontos de extremidade padrão](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient> é uma classe que permite que você envie mensagens de controle para um <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> em um <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Ela contém um método para cada uma das operações compatíveis com o <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contrato, exceto para as operações transacionadas. <xref:System.ServiceModel.Activities.WorkflowControlClient> usa a transação de ambiente para determinar se uma operação transacionada deve ser usada.
