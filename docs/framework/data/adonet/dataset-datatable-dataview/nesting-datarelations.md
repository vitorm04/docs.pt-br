---
title: Aninhamento de DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 971a1bddc40521dc7381ecb2e39709c0fed282ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785990"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="30ad9-102">Aninhamento de DataRelations</span><span class="sxs-lookup"><span data-stu-id="30ad9-102">Nesting DataRelations</span></span>
<span data-ttu-id="30ad9-103">Em uma representação de dados relacional, as tabelas individuais contêm linhas relacionadas umas às outras usando uma coluna ou conjunto de colunas.</span><span class="sxs-lookup"><span data-stu-id="30ad9-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="30ad9-104">No ADO.NET <xref:System.Data.DataSet>, a relação entre as tabelas é implementada usando <xref:System.Data.DataRelation>um.</span><span class="sxs-lookup"><span data-stu-id="30ad9-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="30ad9-105">Quando você cria uma **DataRelation**, as relações pai-filho das colunas são gerenciadas somente por meio da relação.</span><span class="sxs-lookup"><span data-stu-id="30ad9-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="30ad9-106">As tabelas e colunas são entidades separadas.</span><span class="sxs-lookup"><span data-stu-id="30ad9-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="30ad9-107">Na representação hierárquica dos dados que o XML fornece, as relações pai-filho são representadas por elementos pai que contêm elementos filho aninhados.</span><span class="sxs-lookup"><span data-stu-id="30ad9-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="30ad9-108">Para facilitar o aninhamento de objetos filho quando um **conjunto** de <xref:System.Xml.XmlDataDocument> dados é sincronizado com um ou gravado como dado XML usando **WriteXml**, a **DataRelation** expõe uma propriedade **aninhada** .</span><span class="sxs-lookup"><span data-stu-id="30ad9-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="30ad9-109">Definir a propriedade **aninhada** de uma **DataRelation** como **true** faz com que as linhas filhas da relação sejam aninhadas dentro da coluna pai quando gravadas como dados XML ou sincronizadas com um **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="30ad9-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="30ad9-110">A propriedade **aninhada** de **DataRelation** é **false**, por padrão.</span><span class="sxs-lookup"><span data-stu-id="30ad9-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="30ad9-111">Por exemplo, considere o **conjunto de DataSet**a seguir.</span><span class="sxs-lookup"><span data-stu-id="30ad9-111">For example, consider the following **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="30ad9-112">Como a **Propriedade aninhada** do **objeto DataRelation** não está definida como **true** para esse **conjunto**de dados, os objetos filho não são aninhados dentro dos elementos pai quando esse **DataSet** é representado como um dado XML.</span><span class="sxs-lookup"><span data-stu-id="30ad9-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="30ad9-113">A transformação da representação XML de um **conjunto** de dados que contém **DataSets**relacionados com relação a relações não aninhadas pode causar um desempenho lento.</span><span class="sxs-lookup"><span data-stu-id="30ad9-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="30ad9-114">É recomendável aninhar as relações de dados.</span><span class="sxs-lookup"><span data-stu-id="30ad9-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="30ad9-115">Para fazer isso, defina a propriedade **Nested** como **true**.</span><span class="sxs-lookup"><span data-stu-id="30ad9-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="30ad9-116">Em seguida, escreva o código na folha de estilos XSLT que usa expressões de consulta XPath hierárquicas de cima para baixo para localizar e transformar os dados.</span><span class="sxs-lookup"><span data-stu-id="30ad9-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="30ad9-117">O exemplo de código a seguir mostra o resultado da chamada de **WriteXml** no **conjunto**de resultados.</span><span class="sxs-lookup"><span data-stu-id="30ad9-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="30ad9-118">Observe que o elemento **Customers** e os elementos **Orders** são mostrados como elementos irmãos.</span><span class="sxs-lookup"><span data-stu-id="30ad9-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="30ad9-119">Se você quisesse que os elementos **Orders** fossem exibidos como filhos de seus respectivos elementos pai, a propriedade **aninhada** da **DataRelation** precisaria ser definida como **true** e você adicionaria o seguinte:</span><span class="sxs-lookup"><span data-stu-id="30ad9-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="30ad9-120">O código a seguir mostra a aparência da saída resultante, com os elementos **Orders** aninhados em seus respectivos elementos pai.</span><span class="sxs-lookup"><span data-stu-id="30ad9-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30ad9-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30ad9-121">See also</span></span>

- <span data-ttu-id="30ad9-122">[Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="30ad9-122">[Using XML in a DataSet](using-xml-in-a-dataset.md)</span></span>
- <span data-ttu-id="30ad9-123">[Adding DataRelations](adding-datarelations.md) (Adicionando DataRelations)</span><span class="sxs-lookup"><span data-stu-id="30ad9-123">[Adding DataRelations](adding-datarelations.md)</span></span>
- <span data-ttu-id="30ad9-124">[DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="30ad9-124">[DataSets, DataTables, and DataViews](index.md)</span></span>
- <span data-ttu-id="30ad9-125">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="30ad9-125">[ADO.NET Overview](../ado-net-overview.md)</span></span>
