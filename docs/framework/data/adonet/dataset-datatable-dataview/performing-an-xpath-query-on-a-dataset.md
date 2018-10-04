---
title: Executar uma consulta XPath em um conjunto de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: a1718429360d79c4628e9948eb1b052c3ac01964
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266124"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="0ed87-102">Executar uma consulta XPath em um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="0ed87-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="0ed87-103">A relação entre um sincronizada <xref:System.Data.DataSet> e <xref:System.Xml.XmlDataDocument> lhe permite fazer uso do XML serviços, como a consulta XML Path Language (XPath), que acessam o **XmlDataDocument** e podem executar determinada funcionalidade modo mais conveniente do que o acesso a **conjunto de dados** diretamente.</span><span class="sxs-lookup"><span data-stu-id="0ed87-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="0ed87-104">Por exemplo, em vez de usar o **selecionar** método de um <xref:System.Data.DataTable> navegar em relações com outras tabelas em um **conjunto de dados**, você pode executar uma consulta XPath em um **XmlDataDocument**  que é sincronizado com o **DataSet**, para obter uma lista de elementos XML na forma de um <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="0ed87-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="0ed87-105">Os nós na **XmlNodeList**, convertido como <xref:System.Xml.XmlElement> nós, em seguida, pode ser passado para o **GetRowFromElement** método da **XmlDataDocument**, para retornar a correspondência <xref:System.Data.DataRow> referências às linhas da tabela no sincronizado **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="0ed87-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="0ed87-106">Por exemplo, o exemplo de código a seguir executa uma consulta de XPath "neto".</span><span class="sxs-lookup"><span data-stu-id="0ed87-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="0ed87-107">O **DataSet** é preenchida com três tabelas: **clientes**, **pedidos**, e **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="0ed87-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="0ed87-108">No exemplo, uma relação pai-filho é criada entre o **clientes** e **pedidos** tabelas e entre o **pedidos** e **OrderDetails** tabelas.</span><span class="sxs-lookup"><span data-stu-id="0ed87-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="0ed87-109">Uma consulta XPath é executada, em seguida, para retornar um **XmlNodeList** dos **clientes** nós onde um neto **OrderDetails** nó tem um **ProductID**nó com o valor de 43.</span><span class="sxs-lookup"><span data-stu-id="0ed87-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="0ed87-110">Em essência, o exemplo está usando a consulta XPath para determinar quais clientes têm solicitou o produto que tem o **ProductID** de 43.</span><span class="sxs-lookup"><span data-stu-id="0ed87-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0ed87-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ed87-111">See Also</span></span>  
 [<span data-ttu-id="0ed87-112">Sincronização de DataSet e XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="0ed87-112">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="0ed87-113">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0ed87-113">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
