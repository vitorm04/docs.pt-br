---
title: Sincronizando um conjunto de dados com um XmlDataDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fbc96fa9-b5d1-4f97-b099-c89b0e14ce2c
ms.openlocfilehash: 5aeb5fc3ad1008871b6c54d6c096cb3a76c3416e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514566"
---
# <a name="synchronizing-a-dataset-with-an-xmldatadocument"></a><span data-ttu-id="d4e64-102">Sincronizando um conjunto de dados com um XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="d4e64-102">Synchronizing a DataSet with an XmlDataDocument</span></span>
<span data-ttu-id="d4e64-103">Esta seção demonstra uma etapa no processamento de uma ordem de compra, usando um fortemente tipados <xref:System.Data.DataSet> sincronizado com um <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="d4e64-103">This section demonstrates one step in the processing of a purchase order, using a strongly typed <xref:System.Data.DataSet> synchronized with an <xref:System.Xml.XmlDataDocument>.</span></span> <span data-ttu-id="d4e64-104">Os exemplos a seguir criam uma **conjunto de dados** com um esquema minimizado que corresponde a apenas uma parte do documento XML de origem.</span><span class="sxs-lookup"><span data-stu-id="d4e64-104">The examples that follow create a **DataSet** with a minimized schema that matches only a portion of the source XML document.</span></span> <span data-ttu-id="d4e64-105">Os exemplos usam um **XmlDataDocument** para preservar a fidelidade do documento XML de origem, permitindo que o **conjunto de dados** a ser usado para expor um subconjunto do documento XML.</span><span class="sxs-lookup"><span data-stu-id="d4e64-105">The examples use an **XmlDataDocument** to preserve the fidelity of the source XML document, enabling the **DataSet** to be used to expose a subset of the XML document.</span></span>  
  
 <span data-ttu-id="d4e64-106">O seguinte documento XML contém todas as informações que pertencem a uma ordem de compra: informações do cliente, itens ordenados, informações de remessa e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="d4e64-106">The following XML document contains all the information pertaining to a purchase order: customer information, items ordered, shipping information, and so on.</span></span>  
  
