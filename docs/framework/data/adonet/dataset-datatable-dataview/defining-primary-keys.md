---
title: Definir chaves primárias
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 84c84cb8fc0ee484b09c69c72571a19c335b58f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230623"
---
# <a name="defining-primary-keys"></a>Definir chaves primárias
Uma tabela de banco de dados geralmente tem uma coluna ou um grupo de colunas que identifica exclusivamente cada linha na tabela. Esta coluna de identificação ou grupo de colunas é chamado de chave primária.  
  
 Quando você identificar um único <xref:System.Data.DataColumn> como o <xref:System.Data.DataTable.PrimaryKey%2A> para um <xref:System.Data.DataTable>, a tabela define automaticamente o <xref:System.Data.DataColumn.AllowDBNull%2A> propriedade da coluna a ser **falso** e o <xref:System.Data.DataColumn.Unique%2A> propriedade para  **True**. Para várias colunas chaves primárias, somente o **AllowDBNull** propriedade é definida automaticamente como **falso**.  
  
 O **PrimaryKey** propriedade de uma <xref:System.Data.DataTable> recebe como seu valor de uma matriz de um ou mais **DataColumn** objetos, conforme mostrado nos exemplos a seguir. O primeiro exemplo define uma única coluna como a chave primária.  
  
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
- [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
