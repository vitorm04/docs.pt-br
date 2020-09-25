---
title: Adicionando DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 5fe2bd45e0abada1f9ec7071e3863da853479b51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202377"
---
# <a name="adding-datarelations"></a><span data-ttu-id="2e192-102">Adicionando DataRelations</span><span class="sxs-lookup"><span data-stu-id="2e192-102">Adding DataRelations</span></span>

<span data-ttu-id="2e192-103">Em um <xref:System.Data.DataSet> com vários objetos <xref:System.Data.DataTable>, você pode usar objetos <xref:System.Data.DataRelation> para relacionar uma tabela a outra, para navegar pelas tabelas e para retornar as linhas filho ou pai de uma tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="2e192-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="2e192-104">Os argumentos necessários para criar uma **DataRelation** são um nome para a **DataRelation** que está sendo criada e uma matriz de uma ou mais <xref:System.Data.DataColumn> referências às colunas que servem como as colunas pai e filho na relação.</span><span class="sxs-lookup"><span data-stu-id="2e192-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="2e192-105">Depois de criar uma **DataRelation**, você pode usá-la para navegar entre tabelas e recuperar valores.</span><span class="sxs-lookup"><span data-stu-id="2e192-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="2e192-106">Adicionar uma **DataRelation** a um <xref:System.Data.DataSet> ADDS, por padrão, a <xref:System.Data.UniqueConstraint> à tabela pai e a <xref:System.Data.ForeignKeyConstraint> à tabela filho.</span><span class="sxs-lookup"><span data-stu-id="2e192-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="2e192-107">Para obter mais informações sobre essas restrições padrão, consulte as [restrições de DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="2e192-107">For more information about these default constraints, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="2e192-108">O exemplo de código a seguir cria uma **DataRelation** usando dois <xref:System.Data.DataTable> objetos em um <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="2e192-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="2e192-109">Cada <xref:System.Data.DataTable> contém uma coluna chamada **CustID**, que serve como um link entre os dois <xref:System.Data.DataTable> objetos.</span><span class="sxs-lookup"><span data-stu-id="2e192-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="2e192-110">O exemplo adiciona uma única **DataRelation** à coleção **Relations** do <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="2e192-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="2e192-111">O primeiro argumento no exemplo especifica o nome da **DataRelation** que está sendo criada.</span><span class="sxs-lookup"><span data-stu-id="2e192-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="2e192-112">O segundo argumento define a **DataColumn** pai e o terceiro argumento define o filho **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="2e192-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="2e192-113">Uma **DataRelation** também tem uma propriedade **aninhada** que, quando definida como **true**, faz com que as linhas da tabela filho sejam aninhadas dentro da linha associada da tabela pai quando gravadas como elementos XML usando <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="2e192-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="2e192-114">Para obter mais informações, consulte [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet).</span><span class="sxs-lookup"><span data-stu-id="2e192-114">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e192-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="2e192-115">See also</span></span>

- [<span data-ttu-id="2e192-116">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="2e192-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="2e192-117">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2e192-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
