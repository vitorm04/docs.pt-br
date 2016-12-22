---
title: "Vis&#227;o geral da classe de XAttribute (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vis&#227;o geral da classe de XAttribute (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Atributos são pares de nome\/valor associados um elemento. O <xref:System.Xml.Linq.XAttribute> classe representa atributos XML.  
  
## Visão Geral  
 Trabalhando com atributos em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é semelhante a trabalhar com elementos. Os construtores são semelhantes. Os métodos que você pode usar para recuperar coleções deles são semelhantes. Um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] expressão de consulta para uma coleção de atributos parece muito semelhante a um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] expressão para uma coleção de elementos de consulta.  
  
 A ordem na qual os atributos foram adicionados a um elemento é preservada. Ou seja, quando você itera através de atributos, você vê\-los na mesma ordem em que eles foram adicionados.  
  
## O construtor de XAttribute  
 O seguinte construtor da <xref:System.Xml.Linq.XAttribute> classe é o que você mais usará:  
  
|Construtor|Descrição|  
|----------------|---------------|  
|`XAttribute(XName name, object content)`|Cria um <xref:System.Xml.Linq.XAttribute> objeto. O `name` argumento especifica o nome do atributo; `content` Especifica o conteúdo do atributo.|  
  
### Criando um elemento com um atributo  
 O código a seguir mostra um elemento que contém um atributo usando literais XML no Visual Basic:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### Construção funcional de atributos  
 Você pode construir <xref:System.Xml.Linq.XAttribute> objetos em linha com a construção de <xref:System.Xml.Linq.XElement> objetos, da seguinte maneira:  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### Atributos não são nós  
 Existem algumas diferenças entre elementos e atributos.<xref:System.Xml.Linq.XAttribute> objetos não são nós na árvore XML. Eles são pares de nome\/valor associados a um elemento XML. Em contraste com o DOM Document Object Model \(\), isso melhor reflete a estrutura do XML. Embora <xref:System.Xml.Linq.XAttribute> objetos não são realmente nós na árvore de XML, trabalhar com <xref:System.Xml.Linq.XAttribute> objetos é muito semelhante a trabalhar com <xref:System.Xml.Linq.XElement> objetos.  
  
 Essa distinção é importante principalmente somente para os desenvolvedores que estão escrevendo código que funciona com árvores XML no nível de nó. Muitos desenvolvedores não serão preocupados com essa distinção.  
  
## Consulte também  
 [LINQ para visão geral da programação XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)