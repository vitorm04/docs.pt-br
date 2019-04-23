---
title: Criar um DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 05122f7c980c4b7dfdb27eec73464a4f0556ba99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096674"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="1ec40-102">Criar um DataView</span><span class="sxs-lookup"><span data-stu-id="1ec40-102">Creating a DataView</span></span>
<span data-ttu-id="1ec40-103">Há duas maneiras de criar um <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="1ec40-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="1ec40-104">Você pode usar o **DataView** construtor, ou você pode criar uma referência para o <xref:System.Data.DataTable.DefaultView%2A> propriedade do <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="1ec40-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1ec40-105">O **DataView** construtor pode estar vazia ou pode levar a um **DataTable** como um único argumento, ou uma **DataTable** juntamente com os critérios de filtro, critérios de classificação e uma linha filtro de estado.</span><span class="sxs-lookup"><span data-stu-id="1ec40-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="1ec40-106">Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView**, consulte [classificando e filtrando dados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="1ec40-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="1ec40-107">Porque o índice para uma **DataView** é compilado quando o **DataView** é criado e quando qualquer um dos **classificação**, **RowFilter**, ou  **RowStateFilter** propriedades são modificadas, você obter o melhor desempenho, fornecendo uma ordem de classificação inicial ou critérios de filtragem como argumentos de construtor quando você cria o **DataView**.</span><span class="sxs-lookup"><span data-stu-id="1ec40-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="1ec40-108">Criando um **DataView** sem especificar critérios de classificação ou filtragem e, em seguida, definindo o **classificação**, **RowFilter**, ou **RowStateFilter** propriedades posteriormente faz com que o índice a ser compilado pelo menos duas vezes: depois de quando o **DataView** é criado, e novamente quando qualquer uma das propriedades de classificação ou filtragem são alteradas.</span><span class="sxs-lookup"><span data-stu-id="1ec40-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="1ec40-109">Observe que, se você criar uma **DataView** usando o construtor que não leva argumentos, você não poderá usar o **DataView** até que você tenha definido o **tabela** propriedade .</span><span class="sxs-lookup"><span data-stu-id="1ec40-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="1ec40-110">O exemplo de código a seguir demonstra como criar uma **DataView** usando o **DataView** construtor.</span><span class="sxs-lookup"><span data-stu-id="1ec40-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="1ec40-111">Um **RowFilter**, **classificação** coluna, e **DataViewRowState** são fornecidos juntamente com o **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="1ec40-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="1ec40-112">O exemplo de código a seguir demonstra como obter uma referência para o padrão **DataView** de uma **DataTable** usando o **DefaultView** propriedade da tabela.</span><span class="sxs-lookup"><span data-stu-id="1ec40-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ec40-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ec40-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="1ec40-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="1ec40-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [<span data-ttu-id="1ec40-115">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="1ec40-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)
- [<span data-ttu-id="1ec40-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="1ec40-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- <span data-ttu-id="1ec40-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1ec40-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
