---
title: Adicionando DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: d0f481979ead7af775d462a2624ec43080e2c5a9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399188"
---
# <a name="adding-datarelations"></a><span data-ttu-id="59873-102">Adicionando DataRelations</span><span class="sxs-lookup"><span data-stu-id="59873-102">Adding DataRelations</span></span>
<span data-ttu-id="59873-103">Em um <xref:System.Data.DataSet> com vários objetos <xref:System.Data.DataTable>, você pode usar objetos <xref:System.Data.DataRelation> para relacionar uma tabela a outra, para navegar pelas tabelas e para retornar as linhas filho ou pai de uma tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="59873-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="59873-104">Os argumentos necessários para criar uma **DataRelation** são um nome para o **DataRelation** que está sendo criado e uma matriz de um ou mais <xref:System.Data.DataColumn> referências para as colunas que servem como o pai e filho colunas na relação.</span><span class="sxs-lookup"><span data-stu-id="59873-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="59873-105">Depois de criar uma **DataRelation**, você pode usá-lo para navegar entre as tabelas e para recuperar valores.</span><span class="sxs-lookup"><span data-stu-id="59873-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="59873-106">Adicionando um **DataRelation** para um <xref:System.Data.DataSet> adiciona, por padrão, uma <xref:System.Data.UniqueConstraint> para a tabela pai e um <xref:System.Data.ForeignKeyConstraint> à tabela filho.</span><span class="sxs-lookup"><span data-stu-id="59873-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="59873-107">Para obter mais informações sobre essas restrições padrão, consulte [restrições de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="59873-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="59873-108">O exemplo de código a seguir cria uma **DataRelation** usando duas <xref:System.Data.DataTable> objetos em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="59873-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="59873-109">Cada <xref:System.Data.DataTable> contém uma coluna denominada **CustID**, que serve como um link entre os dois <xref:System.Data.DataTable> objetos.</span><span class="sxs-lookup"><span data-stu-id="59873-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="59873-110">O exemplo adiciona um único **DataRelation** para o **relações** coleção do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="59873-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="59873-111">O primeiro argumento, o exemplo especifica o nome da **DataRelation** que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="59873-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="59873-112">O segundo argumento define o pai **DataColumn** e o terceiro argumento define o filho **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="59873-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
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
  
 <span data-ttu-id="59873-113">Um **DataRelation** também tem um **Nested** propriedade que, quando definido como **verdadeiro**, faz com que as linhas da tabela filho sejam aninhadas na linha associada da tabela pai quando gravadas como elementos XML usando <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="59873-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="59873-114">Para obter mais informações, consulte [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).</span><span class="sxs-lookup"><span data-stu-id="59873-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59873-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59873-115">See Also</span></span>  
 <span data-ttu-id="59873-116">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="59873-116">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="59873-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="59873-117">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
