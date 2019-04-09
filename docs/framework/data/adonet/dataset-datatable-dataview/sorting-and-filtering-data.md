---
title: Classificando e filtrando dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 8d8bd85f65adfde5f239e1e2dd79d65517b745a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166238"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="24a23-102">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="24a23-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="24a23-103">O <xref:System.Data.DataView> fornece várias maneiras de classificar e filtrar dados em uma <xref:System.Data.DataTable>:</span><span class="sxs-lookup"><span data-stu-id="24a23-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="24a23-104">Você pode usar a propriedade <xref:System.Data.DataView.Sort%2A> para especificar uma ou várias ordens de classificação de coluna, e para incluir parâmetros ASC (crescente) e DESC (decrescente).</span><span class="sxs-lookup"><span data-stu-id="24a23-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="24a23-105">Você pode usar a propriedade <xref:System.Data.DataView.ApplyDefaultSort%2A> para criar automaticamente uma ordem de classificação, em ordem crescente, com base na coluna de chave primária ou nas colunas da tabela.</span><span class="sxs-lookup"><span data-stu-id="24a23-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <xref:System.Data.DataView.ApplyDefaultSort%2A> <span data-ttu-id="24a23-106">se aplica somente quando o **classificação** propriedade é uma referência nula ou uma cadeia de caracteres vazia, e quando a tabela tem uma chave primária definida.</span><span class="sxs-lookup"><span data-stu-id="24a23-106">only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="24a23-107">Você pode usar a propriedade <xref:System.Data.DataView.RowFilter%2A> para especificar subconjuntos de linhas com base nos valores de coluna.</span><span class="sxs-lookup"><span data-stu-id="24a23-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="24a23-108">Para obter detalhes sobre expressões válidas para o **RowFilter** propriedade, consulte as informações de referência para o <xref:System.Data.DataColumn.Expression%2A> propriedade do <xref:System.Data.DataColumn> classe.</span><span class="sxs-lookup"><span data-stu-id="24a23-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="24a23-109">Se você quiser retornar os resultados de uma consulta específica nos dados, em vez de fornecer uma exibição dinâmica de um subconjunto dos dados, use o <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> métodos das **DataView** para obter melhor desempenho em vez de Definindo o **RowFilter** propriedade.</span><span class="sxs-lookup"><span data-stu-id="24a23-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="24a23-110">Definindo o **RowFilter** propriedade recria o índice para os dados, adicionando a sobrecarga ao seu aplicativo e prejudicando o desempenho.</span><span class="sxs-lookup"><span data-stu-id="24a23-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="24a23-111">O **RowFilter** propriedade é melhor usada em um aplicativo associado a dados em que um controle associado exibe resultados filtrados.</span><span class="sxs-lookup"><span data-stu-id="24a23-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="24a23-112">O **encontrar** e **FindRows** métodos aproveitam o índice atual sem exigir que o índice seja reconstruído.</span><span class="sxs-lookup"><span data-stu-id="24a23-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="24a23-113">Para obter mais informações sobre o **encontrar** e **FindRows** métodos, consulte [localizando linhas](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="24a23-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="24a23-114">Você pode usar a propriedade <xref:System.Data.DataView.RowStateFilter%2A> para especificar quais versões de linha serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="24a23-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="24a23-115">O **DataView** gerencia implicitamente qual versão de linha para expor de acordo com as **RowState** da linha subjacente.</span><span class="sxs-lookup"><span data-stu-id="24a23-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="24a23-116">Por exemplo, se o **RowStateFilter** é definido como **DataViewRowState. Deleted**, o **DataView** expõe o **Original** versão da linha todos os **Deleted** linhas porque não há nenhuma **atual** versão de linha.</span><span class="sxs-lookup"><span data-stu-id="24a23-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="24a23-117">Você pode determinar qual versão de linha de uma linha está sendo exposto usando o **RowVersion** propriedade da **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="24a23-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="24a23-118">A tabela a seguir mostra as opções para **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="24a23-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="24a23-119">Opções de DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="24a23-119">DataViewRowState options</span></span>|<span data-ttu-id="24a23-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="24a23-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |**<span data-ttu-id="24a23-121">CurrentRows</span><span class="sxs-lookup"><span data-stu-id="24a23-121">CurrentRows</span></span>**|<span data-ttu-id="24a23-122">O **atual** versão de linha de todas as **inalterado**, **adicionado**, e **modificado** linhas.</span><span class="sxs-lookup"><span data-stu-id="24a23-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="24a23-123">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="24a23-123">This is the default.</span></span>|  
    |**<span data-ttu-id="24a23-124">Added</span><span class="sxs-lookup"><span data-stu-id="24a23-124">Added</span></span>**|<span data-ttu-id="24a23-125">O **atual** versão de linha de todas as **adicionado** linhas.</span><span class="sxs-lookup"><span data-stu-id="24a23-125">The **Current** row version of all **Added** rows.</span></span>|  
    |**<span data-ttu-id="24a23-126">Deleted</span><span class="sxs-lookup"><span data-stu-id="24a23-126">Deleted</span></span>**|<span data-ttu-id="24a23-127">O **Original** versão de linha de todas as **Deleted** linhas.</span><span class="sxs-lookup"><span data-stu-id="24a23-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |**<span data-ttu-id="24a23-128">ModifiedCurrent</span><span class="sxs-lookup"><span data-stu-id="24a23-128">ModifiedCurrent</span></span>**|<span data-ttu-id="24a23-129">O **atual** versão de linha de todas as **modificado** linhas.</span><span class="sxs-lookup"><span data-stu-id="24a23-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |**<span data-ttu-id="24a23-130">ModifiedOriginal</span><span class="sxs-lookup"><span data-stu-id="24a23-130">ModifiedOriginal</span></span>**|<span data-ttu-id="24a23-131">O **Original** versão de linha de todas as **modificado** linhas.</span><span class="sxs-lookup"><span data-stu-id="24a23-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |**<span data-ttu-id="24a23-132">Nenhum</span><span class="sxs-lookup"><span data-stu-id="24a23-132">None</span></span>**|<span data-ttu-id="24a23-133">Nenhuma linha.</span><span class="sxs-lookup"><span data-stu-id="24a23-133">No rows.</span></span>|  
    |**<span data-ttu-id="24a23-134">OriginalRows</span><span class="sxs-lookup"><span data-stu-id="24a23-134">OriginalRows</span></span>**|<span data-ttu-id="24a23-135">O **Original** versão de linha de todas as **inalterado**, **modificado**, e **Deleted** linhas.</span><span class="sxs-lookup"><span data-stu-id="24a23-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |**<span data-ttu-id="24a23-136">Unchanged</span><span class="sxs-lookup"><span data-stu-id="24a23-136">Unchanged</span></span>**|<span data-ttu-id="24a23-137">O **atual** versão de linha de todas as **inalterado** linhas.</span><span class="sxs-lookup"><span data-stu-id="24a23-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="24a23-138">Para obter mais informações sobre estados de linha e versões de linha, consulte [estados de linha e versões de linha](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="24a23-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="24a23-139">O exemplo de código a seguir cria uma exibição que mostra todos os produtos em que o número de unidades em estoque é menor ou igual ao nível de reordenação, classificado primeiro por ID do fornecedor e, depois, por nome do produto.</span><span class="sxs-lookup"><span data-stu-id="24a23-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24a23-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24a23-140">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="24a23-141">DataViews</span><span class="sxs-lookup"><span data-stu-id="24a23-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [<span data-ttu-id="24a23-142">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="24a23-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
