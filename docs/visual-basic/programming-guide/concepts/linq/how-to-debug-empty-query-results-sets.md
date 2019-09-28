---
title: 'Como: Depurar conjuntos de resultados de consulta vazios (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 6fc194432b1d44c1214da32d2c6978a4eeb316dc
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351784"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="b345d-102">Como: Depurar conjuntos de resultados de consulta vazios (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b345d-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="b345d-103">Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b345d-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="b345d-104">Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, e deduzido de modo inadequado.</span><span class="sxs-lookup"><span data-stu-id="b345d-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="b345d-105">O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="b345d-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="b345d-106">Para obter mais informações, consulte [visão geral de namespaces (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b345d-106">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>

## <a name="example"></a><span data-ttu-id="b345d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b345d-107">Example</span></span>

<span data-ttu-id="b345d-108">Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.</span><span class="sxs-lookup"><span data-stu-id="b345d-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

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

<span data-ttu-id="b345d-109">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="b345d-109">This example produces the following result:</span></span>

```console
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="b345d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b345d-110">Example</span></span>

<span data-ttu-id="b345d-111">Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.</span><span class="sxs-lookup"><span data-stu-id="b345d-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="b345d-112">A solução é declarar e inicializar um namespace padrão global.</span><span class="sxs-lookup"><span data-stu-id="b345d-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="b345d-113">Isso coloca todas as propriedades XML no namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="b345d-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="b345d-114">Outras alterações necessárias ao exemplo para fazê-lo funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="b345d-114">No other modifications are required to the example to make it work properly.</span></span>

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

<span data-ttu-id="b345d-115">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="b345d-115">This example produces the following result:</span></span>

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="b345d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b345d-116">See also</span></span>

- [<span data-ttu-id="b345d-117">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b345d-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
