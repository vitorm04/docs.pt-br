---
title: Trabalhar com namespaces globais em Visual Basic LINQ to XML
description: Você declara um namespace em Visual Basic com a instrução Imports, se o namespace é um namespace padrão ou tem um prefixo. Este artigo discute as instruções de importação e outros aspectos do trabalho com namespaces.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: f05fcab6788388e36e2b68a2d4f022ea63e74280
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552321"
---
# <a name="work-with-global-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="a0cb2-104">Trabalhar com namespaces globais no Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a0cb2-104">Work with global namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="a0cb2-105">Um dos principais recursos de literais XML no Visual Basic é a capacidade de declarar namespaces XML usando a `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-105">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="a0cb2-106">Usando esse recurso, você pode declarar um namespace XML que usa um prefixo, ou você pode declarar um namespace XML padrão.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-106">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>

<span data-ttu-id="a0cb2-107">Esse recurso é útil em duas situações:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-107">This capability is useful in two situations:</span></span>

- <span data-ttu-id="a0cb2-108">Os namespaces declarados em literais XML não são transferidos para expressões incorporadas.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-108">Namespaces declared in XML literals don't carry over into embedded expressions.</span></span> <span data-ttu-id="a0cb2-109">A declaração de namespaces globais reduz a quantidade de trabalho necessária para usar expressões inseridas com namespaces.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-109">Declaring global namespaces reduces the amount of work needed to use embedded expressions with namespaces.</span></span>
- <span data-ttu-id="a0cb2-110">Você deve declarar namespaces globais para usar namespaces com propriedades XML.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-110">You must declare global namespaces in order to use namespaces with XML properties.</span></span>

<span data-ttu-id="a0cb2-111">Você pode declarar namespaces globais no nível do projeto.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-111">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="a0cb2-112">Você também pode declarar namespaces globais em nível de módulo, que substitui namespaces globais no nível de projeto.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-112">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="a0cb2-113">Finalmente, você pode substituir namespaces globais em um literal XML.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-113">Finally, you can override global namespaces in an XML literal.</span></span>

<span data-ttu-id="a0cb2-114">Ao usar literais XML ou propriedades XML que estão em namespaces declarados globalmente, você pode ver o nome expandido de literais XML ou Propriedades passando o mouse sobre eles no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-114">When using XML literals or XML properties that are in globally declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="a0cb2-115">Você verá o nome expandido em uma dica de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-115">You will see the expanded name in a tooltip.</span></span>

<span data-ttu-id="a0cb2-116">Você pode obter um objeto de <xref:System.Xml.Linq.XNamespace> que corresponde a um namespace global usando o método `GetXmlNamespace` .</span><span class="sxs-lookup"><span data-stu-id="a0cb2-116">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>

## <a name="example-use-imports-to-declare-a-global-namespace"></a><span data-ttu-id="a0cb2-117">Exemplo: use `Imports` para declarar um namespace global</span><span class="sxs-lookup"><span data-stu-id="a0cb2-117">Example: Use `Imports` to declare a global namespace</span></span>

<span data-ttu-id="a0cb2-118">O exemplo a seguir declara um namespace global padrão com a `Imports` instrução e inicializa um <xref:System.Xml.Linq.XElement> objeto nesse namespace com um literal XML:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-118">The following example declares a default global namespace with the `Imports` statement, and then initializes an <xref:System.Xml.Linq.XElement> object in that namespace with an XML literal:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="a0cb2-119">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-119">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" />
```

## <a name="example-declare-a-global-namespace-that-has-a-prefix"></a><span data-ttu-id="a0cb2-120">Exemplo: declarar um namespace global que tem um prefixo</span><span class="sxs-lookup"><span data-stu-id="a0cb2-120">Example: Declare a global namespace that has a prefix</span></span>

<span data-ttu-id="a0cb2-121">O exemplo a seguir declara um namespace global com um prefixo e inicializa um elemento com um literal XML:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-121">The next example declares a global namespace with a prefix, and initializes an element with an XML literal:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="a0cb2-122">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-122">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" />
```

## <a name="example-declare-a-default-namespace-and-use-an-embedded-expression-for-the-child-element"></a><span data-ttu-id="a0cb2-123">Exemplo: declare um namespace padrão e use uma expressão inserida para o `Child` elemento</span><span class="sxs-lookup"><span data-stu-id="a0cb2-123">Example: Declare a default namespace and use an embedded expression for the `Child` element</span></span>

