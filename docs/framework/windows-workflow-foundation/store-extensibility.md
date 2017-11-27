---
title: Extensibilidade de Store
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6700fe67d151e78c8b216d93a4cd7098ed6401d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="store-extensibility"></a>Extensibilidade de Store
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> permite que os usuários elevem o personalizado, as propriedades específicas do aplicativo que podem ser usadas para consultar instâncias na base de dados de persistência. O ato de elevar uma propriedade faz com que o valor esteja disponível em uma exibição especial na base de dados. Essas propriedades elevadas (propriedades que podem ser usadas em consultas de usuário) podem ser de tipos simples como Int64, GUID, cadeia de caracteres, e DateTime ou tipo binário serializado (byte []).  
  
 A classe de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> tem o método de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> que você pode usar para elevar uma propriedade como uma propriedade que pode ser usada em consultas. O exemplo a seguir é um exemplo de ponta a ponta de extensibilidade de armazenamento.  
  
1.  Neste cenário exemplo, um aplicativo de (DP) de processamento de documento tem fluxos de trabalho, cada um deless use atividades personalizadas para processamento de documento. Esses fluxos de trabalho têm um conjunto de variáveis de estado que precisam ser feitos visíveis para o usuário final. Para obter isso, o aplicativo de DP fornece uma extensão da instância do tipo <xref:System.Activities.Persistence.PersistenceParticipant>, que é usado por atividades para fornecer variáveis de estado.  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  A nova extensão é adicionada para o host.  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     Para obter mais detalhes sobre como adicionar um participante de persistência personalizado, consulte o [participantes de persistência](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) exemplo.  
  
3.  As atividades personalizadas no aplicativo DP popular vários campos de status no **Execute** método.  
  
    ```  
    public override void Execute(CodeActivityContext context)  
    {  
        // ...  
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();  
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";  
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";  
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();  
        // ...  
    }  
    ```  
  
4.  Quando uma instância de fluxo de trabalho atinge um ponto de persistência, o **CollectValues** método o **DocumentStatusExtension** participante de persistência salva essas propriedades para os dados de persistência coleção.  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");  
  
        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)  
        {  
            readWriteValues = new Dictionary<XName, object>();  
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);  
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);  
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);  
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);  
  
            writeOnlyValues = null;  
        }  
        // ...  
    }  
    ```  
  
    > [!NOTE]
    >  Todas essas propriedades são passadas para **SqlWorkflowInstanceStore** pela estrutura de persistência por meio de **SaveWorkflowCommand.InstanceData** coleção.  
  
5.  O aplicativo DP inicializa o armazenamento de instância de fluxo de trabalho do SQL e invoca o **promover** método para promover a esses dados.  
  
    ```  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
  
    List<XName> variantProperties = new List<XName>()   
    {   
        xNS.GetName("UserName"),   
        xNS.GetName("ApprovalStatus"),   
        xNS.GetName("DocumentId"),   
        xNS.GetName("LastModifiedTime")   
    };  
  
    store.Promote("DocumentStatus", variantProperties, null);  
    ```  
  
     Com base nessas informações de promoção, **SqlWorkflowInstanceStore** coloca as propriedades de dados em colunas da [InstancePromotedProperties](#InstancePromotedProperties) exibição.
  
6.  Para ver um subconjunto dos dados da tabela da promoção, o aplicativo de DP adiciona um modo de exibição personalizado no modo da promoção.  
  
    ```  
    create view [dbo].[DocumentStatus] with schemabinding  
    as  
        select  P.[InstanceId] as [InstanceId],  
            P.Value1 as [UserName],  
            P.Value2 as [ApprovalStatus],  
            P.Value3 as [DocumentId],  
            P.Value4 as [LastUpdatedTime]  
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P  
    where P.PromotionName = N'DocumentStatus'  
    go  
    ```  
  
##  <a name="InstancePromotedProperties"></a>Exibição [System.Activities.DurableInstancing.InstancePromotedProperties]  
  
|Nome da coluna|Tipo de coluna|Descrição|  
|-----------------|-----------------|-----------------|  
|InstanceId|GUID|A instância de fluxo de trabalho que essa promoção pertence.|  
|PromotionName|nvarchar (400)|O nome da promoção próprio.|  
|Valor1, valor2, Value3. , Value32|sql_variant|O valor da propriedade promovida próprio. A maioria dos tipos de dados primitivos SQL exceto gotas binários e cadeias de caracteres sobre 8000 bytes de comprimento podem caber em sql_variant.|  
|Value33, Value34, Value35,…, Value64|varbinary (máximo)|O valor das propriedades elevadas que são explicitamente declaradas como varbinary (máximo).|