```xml  
<?xml version="1.0" standalone="yes"?>  
<PurchaseOrder>  
  <Customers>  
    <CustomerID>CHOPS</CustomerID>  
    <Orders>  
      <OrderID>10966</OrderID>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>37</ProductID>  
        <UnitPrice>26</UnitPrice>  
        <Quantity>8</Quantity>  
        <Discount>0</Discount>  
      </OrderDetails>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>56</ProductID>  
        <UnitPrice>38</UnitPrice>  
        <Quantity>12</Quantity>  
        <Discount>0.15</Discount>  
      </OrderDetails>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>62</ProductID>  
        <UnitPrice>49.3</UnitPrice>  
        <Quantity>12</Quantity>  
        <Discount>0.15</Discount>  
      </OrderDetails>  
      <CustomerID>CHOPS</CustomerID>  
      <EmployeeID>4</EmployeeID>  
      <OrderDate>1998-03-20T00:00:00.0000000</OrderDate>  
      <RequiredDate>1998-04-17T00:00:00.0000000</RequiredDate>  
      <ShippedDate>1998-04-08T00:00:00.0000000</ShippedDate>  
      <ShipVia>1</ShipVia>  
      <Freight>27.19</Freight>  
      <ShipName>Chop-suey Chinese</ShipName>  
      <ShipAddress>Hauptstr. 31</ShipAddress>  
      <ShipCity>Bern</ShipCity>  
      <ShipPostalCode>3012</ShipPostalCode>  
      <ShipCountry>Switzerland</ShipCountry>  
    </Orders>  
    <CompanyName>Chop-suey Chinese</CompanyName>  
    <ContactName>Yang Wang</ContactName>  
    <ContactTitle>Owner</ContactTitle>  
    <Address>Hauptstr. 29</Address>  
    <City>Bern</City>  
    <PostalCode>3012</PostalCode>  
    <Country>Switzerland</Country>  
    <Phone>0452-076545</Phone>  
  </Customers>  
  <Shippers>  
    <ShipperID>1</ShipperID>  
    <CompanyName>Speedy Express</CompanyName>  
    <Phone>(503) 555-0100</Phone>  
  </Shippers>  
  <Shippers>  
    <ShipperID>2</ShipperID>  
    <CompanyName>United Package</CompanyName>  
    <Phone>(503) 555-0101</Phone>  
  </Shippers>  
  <Shippers>  
    <ShipperID>3</ShipperID>  
    <CompanyName>Federal Shipping</CompanyName>  
    <Phone>(503) 555-0102</Phone>  
  </Shippers>  
  <Products>  
    <ProductID>37</ProductID>  
    <ProductName>Gravad lax</ProductName>  
    <QuantityPerUnit>12 - 500 g pkgs.</QuantityPerUnit>  
    <UnitsInStock>11</UnitsInStock>  
    <UnitsOnOrder>50</UnitsOnOrder>  
    <ReorderLevel>25</ReorderLevel>  
  </Products>  
  <Products>  
    <ProductID>56</ProductID>  
    <ProductName>Gnocchi di nonna Alice</ProductName>  
    <QuantityPerUnit>24 - 250 g pkgs.</QuantityPerUnit>  
    <UnitsInStock>21</UnitsInStock>  
    <UnitsOnOrder>10</UnitsOnOrder>  
    <ReorderLevel>30</ReorderLevel>  
  </Products>  
  <Products>  
    <ProductID>62</ProductID>  
    <ProductName>Tarte au sucre</ProductName>  
    <QuantityPerUnit>48 pies</QuantityPerUnit>  
    <UnitsInStock>17</UnitsInStock>  
    <UnitsOnOrder>0</UnitsOnOrder>  
    <ReorderLevel>0</ReorderLevel>  
  </Products>  
</PurchaseOrder>  
```  
  
 <span data-ttu-id="d4e64-107">É uma etapa para processar as informações de ordem de compra contidas no documento XML anterior para a ordem a ser preenchido do estoque de atual da empresa.</span><span class="sxs-lookup"><span data-stu-id="d4e64-107">One step in processing the purchase order information contained in the preceding XML document is for the order to be filled from the company's current inventory.</span></span> <span data-ttu-id="d4e64-108">O funcionário responsável para preencher a ordem do warehouse da empresa não precisa ver o conteúdo inteiro da ordem de compra; eles só precisarão ver as informações de produto para o pedido.</span><span class="sxs-lookup"><span data-stu-id="d4e64-108">The employee responsible for filling the order from the company's warehouse does not need to see the entire contents of the purchase order; they only need to see the product information for the order.</span></span> <span data-ttu-id="d4e64-109">Para expor somente as informações de produto do documento XML, criar fortemente tipado **conjunto de dados** com um esquema, escrito como o esquema XSD (linguagem) definição de esquema XML, que é mapeado para os produtos e quantidades ordenados.</span><span class="sxs-lookup"><span data-stu-id="d4e64-109">To expose only the product information from the XML document, create a strongly typed **DataSet** with a schema, written as XML Schema definition language (XSD) schema, that maps to the products and quantities ordered.</span></span> <span data-ttu-id="d4e64-110">Para obter mais informações sobre fortemente tipadas **DataSet** objetos, consulte [DataSets tipados](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="d4e64-110">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="d4e64-111">O código a seguir mostra o esquema do qual fortemente tipados **conjunto de dados** é gerado para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="d4e64-111">The following code shows the schema from which the strongly typed **DataSet** is generated for this sample.</span></span>  
  
```xml  
<?xml version="1.0" standalone="yes"?>  
<xs:schema id="OrderDetail" xmlns=""   
                            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
                            xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"   
                            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="OrderDetail" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetails" codegen:typedName="LineItem" codegen:typedPlural="LineItems">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" type="xs:int" minOccurs="0" codegen:typedName="OrderID"/>  
              <xs:element name="Quantity" type="xs:short" minOccurs="0" codegen:typedName="Quantity"/>  
              <xs:element name="ProductID" type="xs:int" minOccurs="0" codegen:typedName="ProductID"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Products" codegen:typedName="Product" codegen:typedPlural="Products">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="ProductID" type="xs:int" minOccurs="0" codegen:typedName="ProductID"/>  
              <xs:element name="ProductName" type="xs:string" minOccurs="0" codegen:typedName="ProductName"/>  
              <xs:element name="QuantityPerUnit" type="xs:string" minOccurs="0" codegen:typedName="QuantityPerUnit"/>  
              <xs:element name="UnitsInStock" type="xs:short" minOccurs="0" codegen:typedName="UnitsInStock"/>  
              <xs:element name="UnitsOnOrder" type="xs:short" minOccurs="0" codegen:typedName="UnitsOnOrder"/>  
              <xs:element name="ReorderLevel" type="xs:short" minOccurs="0" codegen:typedName="ReorderLevel"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Products" />  
      <xs:field xpath="ProductID" />  
    </xs:unique>  
    <xs:keyref name="Relation1" refer="Constraint1" codegen:typedChildren="GetLineItems" codegen:typedParent="Product">  
      <xs:selector xpath=".//OrderDetails" />  
      <xs:field xpath="ProductID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="d4e64-112">Observe que somente informações do **OrderDetails** e **produtos** elementos do documento XML original são incluídos no esquema para o **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="d4e64-112">Notice that only information from the **OrderDetails** and **Products** elements of the original XML document are included in the schema for the **DataSet**.</span></span> <span data-ttu-id="d4e64-113">Sincronizando a **DataSet** com um **XmlDataDocument** garante que os elementos não incluídos no **conjunto de dados** serão mantidos com o documento XML.</span><span class="sxs-lookup"><span data-stu-id="d4e64-113">Synchronizing the **DataSet** with an **XmlDataDocument** ensures that the elements not included in the **DataSet** will persist with the XML document.</span></span>  
  
 <span data-ttu-id="d4e64-114">Com rigidez de tipos **DataSet** gerado do esquema XML (com um namespace de **Northwind.FillOrder**), uma parte do documento XML original pode ser exposta sincronizando o  **Conjunto de dados** com o **XmlDataDocument** carregados do documento XML de origem.</span><span class="sxs-lookup"><span data-stu-id="d4e64-114">With the strongly typed **DataSet** generated from the XML Schema (with a namespace of **Northwind.FillOrder**), a portion of the original XML document can be exposed by synchronizing the **DataSet** with the **XmlDataDocument** loaded from the source XML document.</span></span> <span data-ttu-id="d4e64-115">Observe que o **conjunto de dados** gerado a partir o esquema contém a estrutura, mas nenhum dado.</span><span class="sxs-lookup"><span data-stu-id="d4e64-115">Notice that the **DataSet** generated from the schema contains structure but no data.</span></span> <span data-ttu-id="d4e64-116">Os dados são preenchidos quando você carrega o XML para o **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="d4e64-116">The data is filled in when you load the XML into the **XmlDataDocument**.</span></span> <span data-ttu-id="d4e64-117">Se você tentar carregar um **XmlDataDocument** que foi sincronizado com um **conjunto de dados** que já contém dados, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="d4e64-117">If you attempt to load an **XmlDataDocument** that has been synchronized with a **DataSet** that already contains data, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="d4e64-118">Após o **DataSet** (e o **XmlDataDocument**) tiver sido atualizado, o **XmlDataDocument** pode, em seguida, gravar o documento XML modificado com os elementos ignorados pelo **Conjunto de dados** permanecem intactos, conforme mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="d4e64-118">After the **DataSet** (and the **XmlDataDocument**) has been updated, the **XmlDataDocument** can then write out the modified XML document with the elements ignored by the **DataSet** still intact, as shown below.</span></span> <span data-ttu-id="d4e64-119">No cenário de ordem de compra, depois que os itens da ordem foram preenchidos, o documento XML modificado pode, em seguida, passado para a próxima etapa no processo de pedido, talvez para o departamento de envio da empresa.</span><span class="sxs-lookup"><span data-stu-id="d4e64-119">In the purchase order scenario, after the order items have been filled, the modified XML document can then be passed on to the next step in the order process, perhaps to the company's shipping department.</span></span>  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Xml  
Imports Northwind.FillOrder  
  
Public class Sample  
  Public Shared Sub Main()  
  
    Dim orderDS As OrderDetail = New OrderDetail  
  
    Dim xmlDocument As XmlDataDocument = New XmlDataDocument(orderDS)   
  
    xmlDocument.Load("Order.xml")  
  
    Dim orderItem As OrderDetail.LineItem  
    Dim product As OrderDetail.Product  
  
    For Each orderItem In orderDS.LineItems  
      product = orderItem.Product  
  
      ' Remove quantity from the current stock.  
      product.UnitsInStock = CType(product.UnitsInStock - orderItem.Quantity, Short)  
  
      ' If the remaining stock is less than the reorder level, order more.  
      If ((product.UnitsInStock + product.UnitsOnOrder) < product.ReorderLevel) Then  
        product.UnitsOnOrder = CType(product.UnitsOnOrder + product.ReorderLevel, Short)  
      End If  
    Next  
  
    xmlDocument.Save("Order_out.xml")  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Xml;  
using Northwind.FillOrder;  
  
public class Sample  
{  
  public static void Main()  
  {  
    OrderDetail orderDS = new OrderDetail();   
  
    XmlDataDocument xmlDocument = new XmlDataDocument(orderDS);   
  
    xmlDocument.Load("Order.xml");  
  
    foreach (OrderDetail.LineItem orderItem in orderDS.LineItems)  
    {  
      OrderDetail.Product product = orderItem.Product;  
  
      // Remove quantity from the current stock.  
      product.UnitsInStock = (short)(product.UnitsInStock - orderItem.Quantity);  
  
      // If the remaining stock is less than the reorder level, order more.  
      if ((product.UnitsInStock + product.UnitsOnOrder) < product.ReorderLevel)  
        product.UnitsOnOrder = (short)(product.UnitsOnOrder + product.ReorderLevel);  
    }  
  
    xmlDocument.Save("Order_out.xml");  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4e64-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4e64-120">See Also</span></span>  
 [<span data-ttu-id="d4e64-121">Sincronização de DataSet e XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="d4e64-121">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="d4e64-122">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d4e64-122">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
