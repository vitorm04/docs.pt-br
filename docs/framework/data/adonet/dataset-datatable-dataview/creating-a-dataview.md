---
title: Criando um DataView
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 53cbfc5097c28c0677a164f817cfe14927814d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataview"></a><span data-ttu-id="228c9-102">Criando um DataView</span><span class="sxs-lookup"><span data-stu-id="228c9-102">Creating a DataView</span></span>
<span data-ttu-id="228c9-103">Há duas maneiras de criar um <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="228c9-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="228c9-104">Você pode usar o **DataView** construtor, ou você pode criar uma referência para o <xref:System.Data.DataTable.DefaultView%2A> propriedade o <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="228c9-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="228c9-105">O **DataView** construtor pode estar vazia ou pode levar a um **DataTable** como um único argumento, ou um **DataTable** juntamente com os critérios de filtro, os critérios de classificação e uma linha filtro de estado.</span><span class="sxs-lookup"><span data-stu-id="228c9-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="228c9-106">Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView**, consulte [classificando e filtrando dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="228c9-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="228c9-107">Porque o índice para uma **DataView** baseia-se ambos os quando o **DataView** é criado e quando qualquer uma da **classificação**, **RowFilter**, ou  **RowStateFilter** propriedades são modificadas, você obter melhor desempenho, fornecendo uma ordem de classificação inicial ou critérios de filtragem como argumentos de construtor quando você cria o **DataView**.</span><span class="sxs-lookup"><span data-stu-id="228c9-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="228c9-108">Criando um **DataView** sem especificar critérios de classificação ou filtragem e, em seguida, definindo o **classificação**, **RowFilter**, ou **RowStateFilter** propriedades posteriormente faz com que o índice seja criado pelo menos duas vezes: depois de quando o **DataView** é criado, e novamente quando qualquer uma das propriedades de classificação ou filtro são modificados.</span><span class="sxs-lookup"><span data-stu-id="228c9-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="228c9-109">Observe que, se você criar um **DataView** usando o construtor que não tem nenhum argumento, você não poderá usar o **DataView** até que você definiu o **tabela** propriedade .</span><span class="sxs-lookup"><span data-stu-id="228c9-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="228c9-110">O exemplo de código a seguir demonstra como criar um **DataView** usando o **DataView** construtor.</span><span class="sxs-lookup"><span data-stu-id="228c9-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="228c9-111">Um **RowFilter**, **classificação** coluna, e **DataViewRowState** são fornecidos junto com o **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="228c9-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 <span data-ttu-id="228c9-112">O exemplo de código a seguir demonstra como obter uma referência para o padrão **DataView** de um **DataTable** usando o **DefaultView** propriedade da tabela.</span><span class="sxs-lookup"><span data-stu-id="228c9-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="228c9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="228c9-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="228c9-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="228c9-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="228c9-115">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="228c9-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="228c9-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="228c9-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="228c9-117">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="228c9-117">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
