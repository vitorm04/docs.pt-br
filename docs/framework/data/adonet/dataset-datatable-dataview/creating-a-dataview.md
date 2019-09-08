---
title: Criar um DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 3e1c31dac458594eee70ddd99469aca7cf63b848
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785480"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="18ad9-102">Criar um DataView</span><span class="sxs-lookup"><span data-stu-id="18ad9-102">Creating a DataView</span></span>
<span data-ttu-id="18ad9-103">Há duas maneiras de criar um <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="18ad9-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="18ad9-104">Você pode usar o construtor **DataView** ou pode criar uma referência à <xref:System.Data.DataTable.DefaultView%2A> Propriedade do. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="18ad9-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="18ad9-105">O construtor **DataView** pode estar vazio ou pode ter uma **DataTable** como um único argumento, ou uma **DataTable** junto com critérios de filtro, critérios de classificação e um filtro de estado de linha.</span><span class="sxs-lookup"><span data-stu-id="18ad9-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="18ad9-106">Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView**, consulte [classificando e Filtrando dados](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="18ad9-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="18ad9-107">Como o índice de um **DataView** é criado tanto quando o **DataView** é criado, quanto quando qualquer uma das propriedades **Sort**, **RowStateFilter** **ou de propriedade**é modificada, você obtém o melhor desempenho fornecendo qualquer ordem de classificação ou critérios de filtragem como argumentos de Construtor quando você cria o **DataView**.</span><span class="sxs-lookup"><span data-stu-id="18ad9-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="18ad9-108">A criação de um **DataView** sem especificar critérios de classificação ou de filtro e, em seguida, definir as propriedades **Sort**, **userFilter**ou **RowStateFilter** posteriormente faz com que o índice seja criado pelo menos duas vezes: uma vez quando o **DataView** é criado e novamente quando qualquer uma das propriedades de classificação ou de filtro é modificada.</span><span class="sxs-lookup"><span data-stu-id="18ad9-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="18ad9-109">Observe que se você criar um **DataView** usando o construtor que não usa argumentos, não será possível usar o **DataView** até que você defina a propriedade **Table** .</span><span class="sxs-lookup"><span data-stu-id="18ad9-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="18ad9-110">O exemplo de código a seguir demonstra como criar um **DataView** usando o construtor **DataView** .</span><span class="sxs-lookup"><span data-stu-id="18ad9-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="18ad9-111">Um **filtro**de lista, coluna de **classificação** e **DataViewRowState** são fornecidos junto com a **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="18ad9-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="18ad9-112">O exemplo de código a seguir demonstra como obter uma referência ao **DataView** padrão de uma **DataTable** usando a propriedade **ModoPadrão** da tabela.</span><span class="sxs-lookup"><span data-stu-id="18ad9-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="18ad9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18ad9-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="18ad9-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="18ad9-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="18ad9-115">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="18ad9-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="18ad9-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="18ad9-116">DataTables</span></span>](datatables.md)
- <span data-ttu-id="18ad9-117">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="18ad9-117">[ADO.NET Overview](../ado-net-overview.md)</span></span>
