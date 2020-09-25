---
title: Definir chaves primárias
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 94b033d58061e3d2e48a352d782eec7c4202fa43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166827"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="48906-102">Definir chaves primárias</span><span class="sxs-lookup"><span data-stu-id="48906-102">Defining Primary Keys</span></span>

<span data-ttu-id="48906-103">Uma tabela de banco de dados normalmente tem uma coluna ou grupo de colunas que identifica exclusivamente cada linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="48906-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="48906-104">Essa coluna de identificação ou grupo de colunas é chamada de chave primária.</span><span class="sxs-lookup"><span data-stu-id="48906-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="48906-105">Quando você identifica um único <xref:System.Data.DataColumn> como o <xref:System.Data.DataTable.PrimaryKey%2A> para um <xref:System.Data.DataTable> , a tabela define automaticamente a <xref:System.Data.DataColumn.AllowDBNull%2A> propriedade da coluna como **false** e a <xref:System.Data.DataColumn.Unique%2A> propriedade como **true**.</span><span class="sxs-lookup"><span data-stu-id="48906-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="48906-106">Para chaves primárias de várias colunas, somente a propriedade **AllowDBNull** é definida automaticamente como **false**.</span><span class="sxs-lookup"><span data-stu-id="48906-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="48906-107">A propriedade **PrimaryKey** de um <xref:System.Data.DataTable> recebe como seu valor uma matriz de um ou mais objetos **DataColumn** , conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="48906-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="48906-108">O primeiro exemplo define uma única coluna como a chave primária.</span><span class="sxs-lookup"><span data-stu-id="48906-108">The first example defines a single column as the primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 <span data-ttu-id="48906-109">O exemplo a seguir define duas colunas como uma chave primária.</span><span class="sxs-lookup"><span data-stu-id="48906-109">The following example defines two columns as a primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a><span data-ttu-id="48906-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="48906-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="48906-111">Definição do esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="48906-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="48906-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="48906-112">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="48906-113">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="48906-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
