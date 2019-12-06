---
title: Store instância de fluxo de trabalho do SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 1764017369e82cfbed38be06b4a36847576b5fc0
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837630"
---
# <a name="sql-workflow-instance-store"></a>Store instância de fluxo de trabalho do SQL
Os vem de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] com a instância Store de fluxo de trabalho SQL, que permite que fluxos de trabalho persistam informações de estado sobre instâncias de fluxo de trabalho em uma base de dados SQL Server 2005 ou SQL Server 2008. Esse recurso é implementado primeiro na forma da classe de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , que deriva da classe abstrata de <xref:System.Runtime.DurableInstancing.InstanceStore> a estrutura de persistência. O recurso de Store de instância de fluxo de trabalho do SQL constitui um provedor de persistência SQL, que é uma implementação concreta de persistência API que um host usa para enviar comandos de persistência no armazenamento.  
  
 A instância Store de fluxo de trabalho do SQL oferece suporte fluxos de trabalho são hospedados ou serviços de fluxo de trabalho que usam <xref:System.Activities.WorkflowApplication> ou <xref:System.ServiceModel.WorkflowServiceHost> bem como os serviços hospedado em usavam <xref:System.ServiceModel.WorkflowServiceHost>. Você pode configurar o recurso de Store de instância de fluxo de trabalho SQL para serviços são hospedados por meio de programação usando o modelo de objeto exposto pelo recurso. Você pode configurar esse recurso para os serviços hospedados por <xref:System.ServiceModel.WorkflowServiceHost> programaticamente usando o modelo de objeto e também usando um arquivo de configuração XML.  
  
 O recurso de repositório de instância do fluxo de trabalho SQL (classe**SqlWorkflowInstanceStore** ) não implementa <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> e, portanto, não oferece suporte de persistência para serviços WCF duráveis que não sejam de fluxo de trabalho. Também não implementa <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> e portanto não oferece suporte a persistência para fluxos de trabalho 3.x. O recurso oferece suporte a persistência apenas para fluxos de trabalho WF (4,0 e posteriores) e serviços de fluxo de trabalho. O recurso também não suporta nenhum bases de dados diferentes do SQL Server 2005 e SQL Server 2008.  
  
 Os tópicos nesta seção descrevem as propriedades e os recursos de instância de fluxo de trabalho do SQL e fornecer-l com detalhes sobre como configurar o armazenamento.  
  
 A tela de aplicativo Windows Server fornece seus próprios armazenamento e trabalho feito com ferramentas de instância para simplificar a configuração e uso da instância. Para obter mais informações, consulte [Windows Server app Fabric Instance Store](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)). Para obter mais informações sobre o banco de dados de persistência do App Fabric SQL Server, consulte [app fabric SQL Server Persistence Database](https://docs.microsoft.com/previous-versions/appfabric/ee790819(v=azure.10))  
  
## <a name="in-this-section"></a>Nesta seção  
  
- [Propriedades do repositório de instâncias de fluxo de trabalho do SQL](properties-of-sql-workflow-instance-store.md)  
  
- [Como habilitar a persistência de SQL para fluxos de trabalho e serviços de fluxo de trabalho](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [Ativação de instância](instance-activation.md)  
  
- [Suporte para consultas](support-for-queries.md)  
  
- [Extensibilidade de repositório](store-extensibility.md)  
  
- [Security](security.md)  
  
- [Banco de dados de persistência do SQL Server](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de persistência](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))
