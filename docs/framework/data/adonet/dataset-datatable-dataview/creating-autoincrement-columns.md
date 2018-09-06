---
title: Criando colunas de incremento automático
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 9c6b5393e1928828bca001ba1d2336f09e64c22c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776931"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="f7033-102">Criando colunas de incremento automático</span><span class="sxs-lookup"><span data-stu-id="f7033-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="f7033-103">Para garantir que os valores de coluna exclusiva, você pode definir os valores de coluna para incrementar automaticamente quando novas linhas são adicionadas à tabela.</span><span class="sxs-lookup"><span data-stu-id="f7033-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="f7033-104">Para criar um incremento automático <xref:System.Data.DataColumn>, defina a <xref:System.Data.DataColumn.AutoIncrement%2A> propriedade da coluna a ser **verdadeiro**.</span><span class="sxs-lookup"><span data-stu-id="f7033-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="f7033-105">O <xref:System.Data.DataColumn> , em seguida, começa com o valor definido na <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriedade e, em cada linha adicionada o valor da **AutoIncrement** aumenta o valor definido na coluna a <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriedade da coluna.</span><span class="sxs-lookup"><span data-stu-id="f7033-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="f7033-106">Para **AutoIncrement** colunas, é recomendável que o <xref:System.Data.DataColumn.ReadOnly%2A> propriedade do **DataColumn** ser definido como **true**.</span><span class="sxs-lookup"><span data-stu-id="f7033-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="f7033-107">O exemplo a seguir demonstra como criar uma coluna que começa com um valor de 200 e adiciona de forma incremental nas etapas de 3.</span><span class="sxs-lookup"><span data-stu-id="f7033-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7033-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7033-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="f7033-109">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="f7033-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="f7033-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="f7033-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="f7033-111">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f7033-111">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
