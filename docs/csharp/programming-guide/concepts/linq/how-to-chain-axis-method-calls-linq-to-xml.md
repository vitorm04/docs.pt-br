---
title: "Como encadear chamadas de método de eixo (LINQ to XML) (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a47129d3c84d7bfb49929529a50b064c8424b4c3
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a>Como encadear chamadas de método de eixo (LINQ to XML) (C#)
Um padrão comum que você usar em seu código é chamar um método do eixo, então chama um dos eixos do método de extensão.  
  
 Há dois eixos com o nome de `Elements` que retornam uma coleção de elementos: o método <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> e o método <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>. Você pode combinar esses dois eixos para localizar todos os elementos de um nome especificado em uma determinada profundidade na árvore.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> e <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> para localizar todos os elementos `Name` em todos os elementos `Address` em todos os elementos `PurchaseOrder`.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
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
  
 Isso funciona porque uma das implementações do eixo `Elements` é como um método de extensão em <xref:System.Collections.Generic.IEnumerable%601> da <xref:System.Xml.Linq.XContainer>. A <xref:System.Xml.Linq.XElement> deriva da <xref:System.Xml.Linq.XContainer>, portanto, você pode chamar o método <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> nos resultados de uma chamada ao método <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>.  
  
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
  
 Para fazer isso, você pode usar o eixo <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> da seguinte maneira:  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma técnica para XML que é em um namespace. Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: vários pedidos de compra em um namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
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
 [Eixos do LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
