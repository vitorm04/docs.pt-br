---
title: Criar um DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151332"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="d5970-102">Criar um DataView</span><span class="sxs-lookup"><span data-stu-id="d5970-102">Creating a DataView</span></span>
<span data-ttu-id="d5970-103">Há duas maneiras de criar um <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="d5970-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="d5970-104">Você pode usar o construtor **DataView** ou criar <xref:System.Data.DataTable.DefaultView%2A> uma referência <xref:System.Data.DataTable>à propriedade do .</span><span class="sxs-lookup"><span data-stu-id="d5970-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d5970-105">O construtor **DataView** pode estar vazio ou pode tomar uma **Tabela de Dados** como um único argumento ou uma Tabela de **Dados,** juntamente com critérios de filtro, critérios de classificação e um filtro de estado de linha.</span><span class="sxs-lookup"><span data-stu-id="d5970-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="d5970-106">Para obter mais informações sobre os argumentos adicionais disponíveis para uso com o **DataView,** consulte [Dados de classificação e filtragem](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="d5970-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="d5970-107">Como o índice de um **DataView** é construído tanto quando o **DataView** é criado, quanto quando qualquer uma das propriedades **Sort**, **RowFilter**ou **RowStateFilter** são modificadas, você obtém o melhor desempenho fornecendo qualquer ordem de classificação inicial ou critérios de filtragem como argumentos de construtor quando você cria o **DataView**.</span><span class="sxs-lookup"><span data-stu-id="d5970-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="d5970-108">Criar um **DataView** sem especificar critérios de classificação ou filtro e, em seguida, definir as propriedades **Classificar,** **RowFilter**ou **RowStateFilter** mais tarde faz com que o índice seja construído pelo menos duas vezes: uma vez quando o **DataView** é criado e novamente quando qualquer um dos tipos ou propriedades do filtro for modificado.</span><span class="sxs-lookup"><span data-stu-id="d5970-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="d5970-109">Observe que se você criar um **DataView** usando o construtor que não tenha argumentos, você não poderá usar o **DataView** até definir a propriedade **Tabela.**</span><span class="sxs-lookup"><span data-stu-id="d5970-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="d5970-110">O exemplo de código a seguir demonstra como criar um **DataView** usando o construtor **DataView.**</span><span class="sxs-lookup"><span data-stu-id="d5970-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="d5970-111">Uma **coluna RowFilter**, **Sort** e **DataViewRowState** são fornecidas juntamente com a **Tabela de Dados**.</span><span class="sxs-lookup"><span data-stu-id="d5970-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="d5970-112">O exemplo de código a seguir demonstra como obter uma referência ao **DataView** padrão de uma Tabela de **Dados** usando a propriedade **DefaultView** da tabela.</span><span class="sxs-lookup"><span data-stu-id="d5970-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5970-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="d5970-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="d5970-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="d5970-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="d5970-115">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="d5970-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="d5970-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="d5970-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="d5970-117">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d5970-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
