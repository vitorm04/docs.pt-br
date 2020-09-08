---
title: Como criar um documento com namespaces no Visual Basic-LINQ to XML
description: Use literais XML no Visual Basic para criar documentos que tenham namespaces ou namespaces padrão com um prefixo.
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 48e2a1abf8f7a82df3db5cb2f580804d67776b15
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552021"
---
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="2457e-103">Como criar um documento com namespaces no Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2457e-103">How to create a document with namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="2457e-104">Este artigo mostra como criar um documento com namespaces no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2457e-104">This article shows how to create a document with namespaces in Visual Basic.</span></span>

<span data-ttu-id="2457e-105">Ao usar literais XML no Visual Basic, os usuários podem definir um namespace XML global padrão.</span><span class="sxs-lookup"><span data-stu-id="2457e-105">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="2457e-106">Este namespace é o namespace padrão para literais XML e propriedades XML.</span><span class="sxs-lookup"><span data-stu-id="2457e-106">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="2457e-107">O namespace XML padrão pode ser definida no nível de projeto ou nível de arquivo.</span><span class="sxs-lookup"><span data-stu-id="2457e-107">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="2457e-108">Se ele for definido no nível do arquivo, ele substituirá o namespace padrão no nível do projeto.</span><span class="sxs-lookup"><span data-stu-id="2457e-108">If it's defined at the file level, it overrides the default namespace at the project level.</span></span>

<span data-ttu-id="2457e-109">Você também pode definir namespaces, e especifica os prefixos de namespace para esses namespaces.</span><span class="sxs-lookup"><span data-stu-id="2457e-109">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span> <span data-ttu-id="2457e-110">Você usa a `Imports` palavra-chave para definir os dois tipos de namespace.</span><span class="sxs-lookup"><span data-stu-id="2457e-110">You use the `Imports` keyword to define both types of namespace.</span></span>

<span data-ttu-id="2457e-111">Para obter mais informações, consulte [literais XML no Visual Basic](xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="2457e-111">For more information, see [XML literals in Visual Basic](xml-literals.md).</span></span>

<span data-ttu-id="2457e-112">Observe que o namespace XML padrão se aplica somente aos elementos e não a atributos.</span><span class="sxs-lookup"><span data-stu-id="2457e-112">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="2457e-113">Os atributos são, por padrão, no namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="2457e-113">Attributes are by default in the default namespace.</span></span> <span data-ttu-id="2457e-114">No entanto, você pode usar um prefixo de namespace para colocar um atributo em um namespace.</span><span class="sxs-lookup"><span data-stu-id="2457e-114">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>

## <a name="example-create-a-document-that-has-a-namespace"></a><span data-ttu-id="2457e-115">Exemplo: criar um documento que tem um namespace</span><span class="sxs-lookup"><span data-stu-id="2457e-115">Example: Create a document that has a namespace</span></span>

<span data-ttu-id="2457e-116">Este exemplo cria um documento que contém um namespace.</span><span class="sxs-lookup"><span data-stu-id="2457e-116">This example creates a document that contains a namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child aw:Att="attvalue"/>
            </aw:Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="2457e-117">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="2457e-117">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="2457e-118">Exemplo: criar um documento que tem dois namespaces, um com um prefixo</span><span class="sxs-lookup"><span data-stu-id="2457e-118">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="2457e-119">Este exemplo cria um documento que contém dois namespaces.</span><span class="sxs-lookup"><span data-stu-id="2457e-119">This example creates a document that contains two namespaces.</span></span> <span data-ttu-id="2457e-120">Um é o namespace padrão, o outro tem um prefixo.</span><span class="sxs-lookup"><span data-stu-id="2457e-120">One is the default namespace, the other has a prefix.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child Att="attvalue"/>
                <fc:Child2>child2 content</fc:Child2>
            </Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="2457e-121">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="2457e-121">This example produces the following output:</span></span>

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="2457e-122">Exemplo: criar um documento que tem dois namespaces, ambos com prefixos</span><span class="sxs-lookup"><span data-stu-id="2457e-122">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="2457e-123">O exemplo a seguir cria um documento que contém dois namespaces, ambos tendo os prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="2457e-123">The following example creates a document that contains two namespaces, both having namespace prefixes.</span></span>

<span data-ttu-id="2457e-124">Ao serializar uma árvore XML, LINQ to XML emite declarações de namespace conforme necessário para que cada elemento esteja no namespace designado.</span><span class="sxs-lookup"><span data-stu-id="2457e-124">When serializing an XML tree, LINQ to XML emits namespace declarations as required so that each element is in its designated namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="2457e-125">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="2457e-125">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="2457e-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="2457e-126">See also</span></span>

- [<span data-ttu-id="2457e-127">Visão geral dos namespaces</span><span class="sxs-lookup"><span data-stu-id="2457e-127">Namespaces overview</span></span>](namespaces-overview.md)
