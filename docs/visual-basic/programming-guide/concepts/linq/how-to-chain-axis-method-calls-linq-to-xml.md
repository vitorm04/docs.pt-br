---
title: "Como: encadear chamadas de método do eixo (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c0e9d440ab50b7f275296731e5210578bcedcaa
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a>Como: encadear chamadas de método do eixo (LINQ to XML) (Visual Basic)
Um padrão comum que você usar em seu código é chamar um método do eixo, então chama um dos eixos do método de extensão.  
  
 Há dois eixos com o nome de `Elements` que retornam uma coleção de elementos: o <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>método e o <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>método.</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> Você pode combinar esses dois eixos para localizar todos os elementos de um nome especificado em uma determinada profundidade na árvore.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>e <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>para localizar todos os `Name` elementos em todos os `Address` todos os elementos `PurchaseOrder` elementos.</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: várias ordens de compra (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 Isso funciona porque uma das implementações do `Elements` eixo é como um método de extensão dos <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer> </xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>deriva de <xref:System.Xml.Linq.XContainer>, portanto, você pode chamar o <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>método nos resultados de uma chamada para o <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>método.</xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XElement>  
  
## <a name="example"></a>Exemplo  
 Às vezes você deseja recuperar todos os elementos em uma profundidade específico do elemento quando pode ou não pode haver ancestrais interveniente. Por exemplo, o seguinte documento, você pode desejar recuperar todos os elementos de `ConfigParameter` que são filhos do elemento de `Customer` , mas não `ConfigParameter` que é um filho do elemento de `Root` .  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 Para fazer isso, você pode usar o <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>eixo, da seguinte maneira:</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma técnica para XML que é em um namespace. Para obter mais informações, consulte [trabalhar com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: várias ordens de compra em um Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
