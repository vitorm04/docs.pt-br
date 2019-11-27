---
title: Escopo de namespaces padrão
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: 8ba4d13b6d40180a88651f0503d1323f2b78f36c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343654"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a>Escopo de namespaces padrão no Visual Basic
Namespaces padrões como representadas na árvore XML não estiver no escopo para consultas. Se você tiver XML que é em um namespace padrão, você ainda deve declarar uma variável de <xref:System.Xml.Linq.XNamespace> , e combina-o com o nome local para fazer um nome qualificado para ser usado na consulta.  
  
 Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.  
  
 Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, mas é visto de modo inadequado.  
  
 O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.  
  
### <a name="code"></a>Código  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Comments  
 Este exemplo gerencia o resultado seguinte:  
  
```console  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.  
  
 Ao contrário do exemplo codificado incorretamente acima, a abordagem correta ao usar Visual Basic é declarar e inicializar um namespace padrão global. Isso coloca todas as propriedades XML no namespace padrão. Outras alterações necessárias ao exemplo para fazê-lo funcionar corretamente.  
  
### <a name="code"></a>Código  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Comments  
 Este exemplo gerencia o resultado seguinte:  
  
```console  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de namespaces (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
