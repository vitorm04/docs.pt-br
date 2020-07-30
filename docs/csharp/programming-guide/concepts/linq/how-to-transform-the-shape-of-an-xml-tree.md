---
title: Como transformar a forma de uma árvore XML (C#)
description: Saiba como transformar a forma de uma árvore XML. A forma de uma árvore XML refere-se a seus nomes de elementos e atributos e suas características de hierarquia.
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 4fa3cc18f235d061ae1778c177c4ac9b626f4b71
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302640"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="c12ff-104">Como transformar a forma de uma árvore XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c12ff-104">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="c12ff-105">A *forma* de um documento XML refere-se aos seus nomes de elemento, nomes de atributo e às características de sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="c12ff-105">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="c12ff-106">Às vezes você precisará alterar a forma de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="c12ff-106">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="c12ff-107">Por exemplo, você pode ter que enviar um documento XML existente para outro sistema que requer nomes diferentes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="c12ff-107">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="c12ff-108">Você pode examinar o documento, excluir e renomeando elementos conforme necessário, mas usando funcionais resultados de compilação em um código mais legível e mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="c12ff-108">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="c12ff-109">Para obter mais informações sobre a construção funcional, consulte [Construção funcional (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c12ff-109">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c12ff-110">O primeiro exemplo altera a organização de documento XML.</span><span class="sxs-lookup"><span data-stu-id="c12ff-110">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="c12ff-111">Mover elementos complexos de um local na árvore para outro.</span><span class="sxs-lookup"><span data-stu-id="c12ff-111">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="c12ff-112">O segundo exemplo neste tópico cria um documento XML com uma forma diferente do documento de origem.</span><span class="sxs-lookup"><span data-stu-id="c12ff-112">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="c12ff-113">Altera a caixa de nomes de elemento, renomear alguns elementos, e permitir que alguns elementos da árvore de origem fora da árvore transformada.</span><span class="sxs-lookup"><span data-stu-id="c12ff-113">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c12ff-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c12ff-114">Example</span></span>  
 <span data-ttu-id="c12ff-115">As seguintes alterações de código a forma de um arquivo XML usando expressões inseridas de consulta.</span><span class="sxs-lookup"><span data-stu-id="c12ff-115">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="c12ff-116">O documento XML de origem neste exemplo contém um elemento de `Customers` no elemento de `Root` que contém todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="c12ff-116">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="c12ff-117">Também contém um elemento de `Orders` no elemento de `Root` que contém todos os pedidos.</span><span class="sxs-lookup"><span data-stu-id="c12ff-117">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="c12ff-118">Este exemplo cria uma nova árvore XML em que os pedidos para cada cliente estão contidos em um elemento de `Orders` dentro do elemento de `Customer` .</span><span class="sxs-lookup"><span data-stu-id="c12ff-118">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="c12ff-119">O documento original também contém um elemento de `CustomerID` no elemento de `Order` ; este elemento será removido do documento reformulado.</span><span class="sxs-lookup"><span data-stu-id="c12ff-119">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="c12ff-120">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="c12ff-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 <span data-ttu-id="c12ff-121">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c12ff-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <Fax>(503) 555-2376</Fax>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a><span data-ttu-id="c12ff-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c12ff-122">Example</span></span>  
 <span data-ttu-id="c12ff-123">Este exemplo renomeia alguns elementos e converte alguns atributos para elementos.</span><span class="sxs-lookup"><span data-stu-id="c12ff-123">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="c12ff-124">O código chama `ConvertAddress`, que retorna uma lista de objetos <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="c12ff-124">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="c12ff-125">O argumento para o método é uma consulta que determina o elemento complexo de `Address` onde o atributo de `Type` tem um valor de `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="c12ff-125">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="c12ff-126">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="c12ff-126">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 <span data-ttu-id="c12ff-127">Este código produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="c12ff-127">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
