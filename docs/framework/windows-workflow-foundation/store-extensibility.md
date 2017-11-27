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
# <a name="store-extensibility"></a><span data-ttu-id="f6db9-102">Extensibilidade de Store</span><span class="sxs-lookup"><span data-stu-id="f6db9-102">Store Extensibility</span></span>
<span data-ttu-id="f6db9-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> permite que os usuários elevem o personalizado, as propriedades específicas do aplicativo que podem ser usadas para consultar instâncias na base de dados de persistência.</span><span class="sxs-lookup"><span data-stu-id="f6db9-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="f6db9-104">O ato de elevar uma propriedade faz com que o valor esteja disponível em uma exibição especial na base de dados.</span><span class="sxs-lookup"><span data-stu-id="f6db9-104">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="f6db9-105">Essas propriedades elevadas (propriedades que podem ser usadas em consultas de usuário) podem ser de tipos simples como Int64, GUID, cadeia de caracteres, e DateTime ou tipo binário serializado (byte []).</span><span class="sxs-lookup"><span data-stu-id="f6db9-105">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>  
  
 <span data-ttu-id="f6db9-106">A classe de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> tem o método de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> que você pode usar para elevar uma propriedade como uma propriedade que pode ser usada em consultas.</span><span class="sxs-lookup"><span data-stu-id="f6db9-106">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="f6db9-107">O exemplo a seguir é um exemplo de ponta a ponta de extensibilidade de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="f6db9-107">The following example is an end-to-end example of store extensibility.</span></span>  
  
1.  <span data-ttu-id="f6db9-108">Neste cenário exemplo, um aplicativo de (DP) de processamento de documento tem fluxos de trabalho, cada um deless use atividades personalizadas para processamento de documento.</span><span class="sxs-lookup"><span data-stu-id="f6db9-108">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="f6db9-109">Esses fluxos de trabalho têm um conjunto de variáveis de estado que precisam ser feitos visíveis para o usuário final.</span><span class="sxs-lookup"><span data-stu-id="f6db9-109">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="f6db9-110">Para obter isso, o aplicativo de DP fornece uma extensão da instância do tipo <xref:System.Activities.Persistence.PersistenceParticipant>, que é usado por atividades para fornecer variáveis de estado.</span><span class="sxs-lookup"><span data-stu-id="f6db9-110">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  <span data-ttu-id="f6db9-111">A nova extensão é adicionada para o host.</span><span class="sxs-lookup"><span data-stu-id="f6db9-111">The new extension is then added to the host.</span></span>  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     <span data-ttu-id="f6db9-112">Para obter mais detalhes sobre como adicionar um participante de persistência personalizado, consulte o [participantes de persistência](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="f6db9-112">For more details about adding a custom persistence participant, see the [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) sample.</span></span>  
  
3.  <span data-ttu-id="f6db9-113">As atividades personalizadas no aplicativo DP popular vários campos de status no **Execute** método.</span><span class="sxs-lookup"><span data-stu-id="f6db9-113">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>  
  
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
  
4.  <span data-ttu-id="f6db9-114">Quando uma instância de fluxo de trabalho atinge um ponto de persistência, o **CollectValues** método o **DocumentStatusExtension** participante de persistência salva essas propriedades para os dados de persistência coleção.</span><span class="sxs-lookup"><span data-stu-id="f6db9-114">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>  
  
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
    >  <span data-ttu-id="f6db9-115">Todas essas propriedades são passadas para **SqlWorkflowInstanceStore** pela estrutura de persistência por meio de **SaveWorkflowCommand.InstanceData** coleção.</span><span class="sxs-lookup"><span data-stu-id="f6db9-115">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>  
  
5.  <span data-ttu-id="f6db9-116">O aplicativo DP inicializa o armazenamento de instância de fluxo de trabalho do SQL e invoca o **promover** método para promover a esses dados.</span><span class="sxs-lookup"><span data-stu-id="f6db9-116">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>  
  
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
  
     <span data-ttu-id="f6db9-117">Com base nessas informações de promoção, **SqlWorkflowInstanceStore** coloca as propriedades de dados em colunas da [InstancePromotedProperties](#InstancePromotedProperties) exibição.</span><span class="sxs-lookup"><span data-stu-id="f6db9-117">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>
  
6.  <span data-ttu-id="f6db9-118">Para ver um subconjunto dos dados da tabela da promoção, o aplicativo de DP adiciona um modo de exibição personalizado no modo da promoção.</span><span class="sxs-lookup"><span data-stu-id="f6db9-118">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>  
  
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
  
##  <span data-ttu-id="f6db9-119"><a name="InstancePromotedProperties"></a>Exibição [System.Activities.DurableInstancing.InstancePromotedProperties]</span><span class="sxs-lookup"><span data-stu-id="f6db9-119"><a name="InstancePromotedProperties"></a> [System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>  
  
|<span data-ttu-id="f6db9-120">Nome da coluna</span><span class="sxs-lookup"><span data-stu-id="f6db9-120">Column Name</span></span>|<span data-ttu-id="f6db9-121">Tipo de coluna</span><span class="sxs-lookup"><span data-stu-id="f6db9-121">Column Type</span></span>|<span data-ttu-id="f6db9-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6db9-122">Description</span></span>|  
|-----------------|-----------------|-----------------|  
|<span data-ttu-id="f6db9-123">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f6db9-123">InstanceId</span></span>|<span data-ttu-id="f6db9-124">GUID</span><span class="sxs-lookup"><span data-stu-id="f6db9-124">GUID</span></span>|<span data-ttu-id="f6db9-125">A instância de fluxo de trabalho que essa promoção pertence.</span><span class="sxs-lookup"><span data-stu-id="f6db9-125">The workflow instance that this promotion belongs to.</span></span>|  
|<span data-ttu-id="f6db9-126">PromotionName</span><span class="sxs-lookup"><span data-stu-id="f6db9-126">PromotionName</span></span>|<span data-ttu-id="f6db9-127">nvarchar (400)</span><span class="sxs-lookup"><span data-stu-id="f6db9-127">nvarchar(400)</span></span>|<span data-ttu-id="f6db9-128">O nome da promoção próprio.</span><span class="sxs-lookup"><span data-stu-id="f6db9-128">The name of the promotion itself.</span></span>|  
|<span data-ttu-id="f6db9-129">Valor1, valor2, Value3. , Value32</span><span class="sxs-lookup"><span data-stu-id="f6db9-129">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="f6db9-130">sql_variant</span><span class="sxs-lookup"><span data-stu-id="f6db9-130">sql_variant</span></span>|<span data-ttu-id="f6db9-131">O valor da propriedade promovida próprio.</span><span class="sxs-lookup"><span data-stu-id="f6db9-131">The value of the promoted property itself.</span></span> <span data-ttu-id="f6db9-132">A maioria dos tipos de dados primitivos SQL exceto gotas binários e cadeias de caracteres sobre 8000 bytes de comprimento podem caber em sql_variant.</span><span class="sxs-lookup"><span data-stu-id="f6db9-132">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|  
|<span data-ttu-id="f6db9-133">Value33, Value34, Value35,…, Value64</span><span class="sxs-lookup"><span data-stu-id="f6db9-133">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="f6db9-134">varbinary (máximo)</span><span class="sxs-lookup"><span data-stu-id="f6db9-134">varbinary(max)</span></span>|<span data-ttu-id="f6db9-135">O valor das propriedades elevadas que são explicitamente declaradas como varbinary (máximo).</span><span class="sxs-lookup"><span data-stu-id="f6db9-135">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
