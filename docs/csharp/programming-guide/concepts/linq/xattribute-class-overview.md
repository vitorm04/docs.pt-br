---
title: "Visão geral da classe XAttribute (C#) | Microsoft Docs"
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
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e1b461158fed20ea5824d89ec455abb667d3fef2
ms.lasthandoff: 03/13/2017

---
# <a name="xattribute-class-overview-c"></a>Visão geral da classe XAttribute (C#)
Os atributos são pares nome/valor que são associados a um elemento. A classe <xref:System.Xml.Linq.XAttribute> representa atributos XML.  
  
## <a name="overview"></a>Visão geral  
 Trabalhar com atributos em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é semelhante a trabalhar com elementos. Os construtores são semelhantes. Os métodos que você usa para recuperar coleções deless são semelhantes. Uma expressão de consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para uma coleção de atributos se parece muito com uma expressão de consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para uma coleção de elementos.  
  
 A ordem em que os atributos foram adicionados a um elemento é preservada. Isto é, quando você itera através de atributos, você ver na mesma ordem que foram adicionados.  
  
## <a name="the-xattribute-constructor"></a>O construtor de XAttribute  
 O seguinte construtor da classe <xref:System.Xml.Linq.XAttribute> é aquele que você usará mais comumente:  
  
|Construtor|Descrição|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Cria um objeto <xref:System.Xml.Linq.XAttribute>. O argumento de `name` especifica o nome do atributo; `content` especifica o conteúdo de atributo.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Criando um elemento com um atributo  
 O código a seguir mostra a tarefa comum de criar um elemento que contém um atributo:  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Compilação funcional de atributos  
 Você pode construir objetos <xref:System.Xml.Linq.XAttribute> em linha com a construção de objetos <xref:System.Xml.Linq.XElement>, da seguinte maneira:  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 Este exemplo gera a seguinte saída:  
  
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
  
### <a name="attributes-are-not-nodes"></a>Os atributos não são nós  
 Há algumas diferenças entre atributos e elementos. Os objetos <xref:System.Xml.Linq.XAttribute> não são nós na árvore XML. São pares nome/valor associados com um elemento XML. Em contraste com Document Object Model (DOM), este reflete mais apertadamente a estrutura XML. Embora os objetos <xref:System.Xml.Linq.XAttribute> não sejam realmente nós na árvore de XML, trabalhar com objetos <xref:System.Xml.Linq.XAttribute> é muito semelhante a trabalhar com objetos <xref:System.Xml.Linq.XElement>.  
  
 Essa distinção importante é primeiro somente para os desenvolvedores que estão escrevendo código que funciona com as árvores XML no nível do nó. Muitos desenvolvedores não serão preocupados com essa distinção.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da programação LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
