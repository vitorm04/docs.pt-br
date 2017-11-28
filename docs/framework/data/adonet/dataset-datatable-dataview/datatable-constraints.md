---
title: "Restrições de DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fb1fd2c7aa057fcc83c82ab9d72129db2cac680e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-constraints"></a><span data-ttu-id="4f9a8-102">Restrições de DataTable</span><span class="sxs-lookup"><span data-stu-id="4f9a8-102">DataTable Constraints</span></span>
<span data-ttu-id="4f9a8-103">Você pode usar restrições para impor restrições nos dados em um <xref:System.Data.DataTable>, para manter a integridade dos dados.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-103">You can use constraints to enforce restrictions on the data in a <xref:System.Data.DataTable>, in order to maintain the integrity of the data.</span></span> <span data-ttu-id="4f9a8-104">Uma restrição é uma regra automática, aplicada a uma coluna ou colunas relacionadas, que determina o curso de ação quando o valor de uma linha é modificado de alguma maneira.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-104">A constraint is an automatic rule, applied to a column or related columns, that determines the course of action when the value of a row is somehow altered.</span></span> <span data-ttu-id="4f9a8-105">As restrições são aplicadas quando o `System.Data.DataSet.EnforceConstraints` propriedade o <xref:System.Data.DataSet> é **true**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-105">Constraints are enforced when the `System.Data.DataSet.EnforceConstraints` property of the <xref:System.Data.DataSet> is **true**.</span></span> <span data-ttu-id="4f9a8-106">Para um exemplo de código que mostra como definir a propriedade `EnforceConstraints`, consulte o tópico de referência <xref:System.Data.DataSet.EnforceConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-106">For a code example that shows how to set the `EnforceConstraints` property, see the <xref:System.Data.DataSet.EnforceConstraints%2A> reference topic.</span></span>  
  
 <span data-ttu-id="4f9a8-107">Há dois tipos de restrições no ADO.NET: o <xref:System.Data.ForeignKeyConstraint> e o <xref:System.Data.UniqueConstraint>.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-107">There are two kinds of constraints in ADO.NET: the <xref:System.Data.ForeignKeyConstraint> and the <xref:System.Data.UniqueConstraint>.</span></span> <span data-ttu-id="4f9a8-108">Por padrão, ambas as restrições são criadas automaticamente quando você criar uma relação entre duas ou mais tabelas adicionando um <xref:System.Data.DataRelation> para o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-108">By default, both constraints are created automatically when you create a relationship between two or more tables by adding a <xref:System.Data.DataRelation> to the **DataSet**.</span></span> <span data-ttu-id="4f9a8-109">No entanto, você pode desativar esse comportamento especificando **createConstraints** = **false** ao criar a relação.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-109">However, you can disable this behavior by specifying **createConstraints** = **false** when creating the relation.</span></span>  
  
## <a name="foreignkeyconstraint"></a><span data-ttu-id="4f9a8-110">ForeignKeyConstraint</span><span class="sxs-lookup"><span data-stu-id="4f9a8-110">ForeignKeyConstraint</span></span>  
 <span data-ttu-id="4f9a8-111">Um **ForeignKeyConstraint** impõe regras sobre como as atualizações e exclusões para tabelas relacionadas são propagadas.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-111">A **ForeignKeyConstraint** enforces rules about how updates and deletes to related tables are propagated.</span></span> <span data-ttu-id="4f9a8-112">Por exemplo, se um valor em uma linha de uma tabela é atualizado ou excluído e mesmo valor também é usado em uma ou mais tabelas relacionadas, uma **ForeignKeyConstraint** determina o que acontece nas tabelas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-112">For example, if a value in a row of one table is updated or deleted, and that same value is also used in one or more related tables, a **ForeignKeyConstraint** determines what happens in the related tables.</span></span>  
  
 <span data-ttu-id="4f9a8-113">O <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> e <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> propriedades do **ForeignKeyConstraint** definir a ação a ser tomada quando o usuário tenta excluir ou atualizar uma linha em uma tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-113">The <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> and <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> properties of the **ForeignKeyConstraint** define the action to be taken when the user attempts to delete or update a row in a related table.</span></span> <span data-ttu-id="4f9a8-114">A tabela a seguir descreve as diferentes configurações disponíveis para o **DeleteRule** e **UpdateRule** propriedades do **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-114">The following table describes the different settings available for the **DeleteRule** and **UpdateRule** properties of the **ForeignKeyConstraint**.</span></span>  
  
