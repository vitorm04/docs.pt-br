---
title: Escopo de namespaces padrão-LINQ to XML
description: Os namespaces padrão, conforme representado na árvore XML, não estão no escopo de consultas. Aqui estão as maneiras adequadas e inadequadas de consultá-las.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552323"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a><span data-ttu-id="089c3-104">Escopo de namespaces padrão (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="089c3-104">Scope of default namespaces (LINQ to XML)</span></span>

<span data-ttu-id="089c3-105">Os namespaces padrão, conforme representado na árvore XML, não estão no escopo de consultas.</span><span class="sxs-lookup"><span data-stu-id="089c3-105">Default namespaces as represented in the XML tree aren't in scope for queries.</span></span> <span data-ttu-id="089c3-106">Se você tiver um XML que esteja em um namespace padrão, deverá combinar um namespace com o nome local para fazer com que um nome qualificado seja usado na consulta.</span><span class="sxs-lookup"><span data-stu-id="089c3-106">If you have XML that's in a default namespace, you must combine a namespace with the local name to make a qualified name to be used in the query.</span></span>

<span data-ttu-id="089c3-107">Um erro comum na consulta de uma árvore XML que tem um namespace padrão é gravar a consulta como se o XML estivesse em um namespace.</span><span class="sxs-lookup"><span data-stu-id="089c3-107">A common mistake in querying an XML tree that has a default namespace is to write the query as if the XML weren't in a namespace.</span></span> <span data-ttu-id="089c3-108">O primeiro exemplo mostra uma consulta imprópria típica de um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="089c3-108">The first example shows a typical improper query of a default namespace.</span></span> <span data-ttu-id="089c3-109">O segundo mostra uma consulta apropriada.</span><span class="sxs-lookup"><span data-stu-id="089c3-109">The second shows a proper query.</span></span>

## <a name="example-improper-query-of-xml-in-a-namespace"></a><span data-ttu-id="089c3-110">Exemplo: consulta inadequada de XML em um namespace</span><span class="sxs-lookup"><span data-stu-id="089c3-110">Example: Improper query of XML in a namespace</span></span>

<span data-ttu-id="089c3-111">Este exemplo mostra a criação de XML em um namespace e uma consulta inadequada que retorna um conjunto de resultados vazio.</span><span class="sxs-lookup"><span data-stu-id="089c3-111">This example shows the creation of XML in a namespace, and an improper query that returns an empty result set.</span></span>

```csharp
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
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

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

<span data-ttu-id="089c3-112">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="089c3-112">This example produces the following output:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a><span data-ttu-id="089c3-113">Exemplo: consulta apropriada de XML em um namespace</span><span class="sxs-lookup"><span data-stu-id="089c3-113">Example:  Proper query of XML in a namespace</span></span>

<span data-ttu-id="089c3-114">Este exemplo mostra a criação de XML em um namespace e uma consulta apropriada.</span><span class="sxs-lookup"><span data-stu-id="089c3-114">This example shows the creation of XML in a namespace, and a proper query.</span></span>

<span data-ttu-id="089c3-115">No C#, a abordagem correta é declarar e inicializar um <xref:System.Xml.Linq.XNamespace> objeto e usá-lo ao especificar <xref:System.Xml.Linq.XName> objetos.</span><span class="sxs-lookup"><span data-stu-id="089c3-115">In C#, the correct approach is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="089c3-116">Nesse caso, o argumento para o método de <xref:System.Xml.Linq.XContainer.Elements%2A> é um objeto de <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="089c3-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="089c3-117">A abordagem correta para usar o Visual Basic é declarar e inicializar um namespace global padrão.</span><span class="sxs-lookup"><span data-stu-id="089c3-117">The correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="089c3-118">Isso coloca todas as propriedades XML no namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="089c3-118">This places all XML properties in the default namespace.</span></span>

<span data-ttu-id="089c3-119">Eis o código:</span><span class="sxs-lookup"><span data-stu-id="089c3-119">Here is the code:</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

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

<span data-ttu-id="089c3-120">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="089c3-120">This example produces the following output:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="089c3-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="089c3-121">See also</span></span>

- [<span data-ttu-id="089c3-122">Visão geral dos namespaces</span><span class="sxs-lookup"><span data-stu-id="089c3-122">Namespaces overview</span></span>](namespaces-overview.md)
