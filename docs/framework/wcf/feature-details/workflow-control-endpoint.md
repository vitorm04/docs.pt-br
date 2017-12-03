---
title: Ponto de extremidade de controle de fluxo de trabalho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5894a8b5d4d0873a231927498a8d1e2c4e18afd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-control-endpoint"></a>Ponto de extremidade de controle de fluxo de trabalho
O ponto de extremidade de controle de fluxo de trabalho permite aos desenvolvedores chamar as operações de controle para controlar remotamente as instâncias de fluxo de trabalho hospedadas usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Esse recurso pode ser usado para executar programaticamente as operações de controle como suspender, continuar e encerrar.  
  
> [!WARNING]
>  Se usar o ponto de extremidade de controle de fluxo de trabalho dentro de uma transação e o fluxo de trabalho que está sendo controlado contém um <xref:System.Activities.Statements.Persist> atividade, a instância de fluxo de trabalho parará até que a transação de tempo limite.  
  
## <a name="workflow-instance-management"></a>Gerenciamento de instância de fluxo de trabalho  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]define um novo contrato chamado <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Este contrato define uma série de controle de operações que permitem que você remotamente controlam instâncias de fluxo de trabalho hospedadas por <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>é um ponto de extremidade padrão que fornece uma implementação de <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contrato. <xref:System.ServiceModel.Activities.WorkflowControlClient>é uma classe que é usada para enviar as operações de controle para o <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 Instâncias de fluxo de trabalho podem estar em um dos seguintes estados:  
  
 Ativo  
 O estado de uma instância de fluxo de trabalho antes de atingir o estado concluído e quando ele não está no estado suspenso. Nesse estado, a instância de fluxo de trabalho é executado e processa as mensagens de aplicativo.  
  
 Suspenso  
 Nesse estado, a instância de fluxo de trabalho não é executada, mesmo se houver atividades que não foram iniciadas em execução ou parcialmente executou.  
  
 Concluído  
 O estado final de uma instância de fluxo de trabalho. A instância de fluxo de trabalho não pode executar depois de atingir o estado concluído.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 O <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> interface define um conjunto de operações de controle com versões síncronas e assíncronas. As versões transacionadas requerem o uso de uma associação que reconhece a transação. A tabela a seguir lista as operações de controle com suporte.  
  
|Operação de controle|Descrição|  
|-----------------------|-----------------|  
|Anular|Para forçar a execução da instância do fluxo de trabalho.|  
|Cancelar|Faz a transição de uma instância de fluxo de trabalho do estado ativo ou suspenso para um estado concluído.|  
|Executar|Fornece a oportunidade de executar a uma instância de fluxo de trabalho.|  
|Suspender|Faz a transição de uma instância de fluxo de trabalho do estado ativo para o estado suspenso.|  
|Terminate|Faz a transição de uma instância de fluxo de trabalho do estado ativo ou suspenso para um estado concluído.|  
|Cancelar suspensão|Faz a transição de uma instância de fluxo de trabalho do estado suspenso para o estado ativo.|  
|TransactedCancel|Executa a operação de cancelamento de uma transação (recebida no fluxo do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
|TransactedRun|Executa a operação de execução em uma transação (recebida no fluxo do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
|TransactedSuspend|Executa a operação de suspensão em uma transação (recebida no fluxo do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
|TransactedTerminate|Executa a operação terminar em uma transação (recebida no fluxo do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
|TransactedUnsuspend|Executa a operação Unsuspend em uma transação (recebida no fluxo do cliente ou criado localmente). Se o sistema mantém o estado durável da instância do fluxo de trabalho, a instância de fluxo de trabalho deve ser persistida durante a execução desta operação.|  
  
 O <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contrato não fornecem um meio para criar uma nova instância de fluxo de trabalho, apenas para gerenciar instâncias de fluxo de trabalho existentes. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]remotamente criando uma nova instância de fluxo de trabalho, consulte [extensibilidade de Host do serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>é um ponto de extremidade padrão com um contrato fixo, <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Quando adicionada a um <xref:System.ServiceModel.Activities.WorkflowServiceHost> de instância, esse ponto de extremidade pode então ser usado para enviar as operações de comando em qualquer instância de fluxo de trabalho hospedada pela instância de host. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pontos de extremidade padrão, consulte [pontos de extremidade padrão](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient>é uma classe que permite enviar mensagens de controle para um <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> em um <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Ele contém um método para cada uma das operações com suporte a <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contrato, exceto as operações transacionadas. <xref:System.ServiceModel.Activities.WorkflowControlClient>usa a transação de ambiente para determinar se uma operação transacionada deve ser usada.