|<span data-ttu-id="4f9a8-115">Configuração de regra</span><span class="sxs-lookup"><span data-stu-id="4f9a8-115">Rule setting</span></span>|<span data-ttu-id="4f9a8-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f9a8-116">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="4f9a8-117">**Em cascata**</span><span class="sxs-lookup"><span data-stu-id="4f9a8-117">**Cascade**</span></span>|<span data-ttu-id="4f9a8-118">Excluir ou atualizar linhas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-118">Delete or update related rows.</span></span>|  
|<span data-ttu-id="4f9a8-119">**SetNull**</span><span class="sxs-lookup"><span data-stu-id="4f9a8-119">**SetNull**</span></span>|<span data-ttu-id="4f9a8-120">Defina os valores nas linhas relacionadas para **DBNull**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-120">Set values in related rows to **DBNull**.</span></span>|  
|<span data-ttu-id="4f9a8-121">**SetDefault**</span><span class="sxs-lookup"><span data-stu-id="4f9a8-121">**SetDefault**</span></span>|<span data-ttu-id="4f9a8-122">Definir valores em linhas relacionadas para o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-122">Set values in related rows to the default value.</span></span>|  
|<span data-ttu-id="4f9a8-123">**Nenhum**</span><span class="sxs-lookup"><span data-stu-id="4f9a8-123">**None**</span></span>|<span data-ttu-id="4f9a8-124">Nenhuma ação em linhas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-124">Take no action on related rows.</span></span> <span data-ttu-id="4f9a8-125">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-125">This is the default.</span></span>|  
  
 <span data-ttu-id="4f9a8-126">Um **ForeignKeyConstraint** pode restringir, bem como propagar, alterações de colunas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-126">A **ForeignKeyConstraint** can restrict, as well as propagate, changes to related columns.</span></span> <span data-ttu-id="4f9a8-127">Dependendo das propriedades definidas para o **ForeignKeyConstraint** de uma coluna, se o **EnforceConstraints** propriedade o **conjunto de dados** é **true**, executar determinadas operações na linha pai resultará em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-127">Depending on the properties set for the **ForeignKeyConstraint** of a column, if the **EnforceConstraints** property of the **DataSet** is **true**, performing certain operations on the parent row will result in an exception.</span></span> <span data-ttu-id="4f9a8-128">Por exemplo, se o **DeleteRule** propriedade o **ForeignKeyConstraint** é **nenhum**, uma linha pai não pode ser excluída se tiver linhas filho.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-128">For example, if the **DeleteRule** property of the **ForeignKeyConstraint** is **None**, a parent row cannot be deleted if it has any child rows.</span></span>  
  
 <span data-ttu-id="4f9a8-129">Você pode criar uma restrição de chave estrangeira entre colunas únicas ou uma matriz de colunas usando o **ForeignKeyConstraint** construtor.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-129">You can create a foreign key constraint between single columns or between an array of columns by using the **ForeignKeyConstraint** constructor.</span></span> <span data-ttu-id="4f9a8-130">Passar resultante **ForeignKeyConstraint** o objeto para o **adicionar** método da tabela de **restrições** propriedade, que é um **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-130">Pass the resulting **ForeignKeyConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="4f9a8-131">Você também pode passar argumentos de construtor para várias sobrecargas do **adicionar** método de um **ConstraintCollection** para criar um **ForeignKeyConstraint**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-131">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **ForeignKeyConstraint**.</span></span>  
  
 <span data-ttu-id="4f9a8-132">Ao criar um **ForeignKeyConstraint**, você pode passar o **DeleteRule** e **UpdateRule** valores para o construtor como argumentos, ou você podem defini-las como propriedades como o exemplo a seguir (onde o **DeleteRule** valor é definido como **nenhum**).</span><span class="sxs-lookup"><span data-stu-id="4f9a8-132">When creating a **ForeignKeyConstraint**, you can pass the **DeleteRule** and **UpdateRule** values to the constructor as arguments, or you can set them as properties as in the following example (where the **DeleteRule** value is set to **None**).</span></span>  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a><span data-ttu-id="4f9a8-133">AcceptRejectRule</span><span class="sxs-lookup"><span data-stu-id="4f9a8-133">AcceptRejectRule</span></span>  
 <span data-ttu-id="4f9a8-134">Alterações em linhas podem ser aceitos usando o **AcceptChanges** método ou cancelada usando o **RejectChanges** método o **DataSet**, **DataTable**, ou **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-134">Changes to rows can be accepted using the **AcceptChanges** method or canceled using the **RejectChanges** method of the **DataSet**, **DataTable**, or **DataRow**.</span></span> <span data-ttu-id="4f9a8-135">Quando um **DataSet** contém **ForeignKeyConstraints**, invocando o **AcceptChanges** ou **RejectChanges** métodos impõe o  **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-135">When a **DataSet** contains **ForeignKeyConstraints**, invoking the **AcceptChanges** or **RejectChanges** methods enforces the **AcceptRejectRule**.</span></span> <span data-ttu-id="4f9a8-136">O **AcceptRejectRule** propriedade o **ForeignKeyConstraint** determina qual ação será tomada no filho linhas quando **AcceptChanges** ou  **RejectChanges** é chamado em linha pai.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-136">The **AcceptRejectRule** property of the **ForeignKeyConstraint** determines which action will be taken on the child rows when **AcceptChanges** or **RejectChanges** is called on the parent row.</span></span>  
  
 <span data-ttu-id="4f9a8-137">A tabela a seguir lista as configurações disponíveis para o **AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-137">The following table lists the available settings for the **AcceptRejectRule**.</span></span>  
  
