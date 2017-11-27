---
title: Classificando e filtrando dados
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
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 01c09d94fd3224e8fd875b7f6eea06b2d2c35cca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="3cf15-102">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="3cf15-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="3cf15-103">O <xref:System.Data.DataView> fornece várias maneiras de classificar e filtrar dados em uma <xref:System.Data.DataTable>:</span><span class="sxs-lookup"><span data-stu-id="3cf15-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="3cf15-104">Você pode usar a propriedade <xref:System.Data.DataView.Sort%2A> para especificar uma ou várias ordens de classificação de coluna, e para incluir parâmetros ASC (crescente) e DESC (decrescente).</span><span class="sxs-lookup"><span data-stu-id="3cf15-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="3cf15-105">Você pode usar a propriedade <xref:System.Data.DataView.ApplyDefaultSort%2A> para criar automaticamente uma ordem de classificação, em ordem crescente, com base na coluna de chave primária ou nas colunas da tabela.</span><span class="sxs-lookup"><span data-stu-id="3cf15-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="3cf15-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>só se aplica quando o **classificação** propriedade é uma referência nula ou uma cadeia de caracteres vazia, e quando a tabela tem uma chave primária definida.</span><span class="sxs-lookup"><span data-stu-id="3cf15-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="3cf15-107">Você pode usar a propriedade <xref:System.Data.DataView.RowFilter%2A> para especificar subconjuntos de linhas com base nos valores de coluna.</span><span class="sxs-lookup"><span data-stu-id="3cf15-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="3cf15-108">Para obter detalhes sobre expressões válidas para o **RowFilter** propriedade, consulte as informações de referência para o <xref:System.Data.DataColumn.Expression%2A> propriedade o <xref:System.Data.DataColumn> classe.</span><span class="sxs-lookup"><span data-stu-id="3cf15-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="3cf15-109">Se você quiser retornar os resultados de uma determinada consulta nos dados, em vez de fornecer uma exibição dinâmica de um subconjunto dos dados, usam o <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> métodos do **DataView** para obter melhor desempenho em vez de Definindo o **RowFilter** propriedade.</span><span class="sxs-lookup"><span data-stu-id="3cf15-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="3cf15-110">Definindo o **RowFilter** propriedade recria o índice para os dados, adicionando sobrecarga para o seu aplicativo e diminuindo o desempenho.</span><span class="sxs-lookup"><span data-stu-id="3cf15-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="3cf15-111">O **RowFilter** propriedade melhor é usada em um aplicativo de associação de dados em que um controle associado exibe resultados filtrados.</span><span class="sxs-lookup"><span data-stu-id="3cf15-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="3cf15-112">O **localizar** e **FindRows** métodos aproveitam o índice atual sem a necessidade do índice seja reconstruído.</span><span class="sxs-lookup"><span data-stu-id="3cf15-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="3cf15-113">Para obter mais informações sobre o **localizar** e **FindRows** métodos, consulte [localizando linhas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="3cf15-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="3cf15-114">Você pode usar a propriedade <xref:System.Data.DataView.RowStateFilter%2A> para especificar quais versões de linha serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="3cf15-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="3cf15-115">O **DataView** implicitamente gerencia qual versão de linha para expor dependendo do **RowState** da linha de base.</span><span class="sxs-lookup"><span data-stu-id="3cf15-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="3cf15-116">Por exemplo, se o **RowStateFilter** é definido como **DataViewRowState.Deleted**, o **DataView** expõe o **Original** versão de linha de todos os **excluído** linhas porque não há nenhum **atual** versão de linha.</span><span class="sxs-lookup"><span data-stu-id="3cf15-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="3cf15-117">Você pode determinar qual versão de linha de uma linha está sendo exposto por meio de **RowVersion** propriedade o **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="3cf15-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="3cf15-118">A tabela a seguir mostra as opções para **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="3cf15-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="3cf15-119">Opções de DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="3cf15-119">DataViewRowState options</span></span>|<span data-ttu-id="3cf15-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="3cf15-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="3cf15-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="3cf15-121">**CurrentRows**</span></span>|<span data-ttu-id="3cf15-122">O **atual** versão de linha de todos os **inalterado**, **adicionado**, e **modificadas** linhas.</span><span class="sxs-lookup"><span data-stu-id="3cf15-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="3cf15-123">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="3cf15-123">This is the default.</span></span>|  
    |<span data-ttu-id="3cf15-124">**Adicionado**</span><span class="sxs-lookup"><span data-stu-id="3cf15-124">**Added**</span></span>|<span data-ttu-id="3cf15-125">O **atual** versão de linha de todos os **adicionado** linhas.</span><span class="sxs-lookup"><span data-stu-id="3cf15-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="3cf15-126">**Excluído**</span><span class="sxs-lookup"><span data-stu-id="3cf15-126">**Deleted**</span></span>|<span data-ttu-id="3cf15-127">O **Original** versão de linha de todos os **excluído** linhas.</span><span class="sxs-lookup"><span data-stu-id="3cf15-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="3cf15-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="3cf15-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="3cf15-129">O **atual** versão de linha de todos os **modificadas** linhas.</span><span class="sxs-lookup"><span data-stu-id="3cf15-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="3cf15-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="3cf15-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="3cf15-131">O **Original** versão de linha de todos os **modificadas** linhas.</span><span class="sxs-lookup"><span data-stu-id="3cf15-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="3cf15-132">**Nenhum**</span><span class="sxs-lookup"><span data-stu-id="3cf15-132">**None**</span></span>|<span data-ttu-id="3cf15-133">Nenhuma linha.</span><span class="sxs-lookup"><span data-stu-id="3cf15-133">No rows.</span></span>|  
    |<span data-ttu-id="3cf15-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="3cf15-134">**OriginalRows**</span></span>|<span data-ttu-id="3cf15-135">O **Original** versão de linha de todos os **inalterado**, **modificadas**, e **excluído** linhas.</span><span class="sxs-lookup"><span data-stu-id="3cf15-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="3cf15-136">**Inalterado**</span><span class="sxs-lookup"><span data-stu-id="3cf15-136">**Unchanged**</span></span>|<span data-ttu-id="3cf15-137">O **atual** versão de linha de todos os **inalterado** linhas.</span><span class="sxs-lookup"><span data-stu-id="3cf15-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="3cf15-138">Para obter mais informações sobre estados de linha e versões de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="3cf15-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="3cf15-139">O exemplo de código a seguir cria uma exibição que mostra todos os produtos em que o número de unidades em estoque é menor ou igual ao nível de reordenação, classificado primeiro por ID do fornecedor e, depois, por nome do produto.</span><span class="sxs-lookup"><span data-stu-id="3cf15-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cf15-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cf15-140">See Also</span></span>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="3cf15-141">DataViews</span><span class="sxs-lookup"><span data-stu-id="3cf15-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="3cf15-142">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3cf15-142">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
