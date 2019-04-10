---
title: Definir chaves primárias
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 84c84cb8fc0ee484b09c69c72571a19c335b58f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230623"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="24305-102">Definir chaves primárias</span><span class="sxs-lookup"><span data-stu-id="24305-102">Defining Primary Keys</span></span>
<span data-ttu-id="24305-103">Uma tabela de banco de dados geralmente tem uma coluna ou um grupo de colunas que identifica exclusivamente cada linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="24305-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="24305-104">Esta coluna de identificação ou grupo de colunas é chamado de chave primária.</span><span class="sxs-lookup"><span data-stu-id="24305-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="24305-105">Quando você identificar um único <xref:System.Data.DataColumn> como o <xref:System.Data.DataTable.PrimaryKey%2A> para um <xref:System.Data.DataTable>, a tabela define automaticamente o <xref:System.Data.DataColumn.AllowDBNull%2A> propriedade da coluna a ser **falso** e o <xref:System.Data.DataColumn.Unique%2A> propriedade para  **True**.</span><span class="sxs-lookup"><span data-stu-id="24305-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="24305-106">Para várias colunas chaves primárias, somente o **AllowDBNull** propriedade é definida automaticamente como **falso**.</span><span class="sxs-lookup"><span data-stu-id="24305-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="24305-107">O **PrimaryKey** propriedade de uma <xref:System.Data.DataTable> recebe como seu valor de uma matriz de um ou mais **DataColumn** objetos, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="24305-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="24305-108">O primeiro exemplo define uma única coluna como a chave primária.</span><span class="sxs-lookup"><span data-stu-id="24305-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="24305-109">O exemplo a seguir define duas colunas como uma chave primária.</span><span class="sxs-lookup"><span data-stu-id="24305-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24305-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24305-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="24305-111">Definição do esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="24305-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="24305-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="24305-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="24305-113">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="24305-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
