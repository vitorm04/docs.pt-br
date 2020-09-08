---
title: Criar árvores XML em C#-LINQ to XML
description: Você pode criar uma árvore XML em C# usando os construtores LINQ to XML XElement e XAttribute, e pode fazer com que o código se assemelhe à estrutura do XML subjacente.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 97bf40d84f40eabf6fa84f10bf4febb7697b10f5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552300"
---
# <a name="create-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="12f64-103">Criar árvores XML em C# (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="12f64-103">Create XML trees in C# (LINQ to XML)</span></span>

<span data-ttu-id="12f64-104">Este artigo fornece informações sobre a criação de árvores XML em C#.</span><span class="sxs-lookup"><span data-stu-id="12f64-104">This article provides information about creating XML trees in C#.</span></span>

<span data-ttu-id="12f64-105">Para obter informações sobre como usar os resultados de consultas LINQ como o conteúdo de um <xref:System.Xml.Linq.XElement> , consulte [construção funcional](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="12f64-105">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional construction](functional-construction.md).</span></span>

## <a name="construct-elements"></a><span data-ttu-id="12f64-106">Elementos de construção</span><span class="sxs-lookup"><span data-stu-id="12f64-106">Construct elements</span></span>

<span data-ttu-id="12f64-107">As assinaturas dos construtores <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute> permitem que você passe o conteúdo do elemento ou atributo como argumentos para o construtor.</span><span class="sxs-lookup"><span data-stu-id="12f64-107">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="12f64-108">Como um dos construtores recebe um número variável de argumentos, você pode passar qualquer número de elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="12f64-108">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="12f64-109">Naturalmente, cada um desses elementos filhos pode conter seus próprios elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="12f64-109">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="12f64-110">Para qualquer elemento, você pode adicionar a quantidade desejada de atributos.</span><span class="sxs-lookup"><span data-stu-id="12f64-110">For any element, you can add any number of attributes.</span></span>

