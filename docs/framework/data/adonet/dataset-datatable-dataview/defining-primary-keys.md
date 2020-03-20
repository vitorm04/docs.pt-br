---
title: Definir chaves primárias
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 159b23eb4ef5ca38ebce6e488080d315ec3be081
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151176"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="493c3-102">Definir chaves primárias</span><span class="sxs-lookup"><span data-stu-id="493c3-102">Defining Primary Keys</span></span>
<span data-ttu-id="493c3-103">Uma tabela de banco de dados geralmente tem uma coluna ou grupo de colunas que identifica exclusivamente cada linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="493c3-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="493c3-104">Esta coluna de identificação ou grupo de colunas é chamada de chave primária.</span><span class="sxs-lookup"><span data-stu-id="493c3-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="493c3-105">Quando você identifica <xref:System.Data.DataColumn> um <xref:System.Data.DataTable.PrimaryKey%2A> único <xref:System.Data.DataTable>como o de <xref:System.Data.DataColumn.AllowDBNull%2A> a , a tabela <xref:System.Data.DataColumn.Unique%2A> define automaticamente a propriedade da coluna como **falsa** e a propriedade como **verdadeira**.</span><span class="sxs-lookup"><span data-stu-id="493c3-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="493c3-106">Para chaves primárias de várias colunas, apenas a propriedade **AllowDBNull** é definida automaticamente como **falsa**.</span><span class="sxs-lookup"><span data-stu-id="493c3-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="493c3-107">A propriedade **PrimaryKey** de um <xref:System.Data.DataTable> recebe como valor uma matriz de um ou mais objetos **dataColumn,** como mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="493c3-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="493c3-108">O primeiro exemplo define uma única coluna como a chave principal.</span><span class="sxs-lookup"><span data-stu-id="493c3-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="493c3-109">O exemplo a seguir define duas colunas como uma chave primária.</span><span class="sxs-lookup"><span data-stu-id="493c3-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="493c3-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="493c3-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="493c3-111">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="493c3-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="493c3-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="493c3-112">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="493c3-113">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="493c3-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
