---
title: Exemplo de execução adiada (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: a9827b73ebc0df589a14032d99b32d1e1bc891ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="deferred-execution-example-visual-basic"></a>Exemplo de execução adiada (Visual Basic)
Este tópico mostra como execução adiada e a avaliação lazy afetam a execução das consultas LINQ to XML.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a ordem de execução para usar um método de extensão que use a execução adiada. O exemplo declara uma matriz de três cadeias de caracteres. Em itera através da coleção retornada por `ConvertCollectionToUpperCase`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module Module1  
  
    <Extension()>  
    Private Iterator Function ConvertCollectionToUpperCase(  
    ByVal source As IEnumerable(Of String)) _  
    As IEnumerable(Of String)   
        For Each str As String In source  
            Console.WriteLine("ToUpper: source {0}", str)   
            Yield str.ToUpper()  
        Next  
    End Function  
  
    Sub Main()  
        Dim stringArray = New String() {"abc", "def", "ghi"}  
  
        Dim q = From str In stringArray.ConvertCollectionToUpperCase()  
                Select str  
  
        For Each Str As String In q  
            Console.WriteLine("Main: str {0}", Str)   
        Next  
    End Sub  
  
End Module  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Observe que para iterar através da coleção retornada por `ConvertCollectionToUpperCase`, cada item é recuperado de matriz de cadeias de caracteres de origem e convertido para maiúsculas antes que o próximo item é recuperado de matriz de cadeias de caracteres de origem.  
  
 Você pode ver que a matriz inteira de cadeias de caracteres não é convertida para maiúsculas antes que cada item na coleção retornada é processado no loop de `foreach` em `Main`.  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: Adiada execução (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
