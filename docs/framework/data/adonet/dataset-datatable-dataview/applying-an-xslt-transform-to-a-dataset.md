---
title: Aplicar uma transformação XSLT a um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: d9767844400d67e81c7065148b22c62352af0428
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784793"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="ce48d-102">Aplicar uma transformação XSLT a um DataSet</span><span class="sxs-lookup"><span data-stu-id="ce48d-102">Applying an XSLT Transform to a DataSet</span></span>
<span data-ttu-id="ce48d-103">O método **WriteXml** do <xref:System.Data.DataSet> permite que você grave o conteúdo de um **DataSet** como dados XML.</span><span class="sxs-lookup"><span data-stu-id="ce48d-103">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="ce48d-104">Uma tarefa comum é transformar esse XML em outro formato usando transformações XSL (XSLT).</span><span class="sxs-lookup"><span data-stu-id="ce48d-104">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="ce48d-105">No entanto, a sincronização de um <xref:System.Xml.XmlDataDocument> conjunto de dados com um permite que você aplique uma folha de estilos XSLT ao conteúdo de um **conjunto** de dados sem precisar primeiro gravar o conteúdo do **DataSet** como dado XML usando **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="ce48d-105">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="ce48d-106">O exemplo a seguir popula um **conjunto** de um DataSet com tabelas e relações, sincroniza o **conjunto** de os com um **XmlDataDocument**e grava uma parte do **conjunto** de um arquivo HTML usando uma folha de estilos XSLT.</span><span class="sxs-lookup"><span data-stu-id="ce48d-106">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="ce48d-107">A seguir estão os conteúdos da folha de estilos XSLT.</span><span class="sxs-lookup"><span data-stu-id="ce48d-107">Following are the contents of the XSLT stylesheet.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="ce48d-108">O código a seguir preenche o **DataSet** e aplica a folha de estilos XSLT.</span><span class="sxs-lookup"><span data-stu-id="ce48d-108">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce48d-109">Se você estiver aplicando uma folha de estilos XSLT a um **conjunto** de um que contém relações, você obterá o melhor desempenho se definir <xref:System.Data.DataRelation> a propriedade **aninhada** de como **true** para cada relação aninhada.</span><span class="sxs-lookup"><span data-stu-id="ce48d-109">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="ce48d-110">Isso permite que você use as folhas de estilo XSLT que implementam o processamento de cima para baixo natural para navegar na hierarquia e transformar os dados, em oposição ao uso de eixos de local XPath com uso intensivo de desempenho (por exemplo, irmão precedente e o irmão seguinte no estilo expressões de teste de nó de planilha) para navegar.</span><span class="sxs-lookup"><span data-stu-id="ce48d-110">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="ce48d-111">Para obter mais informações sobre relações aninhadas, consulte [aninhando DataRelations](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="ce48d-111">For more information on nested relations, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);   
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",   
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce48d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce48d-112">See also</span></span>

- [<span data-ttu-id="ce48d-113">Sincronização de DataSet e XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="ce48d-113">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- <span data-ttu-id="ce48d-114">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ce48d-114">[ADO.NET Overview](../ado-net-overview.md)</span></span>
