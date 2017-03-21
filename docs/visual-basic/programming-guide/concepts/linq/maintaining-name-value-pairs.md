---
title: Mantendo pares de nome-valor (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 54db297ecd39e37492dcf8bb4de4f64476662670
ms.lasthandoff: 03/13/2017


---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Mantendo pares de nome/valor (Visual Basic)
Muitos aplicativos devem manter informações que são melhor armazenadas como pares de valor/nome. Essas informações podem ser informações de configuração ou configurações globais. O [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] contém alguns métodos que facilitam o trabalho de manter um conjunto de pares de valor/nome. É possível manter informações como atributos ou como um conjunto de elementos filho.  
  
 Uma das diferenças entre manter as informações como atributos ou como elementos filho é que os atributos possuem a restrição de que pode existir apenas um atributo com um nome específico para um elemento. Essa limitação não se aplica aos elementos filho.  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue e SetElementValue  
 Os dois métodos que facilitam a manutenção de nome/valor pares são <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>e <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</xref:System.Xml.Linq.XElement.SetElementValue%2A> </xref:System.Xml.Linq.XElement.SetAttributeValue%2A> Esses dois métodos possuem semântica semelhante.  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>pode adicionar, modificar ou remover atributos de um elemento.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>com um nome de um atributo que não existe, o método cria um novo atributo e o adiciona ao elemento especificado.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>com um nome de um atributo existente e algum especificado conteúdo, o conteúdo do atributo é substituído pelo conteúdo especificado.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>com um nome de um objeto existente do atributo e especifique null para o conteúdo, o atributo é removido de seu pai.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>pode adicionar, modificar ou remover elementos filho de um elemento.</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A>com o nome de um elemento filho que não existe, o método cria um novo elemento e o adiciona ao elemento especificado.</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A>com um nome de um elemento existente e algum especificado conteúdo, o conteúdo do elemento é substituído pelo conteúdo especificado.</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
-   Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A>com o nome de um elemento existente e especificar nulo para o conteúdo, o elemento é removido de seu pai.</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um elemento sem atributos. Ele usa o <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>método para criar e manter uma lista de pares nome/valor.</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um elemento sem elementos filho. Ele usa o <xref:System.Xml.Linq.XElement.SetElementValue%2A>método para criar e manter uma lista de pares nome/valor.</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A></xref:System.Xml.Linq.XElement.SetAttributeValue%2A>   
 <xref:System.Xml.Linq.XElement.SetElementValue%2A></xref:System.Xml.Linq.XElement.SetElementValue%2A>   
 [Modificando árvores XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
