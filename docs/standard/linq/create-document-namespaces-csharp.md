---
title: Como criar um documento com namespaces em C#-LINQ to XML
description: Use o objeto XNamespace em C# para criar documentos que têm namespaces ou namespaces padrão com um prefixo.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 3ec9624bcc599a73a6872e5c4c79504a1a4b4380
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552024"
---
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a><span data-ttu-id="8de31-103">Como criar um documento com namespaces em C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8de31-103">How to create a document with namespaces in C# (LINQ to XML)</span></span>

<span data-ttu-id="8de31-104">Este artigo mostra como criar documentos em C# que têm namespaces.</span><span class="sxs-lookup"><span data-stu-id="8de31-104">This article shows how to create documents in C# that have namespaces.</span></span>

## <a name="example-declare-and-initialize-a-default-namespace"></a><span data-ttu-id="8de31-105">Exemplo: declarar e inicializar um namespace padrão</span><span class="sxs-lookup"><span data-stu-id="8de31-105">Example: Declare and initialize a default namespace</span></span>

<span data-ttu-id="8de31-106">Para criar um elemento ou um atributo que esteja em um namespace, primeiro declare e inicialize um <xref:System.Xml.Linq.XNamespace> objeto.</span><span class="sxs-lookup"><span data-stu-id="8de31-106">To create an element or an attribute that's in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="8de31-107">Em seguida, você usa a sobrecarga do operador de adição para combinar o namespace com o nome local, expresso como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8de31-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>

<span data-ttu-id="8de31-108">O exemplo a seguir cria um documento com um namespace.</span><span class="sxs-lookup"><span data-stu-id="8de31-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="8de31-109">Por padrão, o LINQ to XML serializa esse documento com um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="8de31-109">By default, LINQ to XML serializes this document with a default namespace.</span></span>

```csharp
// Create an XML tree in a namespace.
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="8de31-110">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="8de31-110">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child>child content</Child>
</Root>
```

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a><span data-ttu-id="8de31-111">Exemplo: criar um documento que tem um namespace e um atributo</span><span class="sxs-lookup"><span data-stu-id="8de31-111">Example: Create a document that has a namespace and an attribute</span></span>

<span data-ttu-id="8de31-112">O exemplo a seguir cria um documento com um namespace.</span><span class="sxs-lookup"><span data-stu-id="8de31-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="8de31-113">Também cria um atributo que declara o namespace com um prefixo de namespace.</span><span class="sxs-lookup"><span data-stu-id="8de31-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="8de31-114">Para criar um atributo que declare um namespace com um prefixo, você cria um atributo onde o namespace do nome do atributo seja o prefixo do namespace, e esse nome esteja no namespace <xref:System.Xml.Linq.XNamespace.Xmlns%2A>.</span><span class="sxs-lookup"><span data-stu-id="8de31-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="8de31-115">O valor desse atributo é o URI do namespace.</span><span class="sxs-lookup"><span data-stu-id="8de31-115">The value of this attribute is the URI of the namespace.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="8de31-116">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="8de31-116">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="8de31-117">Exemplo: criar um documento que tem dois namespaces, um com um prefixo</span><span class="sxs-lookup"><span data-stu-id="8de31-117">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="8de31-118">O exemplo a seguir mostra a criação de um documento que contém dois namespaces.</span><span class="sxs-lookup"><span data-stu-id="8de31-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="8de31-119">Um é o namespace padrão, o outro é um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="8de31-119">One is the default namespace, the other is a namespace with a prefix.</span></span>

<span data-ttu-id="8de31-120">Ao incluir atributos de namespace no elemento raiz, os namespaces são serializados para que `http://www.adventure-works.com` seja o namespace padrão e `www.fourthcoffee.com` é serializado com um prefixo de `fc` .</span><span class="sxs-lookup"><span data-stu-id="8de31-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of `fc`.</span></span> <span data-ttu-id="8de31-121">Para criar um atributo que declara um namespace padrão, você cria um atributo com o nome `xmlns` , sem um namespace.</span><span class="sxs-lookup"><span data-stu-id="8de31-121">To create an attribute that declares a default namespace, you create an attribute with the name `xmlns`, without a namespace.</span></span> <span data-ttu-id="8de31-122">O valor do atributo é o URI padrão do namespace.</span><span class="sxs-lookup"><span data-stu-id="8de31-122">The value of the attribute is the default namespace URI.</span></span>

```csharp
// The http://www.adventure-works.com namespace is forced to be the default namespace.
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute("xmlns", "http://www.adventure-works.com"),
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

<span data-ttu-id="8de31-123">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="8de31-123">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <DifferentChild>other content</DifferentChild>
  </fc:Child>
  <Child2>c2 content</Child2>
  <fc:Child3>c3 content</fc:Child3>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="8de31-124">Exemplo: criar um documento que tem dois namespaces, ambos com prefixos</span><span class="sxs-lookup"><span data-stu-id="8de31-124">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="8de31-125">O exemplo a seguir cria um documento que contém dois namespaces, ambos com prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="8de31-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

<span data-ttu-id="8de31-126">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="8de31-126">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="example-create-a-namespace-using-expanded-names"></a><span data-ttu-id="8de31-127">Exemplo: criar um namespace usando nomes expandidos</span><span class="sxs-lookup"><span data-stu-id="8de31-127">Example: Create a namespace using expanded names</span></span>

<span data-ttu-id="8de31-128">Outra maneira de obter o mesmo resultado é usar nomes expandidos, em vez de declarar e criar um objeto <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="8de31-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>

<span data-ttu-id="8de31-129">Essa abordagem tem implicações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="8de31-129">This approach has performance implications.</span></span> <span data-ttu-id="8de31-130">Cada vez que você passa uma cadeia de caracteres que contém um nome expandido para LINQ to XML, LINQ to XML deve analisar o nome, localizar o namespace estendido e encontrar o nome atomado.</span><span class="sxs-lookup"><span data-stu-id="8de31-130">Each time you pass a string that contains an expanded name to LINQ to XML, LINQ to XML must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="8de31-131">Esse processo utiliza tempo de CPU.</span><span class="sxs-lookup"><span data-stu-id="8de31-131">This process takes CPU time.</span></span> <span data-ttu-id="8de31-132">Se o desempenho for importante, convém declarar e usar um objeto <xref:System.Xml.Linq.XNamespace> explicitamente.</span><span class="sxs-lookup"><span data-stu-id="8de31-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>

<span data-ttu-id="8de31-133">Se o desempenho for um problema importante, consulte [pré-atomização de objetos XName](pre-atomization-xname-objects.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="8de31-133">If performance is an important issue, see [Pre-Atomization of XName Objects](pre-atomization-xname-objects.md) for more information.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XElement root = new XElement("{http://www.adventure-works.com}Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement("{http://www.adventure-works.com}Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="8de31-134">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="8de31-134">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="8de31-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="8de31-135">See also</span></span>

- [<span data-ttu-id="8de31-136">Visão geral dos namespaces</span><span class="sxs-lookup"><span data-stu-id="8de31-136">Namespaces overview</span></span>](namespaces-overview.md)
