---
title: Escopo de namespace padrão no Visual Basic
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: e33505dd8e8ad94e3c758f15f245d0cbaf6987bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836708"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="ebc2d-102">Escopo de namespace padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebc2d-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="ebc2d-103">Namespaces padrões como representadas na árvore XML não estiver no escopo para consultas.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="ebc2d-104">Se você tiver XML que é em um namespace padrão, você ainda deve declarar uma variável de <xref:System.Xml.Linq.XNamespace> , e combina-o com o nome local para fazer um nome qualificado para ser usado na consulta.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="ebc2d-105">Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="ebc2d-106">Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, mas é visto de modo inadequado.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="ebc2d-107">O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebc2d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebc2d-108">Example</span></span>  
 <span data-ttu-id="ebc2d-109">Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ebc2d-110">Código</span><span class="sxs-lookup"><span data-stu-id="ebc2d-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="ebc2d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebc2d-111">Comments</span></span>  
 <span data-ttu-id="ebc2d-112">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="ebc2d-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="ebc2d-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebc2d-113">Example</span></span>  
 <span data-ttu-id="ebc2d-114">Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="ebc2d-115">Em contraste com incorretamente codificado o exemplo acima, a abordagem correta ao usar o Visual Basic é declarar e inicializar um namespace global padrão.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="ebc2d-116">Isso coloca todas as propriedades XML no namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="ebc2d-117">Outras alterações necessárias ao exemplo para fazê-lo funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="ebc2d-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ebc2d-118">Código</span><span class="sxs-lookup"><span data-stu-id="ebc2d-118">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="ebc2d-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebc2d-119">Comments</span></span>  
 <span data-ttu-id="ebc2d-120">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="ebc2d-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebc2d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebc2d-121">See also</span></span>

- [<span data-ttu-id="ebc2d-122">Trabalhando com Namespaces XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebc2d-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
