---
title: Trabalhar com namespaces globais (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 80510e370e0a9c7ab27cb5177d9b547ead82715c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350990"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>Trabalhar com namespaces globais (Visual Basic) (LINQ to XML)
One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement. Usando esse recurso, você pode declarar um namespace XML que usa um prefixo, ou você pode declarar um namespace XML padrão.  
  
 Esse recurso é útil em duas situações. Primeiro, namespaces declaradas em literais XML não transferem em expressões inseridas. Declarar namespaces globais reduz a quantidade de trabalho que você tem que fazer para usar expressões inseridas com namespaces. Segundo, você deve declarar namespaces globais para usar namespaces com propriedades XML.  
  
 Você pode declarar namespaces globais no nível do projeto. Você também pode declarar namespaces globais em nível de módulo, que substitui namespaces globais no nível de projeto. Finalmente, você pode substituir namespaces globais em um literal XML.  
  
 Ao usar as literal XML ou propriedades XML que estão em namespaces globais - declaradas, você pode ver o nome do literal XML ou propriedades focalizando sobre eles em Visual Studio. Você verá o nome expandido em uma dica de ferramenta.  
  
 Você pode obter um objeto de <xref:System.Xml.Linq.XNamespace> que corresponde a um namespace global usando o método `GetXmlNamespace` .  
  
## <a name="examples-of-global-namespaces"></a>Exemplos de namespaces globais  
 O exemplo a seguir declara um namespace global padrão usando a instrução de `Imports` em seguida, usa uma literal XML para inicializar um objeto de <xref:System.Xml.Linq.XElement> nesse namespace:  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 O exemplo a seguir declara um namespace global com um prefixo em seguida, usa uma literal XML para inicializar um elemento:  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a>Namespaces globais e expressões inseridas  
 Namespaces que são declaradas em literais XML não transferem em expressões inseridas. O exemplo a seguir declara um namespace padrão. Usar uma expressão inserida para o elemento de `Child` .  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 Como você pode ver, XML resultante inclui uma declaração de namespace padrão para que o elemento de `Child` está em qualquer namespace.  
  
 Você pode declarar novamente o namespace na expressão inserida, como segue:  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 No entanto, isso é mais incômodo usar que o namespace global padrão, que é uma abordagem melhor. Com o namespace global padrão, você pode usar literais XML sem declarar namespaces. XML resultante será no namespace padrão globais - declarada.  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a>Usando namespaces XML com propriedades  
 Se você estiver trabalhando com uma árvore XML que está em um namespace, e você usa propriedades XML, então você deve usar um namespace global de modo que as propriedades XML também estão no namespace correta. O exemplo a seguir declara uma árvore XML em um namespace. Imprime na contagem de elementos de `Child` .  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 Este exemplo indica que não há nenhum elemento de `Child` . Gerencia a saída a seguir:  
  
```console  
0  
```  
  
 Se, no entanto, você declarar um namespace global padrão, então a literal XML e a propriedade XML estão no namespace global padrão:  
  
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
  
 Este exemplo indica que há um elemento de `Child` . Gerencia a saída a seguir:  
  
```console  
1  
```  
  
 Se você declarar um namespace global que tenha um prefixo, você pode usar o prefixo para literais XML e propriedades XML:  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace e namespaces globais  
 Você pode obter um objeto de <xref:System.Xml.Linq.XNamespace> usando o método `GetXmlNamespace` :  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```console  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>Consulte também

- [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
