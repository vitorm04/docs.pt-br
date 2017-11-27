---
title: 'Como: depurar conjuntos de resultados de consulta vazia (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c483153f8ff41c08cfaa0141fed056de7f5f680
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="c780b-102">Como: depurar conjuntos de resultados de consulta vazia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c780b-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>
<span data-ttu-id="c780b-103">Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.</span><span class="sxs-lookup"><span data-stu-id="c780b-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="c780b-104">Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, e deduzido de modo inadequado.</span><span class="sxs-lookup"><span data-stu-id="c780b-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="c780b-105">O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="c780b-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="c780b-106">Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="c780b-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c780b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c780b-107">Example</span></span>  
 <span data-ttu-id="c780b-108">Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.</span><span class="sxs-lookup"><span data-stu-id="c780b-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```vb  
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
```  
  
 <span data-ttu-id="c780b-109">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="c780b-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="c780b-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c780b-110">Example</span></span>  
 <span data-ttu-id="c780b-111">Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.</span><span class="sxs-lookup"><span data-stu-id="c780b-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="c780b-112">A solução é declarar e inicializar um namespace padrão global.</span><span class="sxs-lookup"><span data-stu-id="c780b-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="c780b-113">Isso coloca todas as propriedades XML no namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="c780b-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="c780b-114">Outras alterações necessárias ao exemplo para fazê-lo funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="c780b-114">No other modifications are required to the example to make it work properly.</span></span>  
  
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
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c780b-115">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="c780b-115">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="c780b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c780b-116">See Also</span></span>  
 [<span data-ttu-id="c780b-117">Consultas básicas (LINQ para XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c780b-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
