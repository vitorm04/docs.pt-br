---
title: Aninhamento de DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 08149de9222c34928078c0ca9d88096f7a4a88d1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203261"
---
# <a name="nesting-datarelations"></a>Aninhamento de DataRelations
Em uma representação de dados relacional, as tabelas individuais contêm linhas relacionadas umas às outras usando uma coluna ou conjunto de colunas. No ADO.NET <xref:System.Data.DataSet>, a relação entre as tabelas é implementada usando <xref:System.Data.DataRelation>um. Quando você cria uma **DataRelation**, as relações pai-filho das colunas são gerenciadas somente por meio da relação. As tabelas e colunas são entidades separadas. Na representação hierárquica dos dados que o XML fornece, as relações pai-filho são representadas por elementos pai que contêm elementos filho aninhados.  
  
 Para facilitar o aninhamento de objetos filho quando um **conjunto** de dados é <xref:System.Xml.XmlDataDocument> sincronizado com um ou gravado como dado XML usando **WriteXml**, a DataRelation expõe uma propriedade **aninhada** . Definir a Propriedade aninhada de uma DataRelation como **true** faz com que as linhas filhas da relação sejam aninhadas dentro da coluna pai quando gravadas como dados XML ou sincronizadas com um **XmlDataDocument**. A Propriedade aninhada de **DataRelation** é **false**, por padrão.  
  
 Por exemplo, considere o **conjunto de DataSet**a seguir.  
  
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
  
 Como a Propriedade aninhada do objeto DataRelation não está definida como **true** para esse **conjunto**de dados, os objetos filho não são aninhados dentro dos elementos pai quando esse **DataSet** é representado como um dado XML. A transformação da representação XML de um **conjunto** de dados que contém **DataSets**relacionados com relação a relações não aninhadas pode causar um desempenho lento. É recomendável aninhar as relações de dados. Para fazer isso, defina a Propriedade Nested como **true**. Em seguida, escreva o código na folha de estilos XSLT que usa expressões de consulta XPath hierárquicas de cima para baixo para localizar e transformar os dados.  
  
 O exemplo de código a seguir mostra o resultado da chamada de **WriteXml** no **conjunto**de resultados.  
  
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
  
 Observe que o elemento Customers e os elementos **Orders** são mostrados como elementos irmãos. Se você quisesse que os elementos Orders fossem exibidos como filhos de seus respectivos elementos pai, a propriedade aninhada da DataRelation precisaria ser definida como **true** e você adicionaria o seguinte:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 O código a seguir mostra a aparência da saída resultante, com os elementos **Orders** aninhados em seus respectivos elementos pai.  
  
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

- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [Adding DataRelations](adding-datarelations.md) (Adicionando DataRelations)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
