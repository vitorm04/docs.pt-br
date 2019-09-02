---
title: Criar um DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 391c071f19149e9690c9121b1094aef5bfa605cd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203828"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="3d40f-102">Criar um DataView</span><span class="sxs-lookup"><span data-stu-id="3d40f-102">Creating a DataView</span></span>
<span data-ttu-id="3d40f-103">Há duas maneiras de criar um <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="3d40f-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="3d40f-104">Você pode usar o construtor **DataView** ou pode criar uma referência à <xref:System.Data.DataTable.DefaultView%2A> Propriedade do. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="3d40f-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="3d40f-105">O construtor **DataView** pode estar vazio ou pode ter uma **DataTable** como um único argumento, ou uma **DataTable** junto com critérios de filtro, critérios de classificação e um filtro de estado de linha.</span><span class="sxs-lookup"><span data-stu-id="3d40f-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="3d40f-106">Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView**, consulte [classificando e Filtrando dados](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="3d40f-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="3d40f-107">Como o índice de um **DataView** é criado tanto quando o **DataView** é criado, quanto quando qualquer uma das propriedades **Sort**, **RowStateFilter** ou de propriedade é modificada, você obtém o melhor desempenho fornecendo qualquer ordem de classificação ou critérios de filtragem como argumentos de Construtor quando você cria o **DataView**.</span><span class="sxs-lookup"><span data-stu-id="3d40f-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="3d40f-108">A criação de um **DataView** sem especificar critérios de classificação ou de filtro e, em seguida, definir as propriedades **Sort**, userFilter ou **RowStateFilter** posteriormente faz com que o índice seja criado pelo menos duas vezes: uma vez quando o **DataView** é criado e novamente quando qualquer uma das propriedades de classificação ou de filtro é modificada.</span><span class="sxs-lookup"><span data-stu-id="3d40f-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="3d40f-109">Observe que se você criar um **DataView** usando o construtor que não usa argumentos, não será possível usar o **DataView** até que você defina a propriedade **Table** .</span><span class="sxs-lookup"><span data-stu-id="3d40f-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="3d40f-110">O exemplo de código a seguir demonstra como criar um **DataView** usando o construtor **DataView** .</span><span class="sxs-lookup"><span data-stu-id="3d40f-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="3d40f-111">Um **filtro**de lista, coluna de **classificação** e **DataViewRowState** são fornecidos junto com a **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="3d40f-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="3d40f-112">O exemplo de código a seguir demonstra como obter uma referência ao **DataView** padrão de uma **DataTable** usando a propriedade **ModoPadrão** da tabela.</span><span class="sxs-lookup"><span data-stu-id="3d40f-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d40f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d40f-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="3d40f-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="3d40f-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="3d40f-115">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="3d40f-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="3d40f-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="3d40f-116">DataTables</span></span>](datatables.md)
- <span data-ttu-id="3d40f-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="3d40f-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
