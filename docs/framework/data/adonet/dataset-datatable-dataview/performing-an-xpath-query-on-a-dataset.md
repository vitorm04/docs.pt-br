---
title: Executar uma consulta XPath em um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 5e9a00ab78a57c3c1686d7c87ed8b45d9b2649af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150825"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Executar uma consulta XPath em um DataSet
A relação entre <xref:System.Data.DataSet> um <xref:System.Xml.XmlDataDocument> sincronizado e permite que você faça uso de serviços XML, como a consulta XML Path Language (XPath), que acessa o **XmlDataDocument** e pode executar certas funcionalidades de forma mais conveniente do que acessar o **DataSet** diretamente. Por exemplo, em **Select** vez de <xref:System.Data.DataTable> usar o método Select de a para navegar relacionamentos com outras tabelas em um Conjunto de **Dados,** você pode executar uma consulta <xref:System.Xml.XmlNodeList>XPath em um **XmlDataDocument** sincronizado com o Conjunto de **Dados,** para obter uma lista de elementos XML na forma de um . Os nós no **XmlNodeList**, <xref:System.Xml.XmlElement> lançados como nós, podem então ser passados para o método **GetRowFromElement** do **XmlDataDocument**, para retornar referências correspondentes <xref:System.Data.DataRow> às linhas da tabela no Conjunto de **Dados**sincronizado .  
  
 Por exemplo, a seguinte amostra de código executa uma consulta XPath "neto". O **DataSet** está preenchido com três **tabelas: Clientes,** **Pedidos**e **Detalhes do Pedido**. Na amostra, uma relação pai-filho é criada pela primeira vez entre as **tabelas Clientes** e **Pedidos** e entre as **tabelas Pedidos** e **Detalhes do Pedido.** Uma consulta XPath é realizada para retornar um **nó XmlNodeList** of **Customers** onde um nó **OrderDetails** neto tem um nó **ProductID** com o valor de 43. Em essência, a amostra está usando a consulta XPath para determinar quais clientes encomendaram o produto que tem o **ProductID** de 43.  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>Confira também

- [Sincronização de DataSet e XmlDataDocument](dataset-and-xmldatadocument-synchronization.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
