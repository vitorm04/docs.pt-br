---
title: "Escopo de namespace padrão no Visual Basic | Documentos do Microsoft"
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
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 138115cb1a5ec2e2c513419a32a9ebaec9c90d61
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="7018f-102">Escopo de namespace padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7018f-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="7018f-103">Namespaces padrões como representadas na árvore XML não estiver no escopo para consultas.</span><span class="sxs-lookup"><span data-stu-id="7018f-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="7018f-104">Se você tiver XML que está em um namespace padrão, você ainda deve declarar um <xref:System.Xml.Linq.XNamespace>variável e combiná-lo com o nome do local para um nome qualificado para ser usado na consulta.</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="7018f-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="7018f-105">Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.</span><span class="sxs-lookup"><span data-stu-id="7018f-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="7018f-106">Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, mas é visto de modo inadequado.</span><span class="sxs-lookup"><span data-stu-id="7018f-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="7018f-107">O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.</span><span class="sxs-lookup"><span data-stu-id="7018f-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7018f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7018f-108">Example</span></span>  
 <span data-ttu-id="7018f-109">Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.</span><span class="sxs-lookup"><span data-stu-id="7018f-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7018f-110">Código</span><span class="sxs-lookup"><span data-stu-id="7018f-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="7018f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7018f-111">Comments</span></span>  
 <span data-ttu-id="7018f-112">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="7018f-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="7018f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7018f-113">Example</span></span>  
 <span data-ttu-id="7018f-114">Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.</span><span class="sxs-lookup"><span data-stu-id="7018f-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="7018f-115">Em contraste com incorretamente codificado o exemplo acima, a abordagem correta para usar o Visual Basic é declarar e inicializar um namespace global padrão.</span><span class="sxs-lookup"><span data-stu-id="7018f-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="7018f-116">Isso coloca todas as propriedades XML no namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="7018f-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="7018f-117">Outras alterações necessárias ao exemplo para fazê-lo funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="7018f-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7018f-118">Código</span><span class="sxs-lookup"><span data-stu-id="7018f-118">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="7018f-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="7018f-119">Comments</span></span>  
 <span data-ttu-id="7018f-120">Este exemplo gerencia o resultado seguinte:</span><span class="sxs-lookup"><span data-stu-id="7018f-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="7018f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7018f-121">See Also</span></span>  
 [<span data-ttu-id="7018f-122">Trabalhando com Namespaces XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7018f-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
