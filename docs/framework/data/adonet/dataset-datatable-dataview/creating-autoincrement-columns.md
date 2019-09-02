---
title: Criar colunas AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205137"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="f37d8-102">Criar colunas AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="f37d8-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="f37d8-103">Para garantir valores de coluna exclusivos, você pode definir os valores de coluna para incrementar automaticamente quando novas linhas forem adicionadas à tabela.</span><span class="sxs-lookup"><span data-stu-id="f37d8-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="f37d8-104">Para criar um incremento <xref:System.Data.DataColumn>automático, defina a <xref:System.Data.DataColumn.AutoIncrement%2A> propriedade da coluna como **true**.</span><span class="sxs-lookup"><span data-stu-id="f37d8-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="f37d8-105">Em seguida, começa com o <xref:System.Data.DataColumn.AutoIncrementSeed%2A> valor definido na propriedade e, com cada linha adicionada, o valor da coluna AutoIncrement <xref:System.Data.DataColumn.AutoIncrementStep%2A> aumenta pelo valor definido na propriedade da coluna. <xref:System.Data.DataColumn></span><span class="sxs-lookup"><span data-stu-id="f37d8-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="f37d8-106">Para colunas de **incremento automático** , recomendamos <xref:System.Data.DataColumn.ReadOnly%2A> que a propriedade de **DataColumn** seja definida como **true**.</span><span class="sxs-lookup"><span data-stu-id="f37d8-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="f37d8-107">O exemplo a seguir demonstra como criar uma coluna que começa com um valor de 200 e adiciona incrementalmente em etapas de 3.</span><span class="sxs-lookup"><span data-stu-id="f37d8-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f37d8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f37d8-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="f37d8-109">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="f37d8-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="f37d8-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="f37d8-110">DataTables</span></span>](datatables.md)
- <span data-ttu-id="f37d8-111">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="f37d8-111">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
