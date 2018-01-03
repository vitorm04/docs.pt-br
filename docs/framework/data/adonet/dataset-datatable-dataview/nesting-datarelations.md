---
title: Aninhamento DataRelations
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
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 264ce39902a23f0f7136a2fa1b49d83d0ce2736b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="nesting-datarelations"></a>Aninhamento DataRelations
Em uma representação relacional de dados, tabelas individuais contêm linhas que estão relacionadas uns aos outros usando uma coluna ou conjunto de colunas. No ADO.NET <xref:System.Data.DataSet>, a relação entre tabelas é implementada usando um <xref:System.Data.DataRelation>. Quando você cria um **DataRelation**, as relações pai-filho das colunas são gerenciadas por meio de relação. As tabelas e colunas são entidades separadas. Na representação hierárquica de dados que o XML fornece, as relações pai-filho são representadas pelos elementos pai que contêm elementos filho aninhada.  
  
 Para facilitar o aninhamento de objetos filho quando um **DataSet** está sincronizado com um <xref:System.Xml.XmlDataDocument> ou gravadas como dados XML usando **WriteXml**, o **DataRelation** expõe um **aninhadas** propriedade. Definindo o **aninhadas** propriedade de um **DataRelation** para **true** faz com que o filho linhas de relação ser aninhadas dentro da coluna pai quando gravadas como dados XML ou sincronizado com um **XmlDataDocument**. O **aninhadas** propriedade o **DataRelation** é **false**, por padrão.  
  
 Por exemplo, considere o seguinte **conjunto de dados**.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 Porque o **aninhadas** propriedade do **DataRelation** objeto não está definido como **true** para este **conjunto de dados**, os objetos filho não estão aninhados dentro de elementos pai quando isso **DataSet** é representado como dados XML. Transformando a representação XML de um **DataSet** que contém relacionados **DataSet**s com relações de dados aninhadas não podem causar lentidão no desempenho. É recomendável que você aninhar as relações de dados. Para fazer isso, defina o **aninhadas** propriedade **true**. Em seguida, escreva o código na folha de estilos XSLT que usa expressões de consulta XPath hierárquicas de cima para baixo para localizar e transformar os dados.  
  
 O exemplo de código a seguir mostra o resultado de chamar **WriteXml** no **conjunto de dados**.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 Observe que o **clientes** elemento e o **pedidos** elementos são mostrados como elementos irmãos. Se você quisesse o **pedidos** elementos aparecem como filhos dos elementos de seu respectivo pai, o **aninhadas** propriedade do **DataRelation** precisa ser definido como **true** e adicione o seguinte:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 O código a seguir mostra como a saída resultante seria, com o **pedidos** elementos aninhados dentro de seus elementos pai do respectivos.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 [Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) (Adicionando DataRelations)  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
