---
title: "Definindo chaves primárias"
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
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a2ba353353b52e5a866887e7f0dc4b743e336bd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="defining-primary-keys"></a>Definindo chaves primárias
Uma tabela de banco de dados geralmente tem uma coluna ou o grupo de colunas que identifica exclusivamente cada linha na tabela. Este grupo de colunas ou coluna de identificação é chamado de chave primária.  
  
 Quando você identificar um único <xref:System.Data.DataColumn> como o <xref:System.Data.DataTable.PrimaryKey%2A> para um <xref:System.Data.DataTable>, a tabela define automaticamente o <xref:System.Data.DataColumn.AllowDBNull%2A> propriedade da coluna a ser **false** e o <xref:System.Data.DataColumn.Unique%2A> propriedade para  **True**. Para chaves primárias de várias colunas, somente o **AllowDBNull** propriedade é definida automaticamente como **false**.  
  
 O **PrimaryKey** propriedade de um <xref:System.Data.DataTable> recebe como seu valor de uma matriz de uma ou mais **DataColumn** objetos, conforme mostrado nos exemplos a seguir. O primeiro exemplo define uma única coluna de chave primária.  
  
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
 <xref:System.Data.DataTable>  
 [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