<span data-ttu-id="a0cb2-124">Os namespaces que são declarados em literais XML não são transferidos para expressões incorporadas.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-124">Namespaces that are declared in XML literals don't carry over into embedded expressions.</span></span> <span data-ttu-id="a0cb2-125">O exemplo a seguir declara um namespace padrão e, em seguida, usa uma expressão inserida para o `Child` elemento.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-125">The following example declares a default namespace, and then uses an embedded expression for the `Child` element.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child/> %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="a0cb2-126">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-126">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="" />
</Root>
```

<span data-ttu-id="a0cb2-127">O XML resultante inclui uma declaração de um namespace padrão para que o `Child` elemento esteja em nenhum namespace.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-127">The resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>

<span data-ttu-id="a0cb2-128">Você pode declarar um namespace diferente na expressão inserida da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-128">You could declare a different namespace in the embedded expression, as follows:</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child xmlns="http://www.adventure-works.com"/> %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="a0cb2-129">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-129">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="http://www.adventure-works.com" />
</Root>
```

<span data-ttu-id="a0cb2-130">No entanto, com o namespace global padrão, você pode usar literais XML sem declarar namespaces.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-130">However, with the global default namespace you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="a0cb2-131">O XML resultante estará no namespace padrão declarado globalmente, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-131">The resulting XML will be in the globally-declared default namespace, as in this example:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root>
                                   <%= <Child/> %>
                               </Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="a0cb2-132">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-132">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child />
</Root>
```

## <a name="example-use-namespaces-with-xml-properties"></a><span data-ttu-id="a0cb2-133">Exemplo: usar namespaces com propriedades XML</span><span class="sxs-lookup"><span data-stu-id="a0cb2-133">Example: Use namespaces with XML properties</span></span>

<span data-ttu-id="a0cb2-134">Se você estiver trabalhando com uma árvore XML que está em um namespace e usar as propriedades XML, deverá usar um namespace global para que as propriedades XML também estejam no namespace correto.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-134">If you're working with an XML tree that's in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="a0cb2-135">O exemplo a seguir declara uma árvore XML em um namespace e, em seguida, imprime a contagem de `Child` elementos.</span><span class="sxs-lookup"><span data-stu-id="a0cb2-135">The following example declares an XML tree in a namespace, and then prints the count of `Child` elements.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <Child>content</Child>
    </Root>
Console.WriteLine(root.<Child>.Count())
```

<span data-ttu-id="a0cb2-136">Este exemplo indica que não há nenhum elemento de `Child` .</span><span class="sxs-lookup"><span data-stu-id="a0cb2-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="a0cb2-137">Ele produz esta saída:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-137">It produces this output:</span></span>

```output
0
```

<span data-ttu-id="a0cb2-138">Se, no entanto, você declarar um namespace global padrão, então a literal XML e a propriedade XML estão no namespace global padrão:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>content</Child>
            </Root>
        Console.WriteLine(root.<Child>.Count())
    End Sub
End Module
```

<span data-ttu-id="a0cb2-139">Este exemplo indica que há um elemento de `Child` .</span><span class="sxs-lookup"><span data-stu-id="a0cb2-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="a0cb2-140">Ele produz esta saída:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-140">It produces this output:</span></span>

```output
1
```

<span data-ttu-id="a0cb2-141">Se você declarar um namespace global que tenha um prefixo, você pode usar o prefixo para literais XML e propriedades XML:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>content</aw:Child>
            </aw:Root>
        Console.WriteLine(root.<aw:Child>.Count())
    End Sub
End Module
```

## <a name="example-use-getxmlnamespace-to-get-an-xnamespace"></a><span data-ttu-id="a0cb2-142">Exemplo: use `GetXmlNamespace` para obter um `XNamespace`</span><span class="sxs-lookup"><span data-stu-id="a0cb2-142">Example: Use `GetXmlNamespace` to get an `XNamespace`</span></span>

<span data-ttu-id="a0cb2-143">Você pode obter um <xref:System.Xml.Linq.XNamespace> objeto usando o `GetXmlNamespace` método:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-143">You can obtain an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Dim xn As XNamespace = GetXmlNamespace(aw)
        Console.WriteLine(xn)
    End Sub
End Module
```

<span data-ttu-id="a0cb2-144">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a0cb2-144">This example produces the following output:</span></span>

```output
http://www.adventure-works.com
```

## <a name="see-also"></a><span data-ttu-id="a0cb2-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="a0cb2-145">See also</span></span>

- [<span data-ttu-id="a0cb2-146">Visão geral dos namespaces</span><span class="sxs-lookup"><span data-stu-id="a0cb2-146">Namespaces overview</span></span>](namespaces-overview.md)
