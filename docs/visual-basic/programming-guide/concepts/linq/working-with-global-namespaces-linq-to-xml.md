---
title: "Trabalhar com namespaces globais (Visual Basic) (LINQ to XML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Trabalhar com namespaces globais (Visual Basic) (LINQ to XML)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um dos principais recursos dos literais XML no Visual Basic é a capacidade de declarar namespaces XML usando o `Imports` instrução. Usando esse recurso, você pode declarar um namespace XML que usa um prefixo, ou você pode declarar um namespace XML padrão.  
  
 Esse recurso é útil em duas situações. Primeiro, namespaces declaradas em literais XML não transferem em expressões inseridas. Declarar namespaces globais reduz a quantidade de trabalho que você precisa fazer para usar expressões inseridas com namespaces. Em segundo lugar, você deve declarar namespaces globais para usar namespaces com propriedades XML.  
  
 Você pode declarar namespaces globais no nível do projeto. Você também pode declarar namespaces globais no nível de módulo, que substitui os namespaces globais no nível do projeto. Por fim, você pode substituir namespaces globais em um literal XML.  
  
 Ao usar literais XML ou propriedades XML que estão em namespaces globais\-declaradas, você pode ver o nome expandido de literais XML ou propriedades focalizando sobre eles no Visual Studio. Você verá o nome expandido em uma dica de ferramenta.  
  
 Você pode obter um <xref:System.Xml.Linq.XNamespace> objeto corresponde a um namespace global usando o `GetXmlNamespace` método.  
  
## Exemplos de Namespaces globais  
 O exemplo a seguir declara um namespace global padrão usando o `Imports` instrução e, em seguida, usa um literal XML para inicializar um <xref:System.Xml.Linq.XElement> objeto nesse namespace:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 O exemplo a seguir declara um namespace global com um prefixo e, em seguida, usa um literal XML para inicializar um elemento:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## Namespaces globais e expressões incorporadas  
 Namespaces são declaradas em literais XML não transferem em expressões inseridas. O exemplo a seguir declara um namespace padrão. Ele usa uma expressão inserida para o `Child` elemento.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
 Como você pode ver, o XML resultante inclui uma declaração de namespace padrão para que o `Child` elemento está em qualquer namespace.  
  
 Você pode declarar novamente o namespace na expressão inserida, da seguinte maneira:  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 No entanto, isso é mais complicado de usar do que o namespace global padrão, que é uma melhor abordagem. Com o namespace global padrão, você pode usar literais XML sem declarar namespaces. O XML resultante será no namespace padrão declarado globalmente.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## Usando Namespaces XML com propriedades  
 Se você estiver trabalhando com uma árvore XML que está em um namespace e usar propriedades XML, você deve usar um namespace global para que as propriedades XML também será o namespace correto. O exemplo a seguir declara uma árvore XML em um namespace. Em seguida, imprime a contagem de `Child` elementos.  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Este exemplo indica que não há nenhum `Child` elementos. Ele produz a seguinte saída:  
  
```  
0  
```  
  
 Se, no entanto, você pode declarar um namespace global padrão, então a literal XML e a propriedade XML estão no namespace global padrão:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 Este exemplo indica que há um `Child` elemento. Ele produz a seguinte saída:  
  
```  
1  
```  
  
 Se você declarar um namespace global que tem um prefixo, você pode usar o prefixo para literais XML e propriedades XML:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## XNamespace e Namespaces globais  
 Você pode obter um <xref:System.Xml.Linq.XNamespace> objeto usando o `GetXmlNamespace` método:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 Este exemplo produz a seguinte saída:  
  
```  
http://www.adventure-works.com  
```  
  
## Consulte também  
 [Trabalhando com Namespaces XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)