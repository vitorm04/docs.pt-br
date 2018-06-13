---
title: Exemplo de execução adiada (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
ms.openlocfilehash: a9827b73ebc0df589a14032d99b32d1e1bc891ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642123"
---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="4e705-102">Exemplo de execução adiada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e705-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="4e705-103">Este tópico mostra como execução adiada e a avaliação lazy afetam a execução das consultas LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="4e705-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e705-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e705-104">Example</span></span>  
 <span data-ttu-id="4e705-105">O exemplo a seguir mostra a ordem de execução para usar um método de extensão que use a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="4e705-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="4e705-106">O exemplo declara uma matriz de três cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4e705-106">The example declares an array of three strings.</span></span> <span data-ttu-id="4e705-107">Em itera através da coleção retornada por `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="4e705-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
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
  
 <span data-ttu-id="4e705-108">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="4e705-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="4e705-109">Observe que para iterar através da coleção retornada por `ConvertCollectionToUpperCase`, cada item é recuperado de matriz de cadeias de caracteres de origem e convertido para maiúsculas antes que o próximo item é recuperado de matriz de cadeias de caracteres de origem.</span><span class="sxs-lookup"><span data-stu-id="4e705-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="4e705-110">Você pode ver que a matriz inteira de cadeias de caracteres não é convertida para maiúsculas antes que cada item na coleção retornada é processado no loop de `foreach` em `Main`.</span><span class="sxs-lookup"><span data-stu-id="4e705-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e705-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e705-111">See Also</span></span>  
 [<span data-ttu-id="4e705-112">Tutorial: Adiada execução (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e705-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
