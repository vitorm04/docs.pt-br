---
title: Recuperação de dados e operações de COMIDA RUMINADA em aplicativos de n camadas (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: ebbc53f2962c99bc31f998f1afcb4316f3ea81f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674697"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="d2e3d-102">Recuperação de dados e operações de COMIDA RUMINADA em aplicativos de n camadas (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="d2e3d-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="d2e3d-103">Quando você serializa objetos de entidade como clientes ou pedidos para um cliente em uma rede, essas entidades são desanexadas de seu contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="d2e3d-104">O contexto de dados não controla as alterações ou suas associações com outros objetos.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="d2e3d-105">Isso não é um problema que os clientes estão lê apenas os dados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="d2e3d-106">Também é relativamente simples permitir que clientes para adicionar novas linhas em uma base de dados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="d2e3d-107">No entanto, se seu aplicativo requer que os clientes possam atualizar ou excluir dados, você deve anexar as entidades a um novo contexto de dados antes de chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d2e3d-108">Além disso, se você estiver usando uma verificação de simultaneidade otimista com valores originais, então você também precisará de uma maneira de fornecer a base de dados a entidade original e a entidade como modificada.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="d2e3d-109">Os métodos de `Attach` são fornecidos para permite que você coloque entidades em um novo contexto de dados depois que foram separados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="d2e3d-110">Mesmo se você estiver serializando objetos de proxy em vez do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entidades, você ainda precisa construir uma entidade na camada de acesso a dados (DAL) e anexá-lo para um novo <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, para enviar os dados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="d2e3d-111">é completamente indiferente sobre como as entidades são serializadas.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="d2e3d-112">Para obter mais informações sobre como usar o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] e ferramentas de SQLMetal para gerar classes que são serializadas usando Windows Communication Foundation (WCF), consulte [como: Tornar entidades serializáveis](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-112">For more information about how to use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2e3d-113">Chamar apenas os métodos de `Attach` em novos ou entidades desserializado.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="d2e3d-114">A única maneira para uma entidade é desanexada de seu contexto de dados original é para que é serializada.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="d2e3d-115">Se você tentar anexar uma entidade undetached a um novo contexto de dados, e a entidade tem adiado ainda carregadores de seu contexto de dados anterior, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] seja lançada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="d2e3d-116">Uma entidade com os carregadores adiados de dois contextos de dados diferentes pode causar resultados indesejados quando você executa insert, update e delete operações nessa entidade.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="d2e3d-117">Para obter mais informações sobre carregadores adiados, consulte [adiada versus imediata Carregando](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="d2e3d-118">Recuperando dados</span><span class="sxs-lookup"><span data-stu-id="d2e3d-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="d2e3d-119">Chamada de método de cliente</span><span class="sxs-lookup"><span data-stu-id="d2e3d-119">Client Method Call</span></span>  
 <span data-ttu-id="d2e3d-120">Os seguintes exemplos mostram uma chamada de método de exemplo para DAL de um cliente Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="d2e3d-121">Nesse exemplo, o DAL é implementado como uma biblioteca de serviço do Windows:</span><span class="sxs-lookup"><span data-stu-id="d2e3d-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =   
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =   
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,   
    // the client needs to store them and pass them back to the   
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="d2e3d-122">Implementação de camada intermediária</span><span class="sxs-lookup"><span data-stu-id="d2e3d-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="d2e3d-123">O exemplo a seguir mostra uma implementação do método de interface na camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="d2e3d-124">A seguir estão as duas problemas básicas para a observação:</span><span class="sxs-lookup"><span data-stu-id="d2e3d-124">The following are the two main points to note:</span></span>  
  
-   <span data-ttu-id="d2e3d-125"><xref:System.Data.Linq.DataContext> é declarado no escopo do método.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
-   <span data-ttu-id="d2e3d-126">O método retorna uma coleção de <xref:System.Collections.IEnumerable> de resultados reais.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="d2e3d-127">O serializador executar a consulta para enviar os resultados de volta para o cliente/camada de apresentação.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="d2e3d-128">Para acessar localmente os resultados da consulta na camada intermediária, você pode forçar a execução chamando `ToList` ou `ToArray` na variável de consulta.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="d2e3d-129">Você pode então retornar a lista ou matriz como `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =   
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();   
}  
```  
  
 <span data-ttu-id="d2e3d-130">Uma instância de um contexto de dados deve ter um tempo de vida de uma unidade de trabalho “.”</span><span class="sxs-lookup"><span data-stu-id="d2e3d-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="d2e3d-131">Em um ambiente fracamente acoplado, uma unidade de trabalho é normalmente pequena, talvez uma transação otimista, incluindo uma única chamada a `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="d2e3d-132">Portanto, o contexto de dados é criado e descartado no escopo de método.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="d2e3d-133">Se a unidade de trabalho inclui chamadas a lógica das regras comerciais, então você geralmente deseja manter a instância de `DataContext` para essa operação inteira.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="d2e3d-134">Em qualquer caso, as instâncias de `DataContext` não sejam mantidas ativas por longos períodos de tempo entre os números arbitrários de transações.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="d2e3d-135">Este método retornará objetos do produto mas não a coleção de objetos de Order_Detail que são associados a cada produto.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="d2e3d-136">Use o objeto de <xref:System.Data.Linq.DataLoadOptions> para alterar esse comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="d2e3d-137">Para obter mais informações, confira [Como: Controlar a quantidade de dados relacionado é recuperado](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-137">For more information, see [How to: Control How Much Related Data Is Retrieved](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="d2e3d-138">Inserindo dados</span><span class="sxs-lookup"><span data-stu-id="d2e3d-138">Inserting Data</span></span>  
 <span data-ttu-id="d2e3d-139">Para inserir um novo objeto, chamadas camada de apresentação apenas o método relevante na interface de camada intermediária, e passa no novo objeto inserção.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="d2e3d-140">Em alguns casos, pode ser mais eficiente para o cliente envia somente em alguns valores e com a camada intermediária construir o objeto completo.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="d2e3d-141">Implementação de camada intermediária</span><span class="sxs-lookup"><span data-stu-id="d2e3d-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="d2e3d-142">Na camada intermediária, novo <xref:System.Data.Linq.DataContext> é criado, o objeto é anexado a <xref:System.Data.Linq.DataContext> usando o método <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> , e o objeto é inserido quando <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="d2e3d-143">Exceções, callbacks, e as condições de erro podem ser tratados assim como em qualquer outro cenário de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a><span data-ttu-id="d2e3d-144">Excluindo dados</span><span class="sxs-lookup"><span data-stu-id="d2e3d-144">Deleting Data</span></span>  
 <span data-ttu-id="d2e3d-145">Para excluir um objeto existente de base de dados, de chamadas camada de apresentação o método relevante na interface de camada intermediária, e passa em sua cópia que inclui valores originais do objeto a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="d2e3d-146">Operações de exclusão envolvem verificação de simultaneidade otimista, e o objeto a ser excluído deve primeiro ser anexado ao novo contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="d2e3d-147">Nesse exemplo, o parâmetro de `Boolean` é definido como `false` para indicar que o objeto não tem um carimbo de data/hora (RowVersion).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="d2e3d-148">Se sua tabela de base de dados gerencia carimbos de data/hora para cada registro, então a verificação de simultaneidade são muito mais simples, especialmente para o cliente.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="d2e3d-149">Basta passar no original ou o objeto alterado e define o parâmetro de `Boolean` a `true`.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="d2e3d-150">Em qualquer caso, na camada intermediária é geralmente necessário capturar <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="d2e3d-151">Para obter mais informações sobre como lidar com conflitos de simultaneidade otimista, consulte [a simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="d2e3d-152">Para excluir as entidades que têm restrições de chave externa em tabelas associadas, você deve primeiro excluir todos os objetos nas coleções de <xref:System.Data.Linq.EntitySet%601> .</span><span class="sxs-lookup"><span data-stu-id="d2e3d-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a><span data-ttu-id="d2e3d-153">Atualizando dados</span><span class="sxs-lookup"><span data-stu-id="d2e3d-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="d2e3d-154">suporta atualizações nesses cenários que envolvem concorrência otimista:</span><span class="sxs-lookup"><span data-stu-id="d2e3d-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
-   <span data-ttu-id="d2e3d-155">Concorrência otimista com base em carimbos de data/hora ou em números de RowVersion.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
-   <span data-ttu-id="d2e3d-156">Concorrência otimista com base em valores originais de um subconjunto de propriedades de entidade.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
-   <span data-ttu-id="d2e3d-157">Concorrência otimista com base nas entidades originais e modificadas completos.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="d2e3d-158">Você também pode executar atualizações e exclusões em uma entidade junto com suas relações, por exemplo um cliente e uma coleção de seus objetos associados de ordem.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="d2e3d-159">Quando você faz alterações no cliente a um gráfico de objetos de entidade e das coleções filho (de`EntitySet`), e as verificações de simultaneidade otimista exigem valores originais, o cliente deve fornecer os valores originais para cada entidade e objeto de <xref:System.Data.Linq.EntitySet%601> .</span><span class="sxs-lookup"><span data-stu-id="d2e3d-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="d2e3d-160">Se você deseja permitir que clientes para fazer um conjunto de atualizações, de exclusões, e de inserções relacionadas em uma única chamada de método, você deve fornecer o cliente uma maneira para indicar que tipo de operação para executar em cada entidade.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="d2e3d-161">Na camada intermediária, então você deve chamar o método apropriado e então <xref:System.Data.Linq.ITable.Attach%2A>de <xref:System.Data.Linq.ITable.InsertOnSubmit%2A> , <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, ou <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (sem `Attach`, porque inserções) para cada entidade antes de chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="d2e3d-162">Não recuperar dados de base de dados como uma maneira para obter valores originais antes de tentar atualizações.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="d2e3d-163">Para obter mais informações sobre a simultaneidade otimista, consulte [a simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="d2e3d-164">Para obter informações detalhadas sobre como resolver a simultaneidade otimista de conflitos de alteração, consulte [como: Gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="d2e3d-165">Os seguintes exemplos demonstram cada cenário:</span><span class="sxs-lookup"><span data-stu-id="d2e3d-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="d2e3d-166">Concorrência otimista com carimbos de data/hora</span><span class="sxs-lookup"><span data-stu-id="d2e3d-166">Optimistic concurrency with timestamps</span></span>  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="d2e3d-167">Com subconjunto de valores originais</span><span class="sxs-lookup"><span data-stu-id="d2e3d-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="d2e3d-168">Nessa abordagem, o cliente retorna o objeto serializado completo, juntamente com os valores a serem alterados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a><span data-ttu-id="d2e3d-169">Com entidades completos</span><span class="sxs-lookup"><span data-stu-id="d2e3d-169">With Complete Entities</span></span>  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }   
    }  
}  
```  
  
 <span data-ttu-id="d2e3d-170">Para atualizar uma coleção, chame <xref:System.Data.Linq.ITable.AttachAll%2A> em vez de `Attach`.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="d2e3d-171">Membros esperados de entidade</span><span class="sxs-lookup"><span data-stu-id="d2e3d-171">Expected Entity Members</span></span>  
 <span data-ttu-id="d2e3d-172">Conforme observado anteriormente, somente certos membros do objeto de entidade são necessários ser definidos antes de chamar os métodos de `Attach` .</span><span class="sxs-lookup"><span data-stu-id="d2e3d-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="d2e3d-173">Membros de entidade que são necessários devem ser definidos atender aos seguintes critérios:</span><span class="sxs-lookup"><span data-stu-id="d2e3d-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
-   <span data-ttu-id="d2e3d-174">É parte da identidade de entidade.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-174">Be part of the entity’s identity.</span></span>  
  
-   <span data-ttu-id="d2e3d-175">É esperado ser alterado.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-175">Be expected to be modified.</span></span>  
  
-   <span data-ttu-id="d2e3d-176">É um carimbo de data/hora ou tem o atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> definido como algo além de `Never`.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="d2e3d-177">Se uma tabela usa um carimbo de data/hora ou número de versão para uma verificação de simultaneidade otimista, você deve definir esses membros antes de chamar <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="d2e3d-178">Um membro é dedicado para concorrência otimista verificando quando a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> é definida para retificar no atributo de coluna.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="d2e3d-179">Todas as atualizações solicitadas serão enviadas somente se os valores de número de versão ou de carimbo de data/hora são os mesmos na base de dados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="d2e3d-180">Um membro é usado também na verificação de simultaneidade otimista do membro não tem <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> definido como `Never`.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="d2e3d-181">O valor padrão é `Always` se nenhum outro valor é especificado.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="d2e3d-182">Se qualquer um desses membros necessários estiver faltando, <xref:System.Data.Linq.ChangeConflictException> é acionada durante <xref:System.Data.Linq.DataContext.SubmitChanges%2A> a linha (“não encontrado ou alterado”).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="d2e3d-183">Estado</span><span class="sxs-lookup"><span data-stu-id="d2e3d-183">State</span></span>  
 <span data-ttu-id="d2e3d-184">Depois que um objeto de entidade é conectado à instância de <xref:System.Data.Linq.DataContext> , o objeto é considerado estar no estado de `PossiblyModified` .</span><span class="sxs-lookup"><span data-stu-id="d2e3d-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="d2e3d-185">Existem três maneiras para forçar um objeto anexado a ser considerado `Modified`.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1.  <span data-ttu-id="d2e3d-186">Como anexá-lo inalterados, e então altere-o diretamente os campos.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2.  <span data-ttu-id="d2e3d-187">Anexa com a sobrecarga de <xref:System.Data.Linq.Table%601.Attach%2A> que recebe a atuais e originais instâncias de objeto.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="d2e3d-188">Isso fornece o perseguidor de alteração com valores antigo e novo de modo que sabe como automaticamente campos que foram alterados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3.  <span data-ttu-id="d2e3d-189">Anexa com a sobrecarga de <xref:System.Data.Linq.Table%601.Attach%2A> que leva um segundo parâmetro boolean (definido para retificar).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="d2e3d-190">Isso dirá o perseguidor de alteração para ver o objeto alterado sem ter que fornecer os valores originais.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="d2e3d-191">Nessa abordagem, o objeto deve ter um campo de versão/carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="d2e3d-192">Para obter mais informações, consulte [estados de objeto e controle de alterações](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="d2e3d-192">For more information, see [Object States and Change-Tracking](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="d2e3d-193">Se um objeto de entidade já ocorre no cache de identificação com a mesma identidade que o objeto sendo anexado, <xref:System.Data.Linq.DuplicateKeyException> é lançada.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="d2e3d-194">Quando você anexa com `IEnumerable` conjunto de objetos, <xref:System.Data.Linq.DuplicateKeyException> é acionada quando uma chave já existente estiver presente.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="d2e3d-195">Os objetos restantes não estão conectados.</span><span class="sxs-lookup"><span data-stu-id="d2e3d-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e3d-196">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2e3d-196">See also</span></span>
- [<span data-ttu-id="d2e3d-197">Aplicativos de N camadas e remotos com o LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d2e3d-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="d2e3d-198">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="d2e3d-198">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
