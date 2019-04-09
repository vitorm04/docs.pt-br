---
title: Store instância de fluxo de trabalho do SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 8314781f46d9cd4eddd06f6be95f8e952feef1b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086566"
---
# <a name="sql-workflow-instance-store"></a>Store instância de fluxo de trabalho do SQL
Os vem de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] com a instância Store de fluxo de trabalho SQL, que permite que fluxos de trabalho persistam informações de estado sobre instâncias de fluxo de trabalho em uma base de dados SQL Server 2005 ou SQL Server 2008. Esse recurso é implementado primeiro na forma da classe de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , que deriva da classe abstrata de <xref:System.Runtime.DurableInstancing.InstanceStore> a estrutura de persistência. O recurso de Store de instância de fluxo de trabalho do SQL constitui um provedor de persistência SQL, que é uma implementação concreta de persistência API que um host usa para enviar comandos de persistência no armazenamento.  
  
 A instância Store de fluxo de trabalho do SQL oferece suporte fluxos de trabalho são hospedados ou serviços de fluxo de trabalho que usam <xref:System.Activities.WorkflowApplication> ou <xref:System.ServiceModel.WorkflowServiceHost> bem como os serviços hospedado em usavam <xref:System.ServiceModel.WorkflowServiceHost>. Você pode configurar o recurso de Store de instância de fluxo de trabalho SQL para serviços são hospedados por meio de programação usando o modelo de objeto exposto pelo recurso. Você pode configurar esse recurso para os serviços hospedados por <xref:System.ServiceModel.WorkflowServiceHost> programaticamente usando o modelo de objeto e também usando um arquivo de configuração XML.  
  
 O recurso de Store de instância de fluxo de trabalho do SQL (**SqlWorkflowInstanceStore** classe) não implementa <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> e portanto não oferece suporte a persistência para os serviços WCF sem fluxo de trabalho duráveis. Também não implementa <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> e portanto não oferece suporte a persistência para fluxos de trabalho 3.x. O recurso oferece suporte a persistência apenas para fluxos de trabalho WF (4,0 e posteriores) e serviços de fluxo de trabalho. O recurso também não suporta nenhum bases de dados diferentes do SQL Server 2005 e SQL Server 2008.  
  
 Os tópicos nesta seção descrevem as propriedades e os recursos de instância de fluxo de trabalho do SQL e fornecer-l com detalhes sobre como configurar o armazenamento.  
  
 A tela de aplicativo Windows Server fornece seus próprios armazenamento e trabalho feito com ferramentas de instância para simplificar a configuração e uso da instância. Para obter mais informações, consulte [Store de instância do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201201). Para obter mais informações sobre, consulte o banco de dados do App Fabric SQL Server persistência [dados de persistência do App Fabric SQL Server](https://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Propriedades de instância Store de fluxo de trabalho do SQL](properties-of-sql-workflow-instance-store.md)  
  
-   [Como: habilitar persistência SQL para fluxos de trabalho e serviços de fluxo de trabalho](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [Ativação de instância](instance-activation.md)  
  
-   [Suporte para consultas](support-for-queries.md)  
  
-   [Extensibilidade de Store](store-extensibility.md)  
  
-   [Segurança](security.md)  
  
-   [A base de dados do SQL Server](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Consulte também

- [Persistência Exemplos](https://go.microsoft.com/fwlink/?LinkID=177735)
