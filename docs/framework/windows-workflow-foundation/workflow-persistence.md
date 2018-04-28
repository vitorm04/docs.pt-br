---
title: Persistência de fluxo de trabalho
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2278762895978f90d80977f9e538b0e10a4f3f8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="workflow-persistence"></a>Persistência de fluxo de trabalho
Persistência de fluxo de trabalho é a captura durável do estado de uma instância de fluxo de trabalho, independente de processo ou de informações do computador. Isso é feito para fornecer um ponto conhecido de recuperação para a instância de fluxo de trabalho no caso de falha do sistema, ou para preservar a memória descarregando as instâncias de fluxo de trabalho que não estão fazendo ativamente o trabalho, ou para mover o estado da instância de fluxo de trabalho de um nó para outro nó em um farm de servidores.  
  
 Persistência permite a agilidade do processo, a escalabilidade, a recuperação face falhar, e a capacidade gerenciar mais eficientemente a memória. O processo de persistência inclui a identificação de um ponto de persistência, a coleta de dados a ser salvos, e finalmente a delegação de armazenamento real de dados a um provedor de persistência.  
  
 Para habilitar a persistência de um fluxo de trabalho, você precisa associar a um repositório de instâncias com o **WorkflowApplication** ou **WorkflowServiceHost** conforme mencionado em [como: Ativar persistência para Fluxos de trabalho e serviços de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md). O **WorkflowApplication** e **WorkflowServiceHost** usar o armazenamento de instância associado a eles para habilitar instâncias de fluxo de trabalho persistentes em um repositório de persistência e carregamento de instâncias de fluxo de trabalho em memória com base nos dados de instância de fluxo de trabalho armazenados no repositório de persistência.  
  
 O [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] acompanha o **SqlWorkflowInstanceStore** classe, que permite a persistência de dados e metadados sobre instâncias de fluxo de trabalho em um banco de dados do SQL Server 2005 ou SQL Server 2008. Consulte [armazenamento de instância de fluxo de trabalho do SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) para obter mais detalhes.  
  
 Para armazenar e carregar os dados específicos do aplicativo junto com informações relacionadas instância de fluxo de trabalho, você pode criar os participantes de persistência que estendem a classe de <xref:System.Activities.Persistence.PersistenceParticipant> . Um participante de persistência participa no processo de persistência para salvar dados serializados personalizados no armazenamento de persistência, para carregar os dados da instância na memória, e executar qualquer lógica adicional em uma transação de persistência. Para obter mais informações, consulte [participantes de persistência](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).  
  
 A tela de aplicativo Windows Server simplifica o processo de configurar a persistência. Para obter mais informações, consulte [conceitos de persistência com Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Pontos implícitos de persistência  
 A lista a seguir contém exemplos das circunstâncias na qual um fluxo de trabalho é mantido quando um armazenamento de instância é associado com um fluxo de trabalho.  
  
-   Quando um **TransactionScope** conclusão da atividade ou um **TransactedReceiveScope** conclusão da atividade.  
  
-   Quando uma instância de fluxo de trabalho se torna ociosa e o **WorkflowIdleBehavior** é definido no host de fluxo de trabalho. Isso ocorre, por exemplo, quando você usar atividades de mensagens ou um **atraso** atividade.  
  
-   Quando um WorkflowApplication fica ocioso e o **PersistableIdle** do aplicativo é definida como **PersistableIdleAction.Persist**.  
  
-   Quando um aplicativo host seja instruído para persistir ou descarregar uma instância de fluxo de trabalho.  
  
-   Quando uma instância de fluxo de trabalho seja finalizada ou termina.  
  
-   Quando um **Persist** atividade é executada.  
  
-   Quando uma instância de um fluxo de trabalho desenvolvido usando uma versão anterior do Windows Workflow Foundation localizar um ponto de persistência durante a execução interoperável.  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Repositório de instâncias de fluxo de trabalho do SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [Armazenamentos de instância](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [Participantes da persistência](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [Práticas recomendadas de persistência](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [Instâncias de fluxo de trabalho não persistentes](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [Pausando e continuando um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
