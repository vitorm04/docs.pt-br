---
title: "Criar colunas de incremento automático"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7bc71e3ae817bbdaf5dc14f22041e297cab949b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="d36ab-102">Criar colunas de incremento automático</span><span class="sxs-lookup"><span data-stu-id="d36ab-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="d36ab-103">Para garantir que os valores de coluna exclusiva, você pode definir os valores de coluna para incrementar automaticamente quando novas linhas são adicionadas à tabela.</span><span class="sxs-lookup"><span data-stu-id="d36ab-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="d36ab-104">Para criar um incremento automático <xref:System.Data.DataColumn>, defina o <xref:System.Data.DataColumn.AutoIncrement%2A> propriedade da coluna a ser **true**.</span><span class="sxs-lookup"><span data-stu-id="d36ab-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="d36ab-105">O <xref:System.Data.DataColumn> , em seguida, começa com o valor definido no <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriedade e cada linha adicionada o valor da **AutoIncrement** coluna aumenta o valor definido no <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriedade da coluna.</span><span class="sxs-lookup"><span data-stu-id="d36ab-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="d36ab-106">Para **AutoIncrement** colunas, é recomendável que o <xref:System.Data.DataColumn.ReadOnly%2A> propriedade o **DataColumn** ser definido como **true**.</span><span class="sxs-lookup"><span data-stu-id="d36ab-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="d36ab-107">O exemplo a seguir demonstra como criar uma coluna que começa com um valor de 200 e adiciona incrementalmente nas etapas de 3.</span><span class="sxs-lookup"><span data-stu-id="d36ab-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d36ab-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d36ab-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="d36ab-109">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="d36ab-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="d36ab-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="d36ab-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="d36ab-111">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d36ab-111">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