|<span data-ttu-id="4f9a8-138">Configuração de regra</span><span class="sxs-lookup"><span data-stu-id="4f9a8-138">Rule setting</span></span>|<span data-ttu-id="4f9a8-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f9a8-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="4f9a8-140">**Em cascata**</span><span class="sxs-lookup"><span data-stu-id="4f9a8-140">**Cascade**</span></span>|<span data-ttu-id="4f9a8-141">Aceitar ou rejeitar alterações em linhas filho.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-141">Accept or reject changes to child rows.</span></span>|  
|<span data-ttu-id="4f9a8-142">**Nenhum**</span><span class="sxs-lookup"><span data-stu-id="4f9a8-142">**None**</span></span>|<span data-ttu-id="4f9a8-143">Nenhuma ação em linhas filho.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-143">Take no action on child rows.</span></span> <span data-ttu-id="4f9a8-144">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-144">This is the default.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="4f9a8-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f9a8-145">Example</span></span>  
 <span data-ttu-id="4f9a8-146">O exemplo a seguir cria um <xref:System.Data.ForeignKeyConstraint>, define várias das suas propriedades, incluindo <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> e adiciona-os ao <xref:System.Data.ConstraintCollection> de um objeto <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-146">The following example creates a <xref:System.Data.ForeignKeyConstraint>, sets several of its properties, including the <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, and adds it to the <xref:System.Data.ConstraintCollection> of a <xref:System.Data.DataTable> object.</span></span>  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a><span data-ttu-id="4f9a8-147">UniqueConstraint</span><span class="sxs-lookup"><span data-stu-id="4f9a8-147">UniqueConstraint</span></span>  
 <span data-ttu-id="4f9a8-148">O **UniqueConstraint** objeto, que pode ser atribuído a uma única coluna ou em uma matriz de colunas em um **DataTable**, garante que todos os dados de coluna ou colunas especificadas é exclusivo por linha.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-148">The **UniqueConstraint** object, which can be assigned either to a single column or to an array of columns in a **DataTable**, ensures that all data in the specified column or columns is unique per row.</span></span> <span data-ttu-id="4f9a8-149">Você pode criar uma restrição exclusiva para uma coluna ou uma matriz de colunas usando o **UniqueConstraint** construtor.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-149">You can create a unique constraint for a column or array of columns by using the **UniqueConstraint** constructor.</span></span> <span data-ttu-id="4f9a8-150">Passar resultante **UniqueConstraint** o objeto para o **adicionar** método da tabela de **restrições** propriedade, que é um **ConstraintCollection**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-150">Pass the resulting **UniqueConstraint** object to the **Add** method of the table's **Constraints** property, which is a **ConstraintCollection**.</span></span> <span data-ttu-id="4f9a8-151">Você também pode passar argumentos de construtor para várias sobrecargas do **adicionar** método de um **ConstraintCollection** para criar um **UniqueConstraint**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-151">You can also pass constructor arguments to several overloads of the **Add** method of a **ConstraintCollection** to create a **UniqueConstraint**.</span></span> <span data-ttu-id="4f9a8-152">Ao criar um **UniqueConstraint** para uma coluna ou colunas, opcionalmente, você pode especificar se a coluna ou colunas são uma chave primária.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-152">When creating a **UniqueConstraint** for a column or columns, you can optionally specify whether the column or columns are a primary key.</span></span>  
  
 <span data-ttu-id="4f9a8-153">Você também pode criar uma restrição exclusiva para uma coluna, definindo o **Unique** propriedade da coluna a ser **true**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-153">You can also create a unique constraint for a column by setting the **Unique** property of the column to **true**.</span></span> <span data-ttu-id="4f9a8-154">Como alternativa, definindo o **Unique** propriedade de uma única coluna para **false** remove qualquer restrição exclusiva que possam existir.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-154">Alternatively, setting the **Unique** property of a single column to **false** removes any unique constraint that may exist.</span></span> <span data-ttu-id="4f9a8-155">Definir uma coluna ou colunas como uma chave primária para uma tabela criará automaticamente uma restrição exclusiva para a coluna ou colunas especificadas.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-155">Defining a column or columns as the primary key for a table will automatically create a unique constraint for the specified column or columns.</span></span> <span data-ttu-id="4f9a8-156">Se você remover uma coluna do **PrimaryKey** propriedade de um **DataTable**, o **UniqueConstraint** é removido.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-156">If you remove a column from the **PrimaryKey** property of a **DataTable**, the **UniqueConstraint** is removed.</span></span>  
  
 <span data-ttu-id="4f9a8-157">O exemplo a seguir cria um **UniqueConstraint** para duas colunas de uma **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="4f9a8-157">The following example creates a **UniqueConstraint** for two columns of a **DataTable**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f9a8-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f9a8-158">See Also</span></span>  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [<span data-ttu-id="4f9a8-159">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="4f9a8-159">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 <span data-ttu-id="4f9a8-160">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="4f9a8-160">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="4f9a8-161">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4f9a8-161">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
