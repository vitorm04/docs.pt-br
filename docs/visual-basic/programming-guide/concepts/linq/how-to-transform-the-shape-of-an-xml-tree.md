---
title: "Como: transformar a forma de uma árvore XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9c71f4af829a395204bc17161547aa5fdd06cbb1
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a>Como: transformar a forma de uma árvore XML (Visual Basic)
O *forma* de XML documento se refere a seus nomes de elemento, nomes de atributo e as características de sua hierarquia.  
  
 Às vezes você precisará alterar a forma de um documento XML. Por exemplo, você pode ter que enviar um documento XML existente para outro sistema que requer nomes diferentes de elementos e atributos. Você pode examinar o documento, excluir e renomeando elementos conforme necessário, mas usando funcionais resultados de compilação em um código mais legível e mais sustentável. Para obter mais informações sobre a construção funcional, consulte [construção funcional (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 O primeiro exemplo altera a organização de documento XML. Mover elementos complexos de um local na árvore para outro.  
  
 O segundo exemplo neste tópico cria um documento XML com uma forma diferente do documento de origem. Altera a caixa de nomes de elemento, renomear alguns elementos, e permitir que alguns elementos da árvore de origem fora da árvore transformada.  
  
## <a name="example"></a>Exemplo  
 As seguintes alterações de código a forma de um arquivo XML usando expressões inseridas de consulta.  
  
 O documento XML de origem neste exemplo contém um elemento de `Customers` no elemento de `Root` que contém todos os clientes. Também contém um elemento de `Orders` no elemento de `Root` que contém todos os pedidos. Este exemplo cria uma nova árvore XML em que os pedidos para cada cliente estão contidos em um elemento de `Orders` dentro do elemento de `Customer` . O documento original também contém um elemento de `CustomerID` no elemento de `Order` ; este elemento será removido do documento reformulado.  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: clientes e pedidos (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
 Esse código gera a seguinte saída:  
  
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
  
## <a name="example"></a>Exemplo  
 Este exemplo renomeia alguns elementos e converte alguns atributos para elementos.  
  
 O código chama `ConvertAddress`, que retorna uma lista de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> O argumento para o método é uma consulta que determina o elemento complexo de `Address` onde o atributo de `Type` tem um valor de `"Shipping"`.  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 Esse código gera a seguinte saída:  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Projeções e transformações (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
