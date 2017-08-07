---
title: "Criando árvores XML em C# (LINQ para XML)"
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
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ac95fcf49736b554c8a3d4d0061f63b3ac4d3f65
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>Criando árvores XML em C# (LINQ para XML)
Esta seção fornece informações sobre a criação de árvores XML em C#.  
  
 Para obter informações sobre como usar os resultados de consultas LINQ como o conteúdo de um <xref:System.Xml.Linq.XElement>, consulte [Construção funcional (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## <a name="constructing-elements"></a>Construindo elementos  
 As assinaturas dos construtores <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute> permitem que você passe o conteúdo do elemento ou atributo como argumentos para o construtor. Como um dos construtores recebe um número variável de argumentos, você pode passar qualquer número de elementos filhos. Naturalmente, cada um desses elementos filhos pode conter seus próprios elementos filhos. Para qualquer elemento, você pode adicionar a quantidade desejada de atributos.  
  
 Ao adicionar objetos <xref:System.Xml.Linq.XNode> (inclusive <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver um pai, os objetos serão simplesmente anexados à árvore XML. Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML. O último exemplo deste tópico demonstra isso.  
  
 Para criar um `contacts`<xref:System.Xml.Linq.XElement>, você pode usar o seguinte código:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Se recuado corretamente, o código para criar objetos <xref:System.Xml.Linq.XElement> é muito parecido com a estrutura do XML subjacente.  
  
## <a name="xelement-constructors"></a>Construtores de XElement  
 A classe <xref:System.Xml.Linq.XElement> usa os seguintes construtores na construção funcional. Observe que há outros construtores para <xref:System.Xml.Linq.XElement>, mas como eles não são usados na construção funcional, eles não são listados aqui.  
  
|Construtor|Descrição|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|Cria um <xref:System.Xml.Linq.XElement>. O parâmetro `name` especifica o nome do elemento; `content` especifica o conteúdo do elemento.|  
|`XElement(XName name)`|Cria um <xref:System.Xml.Linq.XElement> com seu <xref:System.Xml.Linq.XName> inicializado para o nome especificado.|  
|`XElement(XName name, params object[] content)`|Cria um <xref:System.Xml.Linq.XElement> com seu <xref:System.Xml.Linq.XName> inicializado para o nome especificado. Os atributos e/ou elementos filhos são criados a partir do conteúdo da lista de parâmetros.|  
  
 O parâmetro `content` é muito flexível. Ele dá suporte a qualquer tipo de objeto que seja um filho válido de um <xref:System.Xml.Linq.XElement>. As seguintes regras se aplicam aos diferentes tipos de objetos passados neste parâmetro:  
  
-   Uma cadeia de caracteres é adicionada como conteúdo de texto.  
  
-   Um <xref:System.Xml.Linq.XElement> é adicionado como um elemento filho.  
  
-   Um <xref:System.Xml.Linq.XAttribute> é adicionado como um atributo.  
  
-   Um <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> ou <xref:System.Xml.Linq.XText> é adicionado como conteúdo filho.  
  
-   Um <xref:System.Collections.IEnumerable> é enumerado, e essas regras são aplicadas recursivamente aos resultados.  
  
-   Para qualquer outro tipo, seu método `ToString` é chamado e o resultado é adicionado como conteúdo de texto.  
  
### <a name="creating-an-xelement-with-content"></a>Criando um XElement com conteúdo  
 Você pode criar um <xref:System.Xml.Linq.XElement> contendo o conteúdo simples com uma única chamada de método. Para fazer isso, especifique o conteúdo como o segundo parâmetro, como segue:  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Você pode passar qualquer tipo de objeto como o conteúdo. Por exemplo, o seguinte código cria um elemento que contém um número de ponto flutuante como conteúdo:  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 O número de ponto flutuante foi convertido e passado para o construtor. O número é convertido em uma cadeia de caracteres e usado como o conteúdo do elemento.  
  
### <a name="creating-an-xelement-with-a-child-element"></a>Criando um XElement com um elemento filho  
 Se você passar uma instância da classe <xref:System.Xml.Linq.XElement> para o argumento de conteúdo, o construtor criará um elemento com um elemento filho:  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>Criando um XElement com vários elementos filhos  
 Você pode passar um número de objetos <xref:System.Xml.Linq.XElement> para o conteúdo. Cada um dos objetos <xref:System.Xml.Linq.XElement> é incluído como um elemento filho.  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 Por extensão ao exemplo anterior, você pode criar uma árvore XML inteira, desta forma:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),                                                   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  
  
### <a name="creating-an-empty-element"></a>Criando um elemento vazio  
 Para criar um <xref:System.Xml.Linq.XElement> vazio, você não passa conteúdo para o construtor. O seguinte exemplo cria um elemento vazio:  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>Anexar vs. Clonar  
 Conforme citado anteriormente, ao adicionar objetos <xref:System.Xml.Linq.XNode> (inclusive <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver um pai, os objetos serão simplesmente anexados à árvore XML. Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

