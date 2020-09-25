---
title: Criar colunas AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 9a979f39003e60c70c03206bd886bdd6827c82e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203716"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="fe242-102">Criar colunas AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="fe242-102">Creating AutoIncrement Columns</span></span>

<span data-ttu-id="fe242-103">Para garantir valores de coluna exclusivos, você pode definir os valores de coluna para incrementar automaticamente quando novas linhas forem adicionadas à tabela.</span><span class="sxs-lookup"><span data-stu-id="fe242-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="fe242-104">Para criar um incremento automático <xref:System.Data.DataColumn> , defina a <xref:System.Data.DataColumn.AutoIncrement%2A> propriedade da coluna como **true**.</span><span class="sxs-lookup"><span data-stu-id="fe242-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="fe242-105"><xref:System.Data.DataColumn>Em seguida, começa com o valor definido na <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriedade e, com cada linha adicionada, o valor da coluna **AutoIncrement** aumenta pelo valor definido na <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriedade da coluna.</span><span class="sxs-lookup"><span data-stu-id="fe242-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="fe242-106">Para colunas de **incremento automático** , recomendamos que a <xref:System.Data.DataColumn.ReadOnly%2A> propriedade de **DataColumn** seja definida como **true**.</span><span class="sxs-lookup"><span data-stu-id="fe242-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="fe242-107">O exemplo a seguir demonstra como criar uma coluna que começa com um valor de 200 e adiciona incrementalmente em etapas de 3.</span><span class="sxs-lookup"><span data-stu-id="fe242-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe242-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="fe242-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="fe242-109">Definição do esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="fe242-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="fe242-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="fe242-110">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="fe242-111">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe242-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
