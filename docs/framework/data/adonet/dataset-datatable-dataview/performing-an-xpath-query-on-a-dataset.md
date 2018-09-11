---
title: Executar uma consulta XPath em um conjunto de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: a1718429360d79c4628e9948eb1b052c3ac01964
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270373"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Executar uma consulta XPath em um conjunto de dados
A relação entre um sincronizada <xref:System.Data.DataSet> e <xref:System.Xml.XmlDataDocument> lhe permite fazer uso do XML serviços, como a consulta XML Path Language (XPath), que acessam o **XmlDataDocument** e podem executar determinada funcionalidade modo mais conveniente do que o acesso a **conjunto de dados** diretamente. Por exemplo, em vez de usar o **selecionar** método de um <xref:System.Data.DataTable> navegar em relações com outras tabelas em um **conjunto de dados**, você pode executar uma consulta XPath em um **XmlDataDocument**  que é sincronizado com o **DataSet**, para obter uma lista de elementos XML na forma de um <xref:System.Xml.XmlNodeList>. Os nós na **XmlNodeList**, convertido como <xref:System.Xml.XmlElement> nós, em seguida, pode ser passado para o **GetRowFromElement** método da **XmlDataDocument**, para retornar a correspondência <xref:System.Data.DataRow> referências às linhas da tabela no sincronizado **conjunto de dados**.  
  
 Por exemplo, o exemplo de código a seguir executa uma consulta de XPath "neto". O **DataSet** é preenchida com três tabelas: **clientes**, **pedidos**, e **OrderDetails**. No exemplo, uma relação pai-filho é criada entre o **clientes** e **pedidos** tabelas e entre o **pedidos** e **OrderDetails** tabelas. Uma consulta XPath é executada, em seguida, para retornar um **XmlNodeList** dos **clientes** nós onde um neto **OrderDetails** nó tem um **ProductID**nó com o valor de 43. Em essência, o exemplo está usando a consulta XPath para determinar quais clientes têm solicitou o produto que tem o **ProductID** de 43.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Sincronização de DataSet e XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
