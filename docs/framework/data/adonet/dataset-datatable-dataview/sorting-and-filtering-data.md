---
title: Classificando e filtrando dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 09cee2f2b2c3288c835912c9f311bf2511c7b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785921"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="fbe92-102">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="fbe92-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="fbe92-103">O <xref:System.Data.DataView> fornece várias maneiras de classificar e filtrar dados em uma <xref:System.Data.DataTable>:</span><span class="sxs-lookup"><span data-stu-id="fbe92-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="fbe92-104">Você pode usar a propriedade <xref:System.Data.DataView.Sort%2A> para especificar uma ou várias ordens de classificação de coluna, e para incluir parâmetros ASC (crescente) e DESC (decrescente).</span><span class="sxs-lookup"><span data-stu-id="fbe92-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="fbe92-105">Você pode usar a propriedade <xref:System.Data.DataView.ApplyDefaultSort%2A> para criar automaticamente uma ordem de classificação, em ordem crescente, com base na coluna de chave primária ou nas colunas da tabela.</span><span class="sxs-lookup"><span data-stu-id="fbe92-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="fbe92-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>aplica-se somente quando a propriedade **Sort** é uma referência nula ou uma cadeia de caracteres vazia e quando a tabela tem uma chave primária definida.</span><span class="sxs-lookup"><span data-stu-id="fbe92-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="fbe92-107">Você pode usar a propriedade <xref:System.Data.DataView.RowFilter%2A> para especificar subconjuntos de linhas com base nos valores de coluna.</span><span class="sxs-lookup"><span data-stu-id="fbe92-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="fbe92-108">Para obter detalhes sobre as expressões válidas para a propriedade **userFilter** , consulte as informações <xref:System.Data.DataColumn.Expression%2A> de referência para <xref:System.Data.DataColumn> a propriedade da classe.</span><span class="sxs-lookup"><span data-stu-id="fbe92-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="fbe92-109">Se você quiser retornar os resultados de uma consulta específica nos dados, em vez de fornecer uma exibição dinâmica de um subconjunto dos dados, use os <xref:System.Data.DataView.Find%2A> métodos ou <xref:System.Data.DataView.FindRows%2A> do **DataView** para obter o melhor desempenho em vez de definir oPropriedade de filtro.</span><span class="sxs-lookup"><span data-stu-id="fbe92-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="fbe92-110">A configuração da propriedade **userFilter** recria o índice para os dados, adicionando sobrecarga ao seu aplicativo e diminuindo o desempenho.</span><span class="sxs-lookup"><span data-stu-id="fbe92-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="fbe92-111">A propriedade **doFilter** é melhor usada em um aplicativo associado a dados em que um controle ligado exibe resultados filtrados.</span><span class="sxs-lookup"><span data-stu-id="fbe92-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="fbe92-112">Os métodos **Find** e **FindRows** aproveitam o índice atual sem exigir que o índice seja recriado.</span><span class="sxs-lookup"><span data-stu-id="fbe92-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="fbe92-113">Para obter mais informações sobre os métodos **Find** e **FindRows** , consulte [Localizando linhas](finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="fbe92-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="fbe92-114">Você pode usar a propriedade <xref:System.Data.DataView.RowStateFilter%2A> para especificar quais versões de linha serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="fbe92-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="fbe92-115">O **DataView** gerencia implicitamente qual versão de linha é exposta, dependendo do **RowState** da linha subjacente.</span><span class="sxs-lookup"><span data-stu-id="fbe92-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="fbe92-116">Por exemplo, se **RowStateFilter** for definido como **DataViewRowState. Deleted**, o **DataView** expõe a versão de linha **original** de todas as linhas **excluídas** porque não há nenhuma versão de linha **atual** .</span><span class="sxs-lookup"><span data-stu-id="fbe92-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="fbe92-117">Você pode determinar qual versão de linha de uma linha está sendo exposta usando a **Propriedade rowgroup** do **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="fbe92-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="fbe92-118">A tabela a seguir mostra as opções para **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="fbe92-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="fbe92-119">Opções de DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="fbe92-119">DataViewRowState options</span></span>|<span data-ttu-id="fbe92-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="fbe92-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="fbe92-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="fbe92-121">**CurrentRows**</span></span>|<span data-ttu-id="fbe92-122">A versão de linha **atual** de todas as linhas **inalteradas**, **adicionadas**e **modificadas** .</span><span class="sxs-lookup"><span data-stu-id="fbe92-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="fbe92-123">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="fbe92-123">This is the default.</span></span>|  
    |<span data-ttu-id="fbe92-124">**Mais**</span><span class="sxs-lookup"><span data-stu-id="fbe92-124">**Added**</span></span>|<span data-ttu-id="fbe92-125">A versão de linha **atual** de todas as linhas **adicionadas** .</span><span class="sxs-lookup"><span data-stu-id="fbe92-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="fbe92-126">**Excluí**</span><span class="sxs-lookup"><span data-stu-id="fbe92-126">**Deleted**</span></span>|<span data-ttu-id="fbe92-127">A versão de linha **original** de todas as linhas **excluídas** .</span><span class="sxs-lookup"><span data-stu-id="fbe92-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="fbe92-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="fbe92-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="fbe92-129">A versão da linha **atual** de todas as linhas **modificadas** .</span><span class="sxs-lookup"><span data-stu-id="fbe92-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="fbe92-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="fbe92-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="fbe92-131">A versão de linha **original** de todas as linhas **modificadas** .</span><span class="sxs-lookup"><span data-stu-id="fbe92-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="fbe92-132">**Nenhum**</span><span class="sxs-lookup"><span data-stu-id="fbe92-132">**None**</span></span>|<span data-ttu-id="fbe92-133">Nenhuma linha.</span><span class="sxs-lookup"><span data-stu-id="fbe92-133">No rows.</span></span>|  
    |<span data-ttu-id="fbe92-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="fbe92-134">**OriginalRows**</span></span>|<span data-ttu-id="fbe92-135">A versão de linha **original** de todas as linhas **inalteradas**, **modificadas**e **excluídas** .</span><span class="sxs-lookup"><span data-stu-id="fbe92-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="fbe92-136">**Inalterado**</span><span class="sxs-lookup"><span data-stu-id="fbe92-136">**Unchanged**</span></span>|<span data-ttu-id="fbe92-137">A versão de linha **atual** de todas as linhas **inalteradas** .</span><span class="sxs-lookup"><span data-stu-id="fbe92-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="fbe92-138">Para obter mais informações sobre Estados de linha e versões de linha, consulte [Estados de linha e versões de linha](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="fbe92-138">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="fbe92-139">O exemplo de código a seguir cria uma exibição que mostra todos os produtos em que o número de unidades em estoque é menor ou igual ao nível de reordenação, classificado primeiro por ID do fornecedor e, depois, por nome do produto.</span><span class="sxs-lookup"><span data-stu-id="fbe92-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fbe92-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbe92-140">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="fbe92-141">DataViews</span><span class="sxs-lookup"><span data-stu-id="fbe92-141">DataViews</span></span>](dataviews.md)
- <span data-ttu-id="fbe92-142">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="fbe92-142">[ADO.NET Overview](../ado-net-overview.md)</span></span>
