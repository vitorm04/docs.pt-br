---
title: Como escrever consultas em XML em namespaces-LINQ to XML
description: Para gravar uma consulta em XML que está em um namespace, use objetos XName que têm o namespace correto. Saiba como fazer isso em C# e Visual Basic e como criar consultas.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 7d2c765c30409b019bf4723b9161c577e2074c04
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551888"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-linq-to-xml"></a><span data-ttu-id="e203a-104">Como escrever consultas em XML em namespaces (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e203a-104">How to write queries on XML in namespaces (LINQ to XML)</span></span>

<span data-ttu-id="e203a-105">Para gravar uma consulta em XML que está em um namespace, você deve usar <xref:System.Xml.Linq.XName> objetos que têm o namespace correto.</span><span class="sxs-lookup"><span data-stu-id="e203a-105">To write a query on XML that's in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>

<span data-ttu-id="e203a-106">Para C#, a abordagem mais comum é inicializar um <xref:System.Xml.Linq.XNamespace> usando uma cadeia de caracteres que contém o URI, em seguida, usar a sobrecarga de operador de adição para combinar o namespace com o nome local.</span><span class="sxs-lookup"><span data-stu-id="e203a-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>

<span data-ttu-id="e203a-107">Por Visual Basic, a abordagem mais comum é definir um namespace global e, em seguida, usar literais XML e propriedades XML que usam o namespace global.</span><span class="sxs-lookup"><span data-stu-id="e203a-107">For Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="e203a-108">Você pode definir um namespace global padrão nesse caso, no qual os elementos nos literais XML estarão no namespace por padrão.</span><span class="sxs-lookup"><span data-stu-id="e203a-108">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="e203a-109">Como alternativa, você pode definir um namespace global com um prefixo e, em seguida, usar o prefixo conforme necessário nos literais XML e nas propriedades XML.</span><span class="sxs-lookup"><span data-stu-id="e203a-109">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals and in XML properties.</span></span> <span data-ttu-id="e203a-110">Como ocorre com outros formatos de XML, os atributos estão sempre em nenhum namespace por padrão.</span><span class="sxs-lookup"><span data-stu-id="e203a-110">As with other forms of XML, attributes are always in no namespace by default.</span></span>

<span data-ttu-id="e203a-111">O primeiro exemplo neste artigo mostra como criar uma árvore XML em um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="e203a-111">The first example in this article shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="e203a-112">O segundo mostra como criar uma árvore XML em um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="e203a-112">The second shows how to create an XML tree in a namespace with a prefix.</span></span>

## <a name="example-create-a-tree-in-a-default-namespace-and-retrieve-elements"></a><span data-ttu-id="e203a-113">Exemplo: criar uma árvore em um namespace padrão e recuperar elementos</span><span class="sxs-lookup"><span data-stu-id="e203a-113">Example: Create a tree in a default namespace and retrieve elements</span></span>

<span data-ttu-id="e203a-114">O exemplo a seguir cria uma árvore XML que está em um namespace padrão e, em seguida, recupera uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="e203a-114">The following example creates an XML tree that's in a default namespace, and then retrieves a collection of elements.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
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
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
    End Sub
End Module
```

<span data-ttu-id="e203a-115">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e203a-115">This example produces the following output:</span></span>

```output
1
2
3
```

## <a name="example-create-a-tree-in-a-namespace-with-a-prefix-and-retrieve-elements"></a><span data-ttu-id="e203a-116">Exemplo: criar uma árvore em um namespace com um prefixo e recuperar elementos</span><span class="sxs-lookup"><span data-stu-id="e203a-116">Example: Create a tree in a namespace with a prefix and retrieve elements</span></span>

<span data-ttu-id="e203a-117">No C#, você escreve consultas da mesma maneira, independentemente de estar escrevendo consultas em uma árvore XML que usa um namespace com um prefixo ou em uma árvore XML com um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="e203a-117">In C#, you write queries in the same way regardless of whether you're writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>

<span data-ttu-id="e203a-118">O exemplo a seguir cria uma árvore XML que está em um namespace com um prefixo e, em seguida, recupera uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="e203a-118">The following example creates an XML tree that's in a namespace with a prefix, and then retrieves a collection of elements.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
    <aw:Child>1</aw:Child>
    <aw:Child>2</aw:Child>
    <aw:Child>3</aw:Child>
    <aw:AnotherChild>4</aw:AnotherChild>
    <aw:AnotherChild>5</aw:AnotherChild>
    <aw:AnotherChild>6</aw:AnotherChild>
</aw:Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>1</aw:Child>
                <aw:Child>2</aw:Child>
                <aw:Child>3</aw:Child>
                <aw:AnotherChild>4</aw:AnotherChild>
                <aw:AnotherChild>5</aw:AnotherChild>
                <aw:AnotherChild>6</aw:AnotherChild>
            </aw:Root>
        Dim c1 As IEnumerable(Of XElement) = _
            From el In root.<aw:Child> _
            Select el
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
    End Sub
End Module
```

<span data-ttu-id="e203a-119">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e203a-119">This example produces the following output:</span></span>

```output
1
2
3
```

## <a name="see-also"></a><span data-ttu-id="e203a-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="e203a-120">See also</span></span>

- [<span data-ttu-id="e203a-121">Visão geral dos namespaces</span><span class="sxs-lookup"><span data-stu-id="e203a-121">Namespaces overview</span></span>](namespaces-overview.md)
