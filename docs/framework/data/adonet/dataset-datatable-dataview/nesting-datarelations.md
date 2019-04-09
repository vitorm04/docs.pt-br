---
title: Aninhamento de DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 7975e17bd957a822bf3d60d487eb928cee84bd28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117203"
---
# <a name="nesting-datarelations"></a>Aninhamento de DataRelations
Em uma representação de dados relacional, as tabelas individuais contêm linhas que estão relacionadas entre si usando uma coluna ou conjunto de colunas. No ADO.NET <xref:System.Data.DataSet>, a relação entre tabelas é implementada usando um <xref:System.Data.DataRelation>. Quando você cria um **DataRelation**, as relações pai-filho das colunas são gerenciadas por meio de relação. As tabelas e colunas são entidades separadas. Na representação hierárquica dos dados XML fornece, as relações pai-filho são representadas por elementos pai que contêm elementos filho aninhados.  
  
 Para facilitar o aninhamento de objetos filho quando uma **DataSet** está sincronizado com um <xref:System.Xml.XmlDataDocument> ou gravadas como dados XML usando **WriteXml**, o **DataRelation** expõe um **Nested** propriedade. Definindo o **Nested** propriedade de uma **DataRelation** para **verdadeiro** faz com que o filho linhas de relação ser aninhadas dentro da coluna pai quando gravadas como dados XML ou sincronizado com um **XmlDataDocument**. O **Nested** propriedade da **DataRelation** está **false**, por padrão.  
  
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
  
 Porque o **Nested** propriedade da **DataRelation** objeto não está definido como **true** para este **DataSet**, os objetos filho não estão aninhados dentro dos elementos pai quando isso **conjunto de dados** é representado como dados XML. Transformando a representação XML de um **DataSet** que contém relacionados **conjunto de dados**s com relações de dados não aninhadas podem causar lentidão no desempenho. É recomendável que você aninhar as relações de dados. Para fazer isso, defina a **Nested** propriedade **verdadeiro**. Em seguida, escreva o código na folha de estilos XSLT que usa expressões de consulta XPath hierárquicas de cima para baixo para localizar e transformar os dados.  
  
 O exemplo de código a seguir mostra o resultado de chamar **WriteXml** sobre o **conjunto de dados**.  
  
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
  
 Observe que o **clientes** elemento e o **pedidos** elementos são mostrados como elementos irmãos. Se você quisesse a **pedidos** elementos a serem exibidos como filhos de seus elementos do respectivo pai, o **Nested** propriedade do **DataRelation** precisa ser definido como **verdadeira** e adicione o seguinte:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 O código a seguir mostra a saída resultante seria semelhante, com o **pedidos** elementos aninhados dentro de seus elementos do respectivo pai.  
  
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

- [Usando XML em um DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Adicionando DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)
- [DataSets, DataTables e DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
