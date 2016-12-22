---
title: "Criando &#225;rvores XML em C# (LINQ para XML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Criando &#225;rvores XML em C# (LINQ para XML)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta seção fornece informações sobre como criar árvores XML em c\#.  
  
 Para obter informações sobre como usar os resultados de consultas LINQ como o conteúdo de um <xref:System.Xml.Linq.XElement>, consulte [Construção funcional \(LINQ to XML\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
## Construindo elementos  
 As assinaturas da <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute> construtores permitem que você passe o conteúdo do elemento ou atributo como argumentos para o construtor. Porque um dos construtores recebe um número variável de argumentos, você pode passar qualquer número de elementos filho. Obviamente, cada um desses elementos filho pode conter seus próprios elementos filhos. Para qualquer elemento, você pode adicionar qualquer número de atributos.  
  
 Ao adicionar <xref:System.Xml.Linq.XNode> \(incluindo <xref:System.Xml.Linq.XElement>\) ou <xref:System.Xml.Linq.XAttribute> objetos, se o novo conteúdo não tem nenhum pai, os objetos serão simplesmente anexados à árvore XML. Se o novo conteúdo já tiver um pai e faz parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém\-clonado será anexado à árvore XML. O último exemplo neste tópico demonstra isso.  
  
 Para criar um `contacts`<xref:System.Xml.Linq.XElement>, você pode usar o código a seguir:  
  
```c#  
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
  
 Se recuado corretamente, o código para construir <xref:System.Xml.Linq.XElement> objetos parecida com a estrutura do XML subjacente.  
  
## Construtores de XElement  
 O <xref:System.Xml.Linq.XElement> classe usa os seguintes construtores na construção funcional. Observe que há outros construtores para <xref:System.Xml.Linq.XElement>, mas porque eles não são usados na construção funcional, eles não são listados aqui.  
  
|Construtor|Descrição|  
|----------------|---------------|  
|`XElement(XName name, object content)`|Cria um <xref:System.Xml.Linq.XElement>. O `name` parâmetro especifica o nome do elemento; `content` Especifica o conteúdo do elemento.|  
|`XElement(XName name)`|Cria um <xref:System.Xml.Linq.XElement> com seus <xref:System.Xml.Linq.XName> inicializada com o nome especificado.|  
|`XElement(XName name, params object[] content)`|Cria um <xref:System.Xml.Linq.XElement> com seus <xref:System.Xml.Linq.XName> inicializada com o nome especificado. Os atributos e\/ou elementos filho são criados a partir do conteúdo da lista de parâmetros.|  
  
 O `content` parâmetro é extremamente flexível. Ele oferece suporte a qualquer tipo de objeto que é um filho válido de um <xref:System.Xml.Linq.XElement>. As seguintes regras se aplicam a diferentes tipos de objetos passados neste parâmetro:  
  
-   Uma cadeia de caracteres é adicionada como conteúdo de texto.  
  
-   Um <xref:System.Xml.Linq.XElement> é adicionado como um elemento filho.  
  
-   Um <xref:System.Xml.Linq.XAttribute> é adicionado como um atributo.  
  
-   Um <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, ou <xref:System.Xml.Linq.XText> é adicionado como conteúdo filho.  
  
-   Um <xref:System.Collections.IEnumerable> é enumerada, e essas regras são aplicadas recursivamente aos resultados.  
  
-   Para qualquer outro tipo, sua `ToString` método é chamado e o resultado é adicionado como conteúdo de texto.  
  
### Criando um XElement com conteúdo  
 Você pode criar um <xref:System.Xml.Linq.XElement> que contém o conteúdo simples com uma única chamada de método. Para fazer isso, especifique o conteúdo como o segundo parâmetro, da seguinte maneira:  
  
```c#  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 Você pode passar qualquer tipo de objeto como o conteúdo. Por exemplo, o código a seguir cria um elemento que contém um flutuante número como conteúdo de ponto:  
  
```c#  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 O número é convertido e passado para o construtor de ponto flutuante. O número é convertido em uma cadeia de caracteres e usado como o conteúdo do elemento.  
  
### Criando um XElement com um elemento filho  
 Se você passar uma instância do <xref:System.Xml.Linq.XElement> classe para o argumento de conteúdo, o construtor cria um elemento com um elemento filho:  
  
```c#  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### Criando um XElement com vários elementos filho  
 Você pode passar um número de <xref:System.Xml.Linq.XElement> objetos para o conteúdo. Cada um do <xref:System.Xml.Linq.XElement> objetos é incluído como um elemento filho.  
  
```c#  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 Estendendo o exemplo acima, você pode criar uma árvore XML inteira, da seguinte maneira:  
  
```c#  
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
  
 Este exemplo produz a seguinte saída:  
  
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
  
### Criando um elemento vazio  
 Para criar um vazio <xref:System.Xml.Linq.XElement>, você não passar qualquer conteúdo para o construtor. O exemplo a seguir cria um elemento vazio:  
  
```c#  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Customer />  
```  
  
### Anexar vs. Clonagem  
 Como mencionado anteriormente, ao adicionar <xref:System.Xml.Linq.XNode> \(incluindo <xref:System.Xml.Linq.XElement>\) ou <xref:System.Xml.Linq.XAttribute> objetos, se o novo conteúdo não tem nenhum pai, os objetos serão simplesmente anexados à árvore XML. Se o novo conteúdo já tiver um pai e faz parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém\-clonado será anexado à árvore XML.  
  
```c#  
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
  
 Este exemplo produz a seguinte saída:  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## Consulte também  
 [Criando árvores XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)