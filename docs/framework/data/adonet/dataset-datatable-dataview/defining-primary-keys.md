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
# <a name="defining-primary-keys"></a>Definir chaves primárias
Uma tabela de banco de dados geralmente tem uma coluna ou grupo de colunas que identifica exclusivamente cada linha na tabela. Esta coluna de identificação ou grupo de colunas é chamada de chave primária.  
  
 Quando você identifica <xref:System.Data.DataColumn> um <xref:System.Data.DataTable.PrimaryKey%2A> único <xref:System.Data.DataTable>como o de <xref:System.Data.DataColumn.AllowDBNull%2A> a , a tabela <xref:System.Data.DataColumn.Unique%2A> define automaticamente a propriedade da coluna como **falsa** e a propriedade como **verdadeira**. Para chaves primárias de várias colunas, apenas a propriedade **AllowDBNull** é definida automaticamente como **falsa**.  
  
 A propriedade **PrimaryKey** de um <xref:System.Data.DataTable> recebe como valor uma matriz de um ou mais objetos **dataColumn,** como mostrado nos exemplos a seguir. O primeiro exemplo define uma única coluna como a chave principal.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataTable>
- [Definição de esquema de DataTable](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
