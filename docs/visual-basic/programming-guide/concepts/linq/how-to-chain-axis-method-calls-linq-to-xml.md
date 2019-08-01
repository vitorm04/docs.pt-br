---
title: 'Como: Chamadas de método de eixo de cadeia (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
ms.openlocfilehash: 8c607915d83c49958e3aa86c9625fa1311a2274b
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709830"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a>Como: Chamadas de método de eixo de cadeia (LINQ to XML) (Visual Basic)
Um padrão comum que você usar em seu código é chamar um método do eixo, então chama um dos eixos do método de extensão.  
  
 Há dois eixos com o nome de `Elements` que retornam uma coleção de elementos: o método de <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> e o método de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> . Você pode combinar esses dois eixos para localizar todos os elementos de um nome especificado em uma determinada profundidade na árvore.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> e <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> para localizar todos os elementos de `Name` em todos os elementos de `Address` em todos os elementos de `PurchaseOrder` .  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 Isto funciona porque uma das implementações do eixo de `Elements` é como um método de extensão em <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XContainer>. <xref:System.Xml.Linq.XElement> deriva de <xref:System.Xml.Linq.XContainer>, então você pode chamar o método de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> nos resultados de uma chamada para o método de <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> .  
  
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
  
 Para fazer isso, você pode usar o eixo de <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> , como segue:  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma técnica para XML que é em um namespace. Para obter mais informações, consulte [visão geral de namespaces (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra em um namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>Consulte também

- [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
