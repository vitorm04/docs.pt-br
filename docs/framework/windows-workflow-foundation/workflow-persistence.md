---
title: Persistência de fluxo de trabalho
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: afe47975a393db3074222ebf0461f5b73fb6442d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655801"
---
# <a name="workflow-persistence"></a>Persistência de fluxo de trabalho
Persistência de fluxo de trabalho é a captura durável do estado de uma instância de fluxo de trabalho, independente de processo ou de informações do computador. Isso é feito para fornecer um ponto conhecido de recuperação para a instância de fluxo de trabalho no caso de falha do sistema, ou para preservar a memória descarregando as instâncias de fluxo de trabalho que não estão fazendo ativamente o trabalho, ou para mover o estado da instância de fluxo de trabalho de um nó para outro nó em um farm de servidores.  
  
 Persistência permite a agilidade do processo, a escalabilidade, a recuperação face falhar, e a capacidade gerenciar mais eficientemente a memória. O processo de persistência inclui a identificação de um ponto de persistência, a coleta de dados a ser salvos, e finalmente a delegação de armazenamento real de dados a um provedor de persistência.  
  
 Para ativar persistência para um fluxo de trabalho, você precisa associar um armazenamento de instância com o **WorkflowApplication** ou **WorkflowServiceHost** conforme mencionado na [como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho](how-to-enable-persistence-for-workflows-and-workflow-services.md). O **WorkflowApplication** e **WorkflowServiceHost** usar o armazenamento de instância associado a eles para ativar persistir instâncias de fluxo de trabalho em um repositório de persistência e carregar instâncias de fluxo de trabalho em memória com base nos dados de instância de fluxo de trabalho armazenados no repositório de persistência.  
  
 O [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] é fornecido com o **SqlWorkflowInstanceStore** classe, que permite a persistência dos dados e metadados sobre instâncias de fluxo de trabalho em um banco de dados do SQL Server 2005 ou SQL Server 2008. Ver [Store de instância de fluxo de trabalho do SQL](sql-workflow-instance-store.md) para obter mais detalhes.  
  
 Para armazenar e carregar os dados específicos do aplicativo junto com informações relacionadas instância de fluxo de trabalho, você pode criar os participantes de persistência que estendem a classe de <xref:System.Activities.Persistence.PersistenceParticipant> . Um participante de persistência participa no processo de persistência para salvar dados serializados personalizados no armazenamento de persistência, para carregar os dados da instância na memória, e executar qualquer lógica adicional em uma transação de persistência. Para obter mais informações, consulte [participantes de persistência](persistence-participants.md).  
  
 A tela de aplicativo Windows Server simplifica o processo de configurar a persistência. Para obter mais informações, consulte [conceitos de persistência com tela de aplicativo do Windows Server](https://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Pontos implícitos de persistência  
 A lista a seguir contém exemplos das circunstâncias na qual um fluxo de trabalho é mantido quando um armazenamento de instância é associado com um fluxo de trabalho.  
  
- Quando um **TransactionScope** conclusão da atividade ou um **TransactedReceiveScope** atividade é concluída.  
  
- Quando uma instância de fluxo de trabalho fica ociosa e o **WorkflowIdleBehavior** é definido no host de fluxo de trabalho. Isso ocorre, por exemplo, quando você usar as atividades de mensagem ou uma **atraso** atividade.  
  
- Quando um WorkflowApplication se torna ocioso e o **PersistableIdle** do aplicativo estiver definida como **Persistableidleaction**.  
  
- Quando um aplicativo host seja instruído para persistir ou descarregar uma instância de fluxo de trabalho.  
  
- Quando uma instância de fluxo de trabalho seja finalizada ou termina.  
  
- Quando um **Persist** atividade é executada.  
  
- Quando uma instância de um fluxo de trabalho desenvolvido usando uma versão anterior do Windows Workflow Foundation localizar um ponto de persistência durante a execução interoperável.  
  
## <a name="in-this-section"></a>Nesta seção  
  
- [Repositório de instâncias de fluxo de trabalho do SQL](sql-workflow-instance-store.md)  
  
- [Armazenamentos de instância](instance-stores.md)  
  
- [Participantes da persistência](persistence-participants.md)  
  
- [Práticas recomendadas de persistência](persistence-best-practices.md)  
  
- [Instâncias de fluxo de trabalho não persistentes](non-persisted-workflow-instances.md)  
  
- [Pausando e continuando um fluxo de trabalho](pausing-and-resuming-a-workflow.md)
