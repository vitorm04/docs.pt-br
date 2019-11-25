---
title: 'Como: Transformando a forma de uma árvore XML'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 67ffd5f50572c0deba75c664ffd0e12ecfabf730
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332413"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="16c4c-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16c4c-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="16c4c-103">A *forma* de um documento XML refere-se aos seus nomes de elemento, nomes de atributo e às características de sua hierarquia.</span><span class="sxs-lookup"><span data-stu-id="16c4c-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="16c4c-104">Às vezes você precisará alterar a forma de um documento XML.</span><span class="sxs-lookup"><span data-stu-id="16c4c-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="16c4c-105">Por exemplo, você pode ter que enviar um documento XML existente para outro sistema que requer nomes diferentes de elementos e atributos.</span><span class="sxs-lookup"><span data-stu-id="16c4c-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="16c4c-106">Você pode examinar o documento, excluir e renomeando elementos conforme necessário, mas usando funcionais resultados de compilação em um código mais legível e mais sustentável.</span><span class="sxs-lookup"><span data-stu-id="16c4c-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="16c4c-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="16c4c-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="16c4c-108">O primeiro exemplo altera a organização de documento XML.</span><span class="sxs-lookup"><span data-stu-id="16c4c-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="16c4c-109">Mover elementos complexos de um local na árvore para outro.</span><span class="sxs-lookup"><span data-stu-id="16c4c-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="16c4c-110">O segundo exemplo neste tópico cria um documento XML com uma forma diferente do documento de origem.</span><span class="sxs-lookup"><span data-stu-id="16c4c-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="16c4c-111">Altera a caixa de nomes de elemento, renomear alguns elementos, e permitir que alguns elementos da árvore de origem fora da árvore transformada.</span><span class="sxs-lookup"><span data-stu-id="16c4c-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16c4c-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16c4c-112">Example</span></span>  
 <span data-ttu-id="16c4c-113">As seguintes alterações de código a forma de um arquivo XML usando expressões inseridas de consulta.</span><span class="sxs-lookup"><span data-stu-id="16c4c-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="16c4c-114">O documento XML de origem neste exemplo contém um elemento de `Customers` no elemento de `Root` que contém todos os clientes.</span><span class="sxs-lookup"><span data-stu-id="16c4c-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="16c4c-115">Também contém um elemento de `Orders` no elemento de `Root` que contém todos os pedidos.</span><span class="sxs-lookup"><span data-stu-id="16c4c-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="16c4c-116">Este exemplo cria uma nova árvore XML em que os pedidos para cada cliente estão contidos em um elemento de `Orders` dentro do elemento de `Customer` .</span><span class="sxs-lookup"><span data-stu-id="16c4c-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="16c4c-117">O documento original também contém um elemento de `CustomerID` no elemento de `Order` ; este elemento será removido do documento reformulado.</span><span class="sxs-lookup"><span data-stu-id="16c4c-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="16c4c-118">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="16c4c-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim newCustOrd = _  
    <Root>  
        <%= From cust In co.<Customers>.<Customer> _  
            Select _  
            <Customer>  
                <%= cust.Attributes() %>  
                <%= cust.Elements() %>  
                <Orders>  
                    <%= From ord In co.<Orders>.<Order> _  
                        Where ord.<CustomerID>.Value = cust.@CustomerID _  
                        Select _  
                        <Order>  
                            <%= ord.Attributes() %>  
                            <%= ord.<EmployeeID> %>  
                            <%= ord.<OrderDate> %>  
                            <%= ord.<RequiredDate> %>  
                            <%= ord.<ShipInfo> %>  
                        </Order> _  
                    %>  
                </Orders>  
            </Customer> _  
        %>  
    </Root>  
Console.WriteLine(newCustOrd)  
```  
  
 <span data-ttu-id="16c4c-119">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="16c4c-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="16c4c-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16c4c-120">Example</span></span>  
 <span data-ttu-id="16c4c-121">Este exemplo renomeia alguns elementos e converte alguns atributos para elementos.</span><span class="sxs-lookup"><span data-stu-id="16c4c-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="16c4c-122">O código chama `ConvertAddress`, que retorna uma lista de objetos <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="16c4c-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="16c4c-123">O argumento para o método é uma consulta que determina o elemento complexo de `Address` onde o atributo de `Type` tem um valor de `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="16c4c-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="16c4c-124">Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="16c4c-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)  
    Dim fragment = New List(Of XElement)  
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)  
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)  
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)  
    fragment.Add(<ST><%= add.<State>.Value %></ST>)  
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)  
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)  
    Return fragment  
End Function  
  
Sub Main()  
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
    Dim newPo As XElement = _  
        <PO>  
            <ID><%= po.@PurchaseOrderNumber %></ID>  
            <DATE><%= CDate(po.@OrderDate) %></DATE>  
            <%= _  
                ConvertAddress( _  
                (From el In po.<Address> _  
                Where el.@Type = "Shipping" _  
                Select el) _  
                .First() _  
                ) _  
            %>  
        </PO>  
    Console.WriteLine(newPo)  
End Sub  
```  
  
 <span data-ttu-id="16c4c-125">Esse código gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="16c4c-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16c4c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16c4c-126">See also</span></span>

- [<span data-ttu-id="16c4c-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16c4c-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
