---
title: "Adiado exemplo de execução (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ff3d6988ce826fea0aee1987a7c546f5c863e71d
ms.lasthandoff: 03/13/2017


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
