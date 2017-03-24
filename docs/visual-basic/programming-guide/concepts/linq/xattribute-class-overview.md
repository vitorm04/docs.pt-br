---
title: "Visão geral da classe de XAttribute (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1ce5f4be6006908b35057854f89432471fd9f06b
ms.lasthandoff: 03/13/2017

---
# <a name="xattribute-class-overview-visual-basic"></a>Visão geral da classe de XAttribute (Visual Basic)
Os atributos são pares nome/valor que são associados a um elemento. O <xref:System.Xml.Linq.XAttribute>classe representa atributos XML.</xref:System.Xml.Linq.XAttribute>  
  
## <a name="overview"></a>Visão geral  
 Trabalhar com atributos em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é semelhante a trabalhar com elementos. Os construtores são semelhantes. Os métodos que você usa para recuperar coleções deless são semelhantes. A [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] expressão de consulta para uma coleção de atributos parece muito semelhante a um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] expressão para uma coleção de elementos de consulta.  
  
 A ordem em que os atributos foram adicionados a um elemento é preservada. Isto é, quando você itera através de atributos, você ver na mesma ordem que foram adicionados.  
  
## <a name="the-xattribute-constructor"></a>O construtor de XAttribute  
 O seguinte construtor da <xref:System.Xml.Linq.XAttribute>classe é aquele que você usará mais comumente:</xref:System.Xml.Linq.XAttribute>  
  
|Construtor|Descrição|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Cria um <xref:System.Xml.Linq.XAttribute>objeto.</xref:System.Xml.Linq.XAttribute> O argumento de `name` especifica o nome do atributo; `content` especifica o conteúdo de atributo.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Criando um elemento com um atributo  
 O código a seguir mostra um elemento que contém um atributo usando literais XML no Visual Basic:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Compilação funcional de atributos  
 Você pode construir <xref:System.Xml.Linq.XAttribute>objetos em linha com a construção de <xref:System.Xml.Linq.XElement>objetos, da seguinte maneira:</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute>  
  
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
 Há algumas diferenças entre atributos e elementos. <xref:System.Xml.Linq.XAttribute>objetos não são nós na árvore XML.</xref:System.Xml.Linq.XAttribute> São pares nome/valor associados com um elemento XML. Em contraste com Document Object Model (DOM), este reflete mais apertadamente a estrutura XML. Embora <xref:System.Xml.Linq.XAttribute>objetos não são realmente nós na árvore de XML, trabalhar com <xref:System.Xml.Linq.XAttribute>objetos é muito semelhante a trabalhar com <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XAttribute>  
  
 Essa distinção importante é primeiro somente para os desenvolvedores que estão escrevendo código que funciona com as árvores XML no nível do nó. Muitos desenvolvedores não serão preocupados com essa distinção.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ para visão geral da programação XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
