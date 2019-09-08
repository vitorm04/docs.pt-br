---
title: Definir chaves primárias
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 0f87b1b730eecf0edad75bd87ca8b491b96e1d2b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784714"
---
# <a name="defining-primary-keys"></a>Definir chaves primárias
Uma tabela de banco de dados normalmente tem uma coluna ou grupo de colunas que identifica exclusivamente cada linha na tabela. Essa coluna de identificação ou grupo de colunas é chamada de chave primária.  
  
 Quando você identifica um único <xref:System.Data.DataColumn> como o <xref:System.Data.DataTable.PrimaryKey%2A> para um <xref:System.Data.DataTable>, a tabela define automaticamente a <xref:System.Data.DataColumn.AllowDBNull%2A> propriedade da coluna como **false** e a <xref:System.Data.DataColumn.Unique%2A> Propriedade como **true**. Para chaves primárias de várias colunas, somente a propriedade **AllowDBNull** é definida automaticamente como **false**.  
  
 A propriedade **PrimaryKey** de um <xref:System.Data.DataTable> recebe como seu valor uma matriz de um ou mais objetos **DataColumn** , conforme mostrado nos exemplos a seguir. O primeiro exemplo define uma única coluna como a chave primária.  
  
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
  
 O exemplo a seguir define duas colunas como uma chave primária.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataTable>
- [Definição de esquema de DataTable](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
