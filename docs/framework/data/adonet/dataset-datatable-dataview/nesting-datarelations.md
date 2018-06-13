---
title: Aninhamento DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 3f17d81ac41c90e7f1c48523a4ced91bc788a962
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761890"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="11abd-102">Aninhamento DataRelations</span><span class="sxs-lookup"><span data-stu-id="11abd-102">Nesting DataRelations</span></span>
<span data-ttu-id="11abd-103">Em uma representação relacional de dados, tabelas individuais contêm linhas que estão relacionadas uns aos outros usando uma coluna ou conjunto de colunas.</span><span class="sxs-lookup"><span data-stu-id="11abd-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="11abd-104">No ADO.NET <xref:System.Data.DataSet>, a relação entre tabelas é implementada usando um <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="11abd-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="11abd-105">Quando você cria um **DataRelation**, as relações pai-filho das colunas são gerenciadas por meio de relação.</span><span class="sxs-lookup"><span data-stu-id="11abd-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="11abd-106">As tabelas e colunas são entidades separadas.</span><span class="sxs-lookup"><span data-stu-id="11abd-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="11abd-107">Na representação hierárquica de dados que o XML fornece, as relações pai-filho são representadas pelos elementos pai que contêm elementos filho aninhada.</span><span class="sxs-lookup"><span data-stu-id="11abd-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="11abd-108">Para facilitar o aninhamento de objetos filho quando um **DataSet** está sincronizado com um <xref:System.Xml.XmlDataDocument> ou gravadas como dados XML usando **WriteXml**, o **DataRelation** expõe um **aninhadas** propriedade.</span><span class="sxs-lookup"><span data-stu-id="11abd-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="11abd-109">Definindo o **aninhadas** propriedade de um **DataRelation** para **true** faz com que o filho linhas de relação ser aninhadas dentro da coluna pai quando gravadas como dados XML ou sincronizado com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="11abd-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="11abd-110">O **aninhadas** propriedade o **DataRelation** é **false**, por padrão.</span><span class="sxs-lookup"><span data-stu-id="11abd-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="11abd-111">Por exemplo, considere o seguinte **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="11abd-111">For example, consider the following **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="11abd-112">Porque o **aninhadas** propriedade do **DataRelation** objeto não está definido como **true** para este **conjunto de dados**, os objetos filho não estão aninhados dentro de elementos pai quando isso **DataSet** é representado como dados XML.</span><span class="sxs-lookup"><span data-stu-id="11abd-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="11abd-113">Transformando a representação XML de um **DataSet** que contém relacionados **DataSet**s com relações de dados aninhadas não podem causar lentidão no desempenho.</span><span class="sxs-lookup"><span data-stu-id="11abd-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="11abd-114">É recomendável que você aninhar as relações de dados.</span><span class="sxs-lookup"><span data-stu-id="11abd-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="11abd-115">Para fazer isso, defina o **aninhadas** propriedade **true**.</span><span class="sxs-lookup"><span data-stu-id="11abd-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="11abd-116">Em seguida, escreva o código na folha de estilos XSLT que usa expressões de consulta XPath hierárquicas de cima para baixo para localizar e transformar os dados.</span><span class="sxs-lookup"><span data-stu-id="11abd-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="11abd-117">O exemplo de código a seguir mostra o resultado de chamar **WriteXml** no **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="11abd-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="11abd-118">Observe que o **clientes** elemento e o **pedidos** elementos são mostrados como elementos irmãos.</span><span class="sxs-lookup"><span data-stu-id="11abd-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="11abd-119">Se você quisesse o **pedidos** elementos aparecem como filhos dos elementos de seu respectivo pai, o **aninhadas** propriedade do **DataRelation** precisa ser definido como **true** e adicione o seguinte:</span><span class="sxs-lookup"><span data-stu-id="11abd-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="11abd-120">O código a seguir mostra como a saída resultante seria, com o **pedidos** elementos aninhados dentro de seus elementos pai do respectivos.</span><span class="sxs-lookup"><span data-stu-id="11abd-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11abd-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11abd-121">See Also</span></span>  
 <span data-ttu-id="11abd-122">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="11abd-122">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="11abd-123">[Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) (Adicionando DataRelations)</span><span class="sxs-lookup"><span data-stu-id="11abd-123">[Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)</span></span>  
 <span data-ttu-id="11abd-124">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="11abd-124">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="11abd-125">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="11abd-125">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