<span data-ttu-id="12f64-111">Ao adicionar objetos <xref:System.Xml.Linq.XNode> (inclusive <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver um pai, os objetos serão simplesmente anexados à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="12f64-111">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="12f64-112">Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="12f64-112">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="12f64-113">O último exemplo neste artigo demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="12f64-113">The last example in this article demonstrates this.</span></span>

<span data-ttu-id="12f64-114">Para criar um `contacts` <xref:System.Xml.Linq.XElement> , você pode usar o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="12f64-114">To create a `contacts` <xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

<span data-ttu-id="12f64-115">Se recuado corretamente, o código para criar objetos <xref:System.Xml.Linq.XElement> é muito parecido com a estrutura do XML subjacente.</span><span class="sxs-lookup"><span data-stu-id="12f64-115">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>

## <a name="xelement-constructors"></a><span data-ttu-id="12f64-116">Construtores de XElement</span><span class="sxs-lookup"><span data-stu-id="12f64-116">XElement constructors</span></span>

<span data-ttu-id="12f64-117">A classe <xref:System.Xml.Linq.XElement> usa os seguintes construtores na construção funcional.</span><span class="sxs-lookup"><span data-stu-id="12f64-117">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="12f64-118">Observe que há alguns outros construtores para o <xref:System.Xml.Linq.XElement> , mas como eles não são usados para a construção funcional, eles não estão listados aqui.</span><span class="sxs-lookup"><span data-stu-id="12f64-118">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they're not used for functional construction they're not listed here.</span></span>

|<span data-ttu-id="12f64-119">Construtor</span><span class="sxs-lookup"><span data-stu-id="12f64-119">Constructor</span></span>|<span data-ttu-id="12f64-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="12f64-120">Description</span></span>|
|-----------------|-----------------|
|`XElement(XName name, object content)`|<span data-ttu-id="12f64-121">Cria um <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="12f64-121">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="12f64-122">O parâmetro `name` especifica o nome do elemento; `content` especifica o conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="12f64-122">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|
|`XElement(XName name)`|<span data-ttu-id="12f64-123">Cria um <xref:System.Xml.Linq.XElement> com seu <xref:System.Xml.Linq.XName> inicializado para o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="12f64-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|
|`XElement(XName name, params object[] content)`|<span data-ttu-id="12f64-124">Cria um <xref:System.Xml.Linq.XElement> com seu <xref:System.Xml.Linq.XName> inicializado para o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="12f64-124">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="12f64-125">Os atributos e/ou elementos filhos são criados a partir do conteúdo da lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="12f64-125">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|

<span data-ttu-id="12f64-126">O parâmetro `content` é muito flexível.</span><span class="sxs-lookup"><span data-stu-id="12f64-126">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="12f64-127">Ele dá suporte a qualquer tipo de objeto que seja um filho válido de um <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="12f64-127">It supports any type of object that's a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="12f64-128">As seguintes regras se aplicam aos diferentes tipos de objetos passados neste parâmetro:</span><span class="sxs-lookup"><span data-stu-id="12f64-128">The following rules apply to different types of objects passed in this parameter:</span></span>

- <span data-ttu-id="12f64-129">Uma cadeia de caracteres é adicionada como conteúdo de texto.</span><span class="sxs-lookup"><span data-stu-id="12f64-129">A string is added as text content.</span></span>
- <span data-ttu-id="12f64-130">Um <xref:System.Xml.Linq.XElement> é adicionado como um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="12f64-130">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>
- <span data-ttu-id="12f64-131">Um <xref:System.Xml.Linq.XAttribute> é adicionado como um atributo.</span><span class="sxs-lookup"><span data-stu-id="12f64-131">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>
- <span data-ttu-id="12f64-132">Um <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> ou <xref:System.Xml.Linq.XText> é adicionado como conteúdo filho.</span><span class="sxs-lookup"><span data-stu-id="12f64-132">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>
- <span data-ttu-id="12f64-133">Um <xref:System.Collections.IEnumerable> é enumerado, e essas regras são aplicadas recursivamente aos resultados.</span><span class="sxs-lookup"><span data-stu-id="12f64-133">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>
- <span data-ttu-id="12f64-134">Para qualquer outro tipo, seu método `ToString` é chamado e o resultado é adicionado como conteúdo de texto.</span><span class="sxs-lookup"><span data-stu-id="12f64-134">For any other type, its `ToString` method is called and the result is added as text content.</span></span>

## <a name="example-create-an-xelement-with-content"></a><span data-ttu-id="12f64-135">Exemplo: criar um XElement com conteúdo</span><span class="sxs-lookup"><span data-stu-id="12f64-135">Example: Create an XElement with content</span></span>

<span data-ttu-id="12f64-136">Você pode criar um <xref:System.Xml.Linq.XElement> contendo o conteúdo simples com uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="12f64-136">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="12f64-137">Para fazer isso, especifique o conteúdo como o segundo parâmetro, como segue:</span><span class="sxs-lookup"><span data-stu-id="12f64-137">To do this, specify the content as the second parameter, as follows:</span></span>

```csharp
XElement n = new XElement("Customer", "Adventure Works");
Console.WriteLine(n);
```

<span data-ttu-id="12f64-138">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12f64-138">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

<span data-ttu-id="12f64-139">Você pode passar qualquer tipo de objeto como o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="12f64-139">You can pass any type of object as the content.</span></span> <span data-ttu-id="12f64-140">Por exemplo, o seguinte código cria um elemento que contém um número de ponto flutuante como conteúdo:</span><span class="sxs-lookup"><span data-stu-id="12f64-140">For example, the following code creates an element that contains a floating point number as content:</span></span>

```csharp
XElement n = new XElement("Cost", 324.50);
Console.WriteLine(n);
```

<span data-ttu-id="12f64-141">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12f64-141">This example produces the following output:</span></span>

```xml
<Cost>324.5</Cost>
```

<span data-ttu-id="12f64-142">O número de ponto flutuante foi convertido e passado para o construtor.</span><span class="sxs-lookup"><span data-stu-id="12f64-142">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="12f64-143">O número é convertido em uma cadeia de caracteres e usado como o conteúdo do elemento.</span><span class="sxs-lookup"><span data-stu-id="12f64-143">The boxed number is converted to a string and used as the content of the element.</span></span>

## <a name="example-create-an-xelement-with-a-child-element"></a><span data-ttu-id="12f64-144">Exemplo: criar um XElement com um elemento filho</span><span class="sxs-lookup"><span data-stu-id="12f64-144">Example: Create an XElement with a child element</span></span>

<span data-ttu-id="12f64-145">Se você passar uma instância da classe <xref:System.Xml.Linq.XElement> para o argumento de conteúdo, o construtor criará um elemento com um elemento filho:</span><span class="sxs-lookup"><span data-stu-id="12f64-145">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>

```csharp
XElement shippingUnit = new XElement("ShippingUnit",
    new XElement("Cost", 324.50)
);
Console.WriteLine(shippingUnit);
```

<span data-ttu-id="12f64-146">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12f64-146">This example produces the following output:</span></span>

```xml
<ShippingUnit>
  <Cost>324.5</Cost>
</ShippingUnit>
```

## <a name="example-create-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="12f64-147">Exemplo: criar um XElement com vários elementos filho</span><span class="sxs-lookup"><span data-stu-id="12f64-147">Example: Create an XElement with multiple child elements</span></span>

<span data-ttu-id="12f64-148">Você pode passar um número de objetos <xref:System.Xml.Linq.XElement> para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="12f64-148">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="12f64-149">Cada um dos objetos <xref:System.Xml.Linq.XElement> é incluído como um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="12f64-149">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>

```csharp
XElement address = new XElement("Address",
    new XElement("Street1", "123 Main St"),
    new XElement("City", "Mercer Island"),
    new XElement("State", "WA"),
    new XElement("Postal", "68042")
);
Console.WriteLine(address);
```

<span data-ttu-id="12f64-150">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12f64-150">This example produces the following output:</span></span>

```xml
<Address>
  <Street1>123 Main St</Street1>
  <City>Mercer Island</City>
  <State>WA</State>
  <Postal>68042</Postal>
</Address>
```

<span data-ttu-id="12f64-151">Ao estender o exemplo anterior, você pode criar uma árvore XML inteira, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="12f64-151">By extending the previous example, you can create an entire XML tree, as follows:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
Console.WriteLine(contacts);
```

<span data-ttu-id="12f64-152">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12f64-152">This example produces the following output:</span></span>

```xml
<Contacts>
  <Contact>
    <Name>Patrick Hines</Name>
    <Phone>206-555-0144</Phone>
    <Address>
      <Street1>123 Main St</Street1>
      <City>Mercer Island</City>
      <State>WA</State>
      <Postal>68042</Postal>
    </Address>
  </Contact>
</Contacts>
```

## <a name="example-create-an-xelement-with-an-xattribute"></a><span data-ttu-id="12f64-153">Exemplo: criar um XElement com um XAttribute</span><span class="sxs-lookup"><span data-stu-id="12f64-153">Example: Create an XElement with an XAttribute</span></span>

<span data-ttu-id="12f64-154">Se você passar uma instância da classe <xref:System.Xml.Linq.XAttribute> para o argumento de conteúdo, o construtor criará um elemento com um atributo:</span><span class="sxs-lookup"><span data-stu-id="12f64-154">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

<span data-ttu-id="12f64-155">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12f64-155">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-create-an-empty-element"></a><span data-ttu-id="12f64-156">Exemplo: criar um elemento vazio</span><span class="sxs-lookup"><span data-stu-id="12f64-156">Example: Create an empty element</span></span>

<span data-ttu-id="12f64-157">Para criar um vazio <xref:System.Xml.Linq.XElement> , não transmita nenhum conteúdo para o construtor.</span><span class="sxs-lookup"><span data-stu-id="12f64-157">To create an empty <xref:System.Xml.Linq.XElement>, don't pass any content to the constructor.</span></span> <span data-ttu-id="12f64-158">O seguinte exemplo cria um elemento vazio:</span><span class="sxs-lookup"><span data-stu-id="12f64-158">The following example creates an empty element:</span></span>

```csharp
XElement n = new XElement("Customer");
Console.WriteLine(n);
```

<span data-ttu-id="12f64-159">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="12f64-159">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="example-attach-vs-clone"></a><span data-ttu-id="12f64-160">Exemplo: Attach vs. Clone</span><span class="sxs-lookup"><span data-stu-id="12f64-160">Example: Attach vs. clone</span></span>

<span data-ttu-id="12f64-161">Conforme citado anteriormente, ao adicionar objetos <xref:System.Xml.Linq.XNode> (inclusive <xref:System.Xml.Linq.XElement>) ou <xref:System.Xml.Linq.XAttribute>, se o novo conteúdo não tiver um pai, os objetos serão simplesmente anexados à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="12f64-161">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="12f64-162">Se o novo conteúdo já tiver um pai e fizer parte de outra árvore XML, o novo conteúdo será clonado, e o conteúdo recém-clonado será anexado à árvore XML.</span><span class="sxs-lookup"><span data-stu-id="12f64-162">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>

<span data-ttu-id="12f64-163">O exemplo a seguir demonstra o comportamento quando você adiciona um elemento pai a uma árvore e quando você adiciona um elemento sem pai a uma árvore:</span><span class="sxs-lookup"><span data-stu-id="12f64-163">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree:</span></span>

```csharp
// Create a tree with a child element.
XElement xmlTree1 = new XElement("Root",
    new XElement("Child1", 1)
);

// Create an element that's not parented.
XElement child2 = new XElement("Child2", 2);

// Create a tree and add Child1 and Child2 to it.
XElement xmlTree2 = new XElement("Root",
    xmlTree1.Element("Child1"),
    child2
);

// Compare Child1 identity.
Console.WriteLine("Child1 was {0}",
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?
    "attached" : "cloned");

// Compare Child2 identity.
Console.WriteLine("Child2 was {0}",
    child2 == xmlTree2.Element("Child2") ?
    "attached" : "cloned");

// This example produces the following output:
//    Child1 was cloned
//    Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="12f64-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="12f64-164">See also</span></span>

- [<span data-ttu-id="12f64-165">Construção funcional</span><span class="sxs-lookup"><span data-stu-id="12f64-165">Functional construction</span></span>](functional-construction.md)
