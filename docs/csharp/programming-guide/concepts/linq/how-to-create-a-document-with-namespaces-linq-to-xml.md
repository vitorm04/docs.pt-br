---
title: Como criar um documento com namespaces (C#) (LINQ to XML)
description: Saiba como criar um documento com um namespace em LINQ to XML em C# usando um objeto XNamespace para combinar o namespace com o nome local.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 6472baefc73285af1c6dca0bfe7d874003940fc4
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103395"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="e88aa-103">Como criar um documento com namespaces (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e88aa-103">How to create a document with namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="e88aa-104">Este tópico mostra como criar documentos com namespaces.</span><span class="sxs-lookup"><span data-stu-id="e88aa-104">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e88aa-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e88aa-105">Example</span></span>  
 <span data-ttu-id="e88aa-106">Para criar um elemento ou um atributo que esteja em um namespace, você primeiro declara e inicializa um objeto <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="e88aa-106">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="e88aa-107">Em seguida, você usa a sobrecarga do operador de adição para combinar o namespace com o nome local, expresso como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e88aa-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="e88aa-108">O exemplo a seguir cria um documento com um namespace.</span><span class="sxs-lookup"><span data-stu-id="e88aa-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="e88aa-109">Por padrão, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializa esse documento com um namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="e88aa-109">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="e88aa-110">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e88aa-110">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e88aa-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e88aa-111">Example</span></span>  
 <span data-ttu-id="e88aa-112">O exemplo a seguir cria um documento com um namespace.</span><span class="sxs-lookup"><span data-stu-id="e88aa-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="e88aa-113">Também cria um atributo que declara o namespace com um prefixo de namespace.</span><span class="sxs-lookup"><span data-stu-id="e88aa-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="e88aa-114">Para criar um atributo que declare um namespace com um prefixo, você cria um atributo onde o namespace do nome do atributo seja o prefixo do namespace, e esse nome esteja no namespace <xref:System.Xml.Linq.XNamespace.Xmlns%2A>.</span><span class="sxs-lookup"><span data-stu-id="e88aa-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="e88aa-115">O valor desse atributo é o URI do namespace.</span><span class="sxs-lookup"><span data-stu-id="e88aa-115">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="e88aa-116">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e88aa-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e88aa-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e88aa-117">Example</span></span>  
 <span data-ttu-id="e88aa-118">O exemplo a seguir mostra a criação de um documento que contém dois namespaces.</span><span class="sxs-lookup"><span data-stu-id="e88aa-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="e88aa-119">Um é o namespace padrão.</span><span class="sxs-lookup"><span data-stu-id="e88aa-119">One is the default namespace.</span></span> <span data-ttu-id="e88aa-120">O outro é um namespace com um prefixo.</span><span class="sxs-lookup"><span data-stu-id="e88aa-120">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="e88aa-121">Com a inclusão de atributos de namespace no elemento raiz, os namespaces são serializados, de modo que `http://www.adventure-works.com` seja o namespace padrão e `www.fourthcoffee.com` seja serializado com o prefixo "fc".</span><span class="sxs-lookup"><span data-stu-id="e88aa-121">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="e88aa-122">Para criar um atributo que declare um namespace padrão, você cria um atributo com o nome "xmlns", sem um namespace.</span><span class="sxs-lookup"><span data-stu-id="e88aa-122">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="e88aa-123">O valor do atributo é o URI padrão do namespace.</span><span class="sxs-lookup"><span data-stu-id="e88aa-123">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="e88aa-124">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e88aa-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e88aa-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e88aa-125">Example</span></span>  
 <span data-ttu-id="e88aa-126">O exemplo a seguir cria um documento que contém dois namespaces, ambos com prefixos de namespace.</span><span class="sxs-lookup"><span data-stu-id="e88aa-126">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="e88aa-127">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e88aa-127">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e88aa-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e88aa-128">Example</span></span>  
 <span data-ttu-id="e88aa-129">Outra maneira de obter o mesmo resultado é usar nomes expandidos, em vez de declarar e criar um objeto <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="e88aa-129">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="e88aa-130">Essa abordagem tem implicações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="e88aa-130">This approach has performance implications.</span></span> <span data-ttu-id="e88aa-131">Cada vez que você passa uma cadeia de caracteres que contém um nome expandido para o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] deve analisar o nome, localizar o namespace atomizado e localizar o nome atomizado.</span><span class="sxs-lookup"><span data-stu-id="e88aa-131">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="e88aa-132">Esse processo utiliza tempo de CPU.</span><span class="sxs-lookup"><span data-stu-id="e88aa-132">This process takes CPU time.</span></span> <span data-ttu-id="e88aa-133">Se o desempenho for importante, convém declarar e usar um objeto <xref:System.Xml.Linq.XNamespace> explicitamente.</span><span class="sxs-lookup"><span data-stu-id="e88aa-133">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="e88aa-134">Se o desempenho for uma questão importante, consulte [Pré-atomização de objetos XName (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="e88aa-134">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="e88aa-135">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e88aa-135">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e88aa-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="e88aa-136">See also</span></span>

- [<span data-ttu-id="e88aa-137">Visão geral sobre namespaces (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e88aa-137">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
