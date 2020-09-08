---
title: Construção funcional-LINQ to XML
description: LINQ to XML fornece construção funcional, que permite que você crie uma árvore XML em uma única instrução.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: bcdc153d7f60cfb165dcb741d62b6af5c07a148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551911"
---
# <a name="functional-construction-linq-to-xml"></a><span data-ttu-id="1666e-103">Construção funcional (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1666e-103">Functional construction (LINQ to XML)</span></span>

<span data-ttu-id="1666e-104">O LINQ to XML fornece uma maneira eficiente de criar elementos XML chamados *construção funcional*.</span><span class="sxs-lookup"><span data-stu-id="1666e-104">LINQ to XML provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="1666e-105">A construção funcional permite que você crie uma árvore XML em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="1666e-105">Functional construction enables you to create an XML tree in a single statement.</span></span>

<span data-ttu-id="1666e-106">Vários recursos principais da interface de programação de LINQ to XML são usados na construção funcional:</span><span class="sxs-lookup"><span data-stu-id="1666e-106">Several key features of the LINQ to XML programming interface are used in functional construction:</span></span>

- <span data-ttu-id="1666e-107">O construtor <xref:System.Xml.Linq.XElement> utiliza vários tipos de argumentos para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1666e-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="1666e-108">Por exemplo, você pode passar outro objeto <xref:System.Xml.Linq.XElement>, que se torna um elemento filho.</span><span class="sxs-lookup"><span data-stu-id="1666e-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="1666e-109">Você pode passar um objeto <xref:System.Xml.Linq.XAttribute>, que se torna um atributo do elemento.</span><span class="sxs-lookup"><span data-stu-id="1666e-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="1666e-110">Ou você pode passar qualquer outro tipo de objeto, que é convertido em uma cadeia de caracteres e torna-se o conteúdo de texto do elemento.</span><span class="sxs-lookup"><span data-stu-id="1666e-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>
- <span data-ttu-id="1666e-111">O construtor <xref:System.Xml.Linq.XElement> utiliza uma matriz de `params` do tipo <xref:System.Object>, para que você possa passar qualquer número de objetos para o construtor.</span><span class="sxs-lookup"><span data-stu-id="1666e-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="1666e-112">Isso permite que você crie um elemento que tem o conteúdo complexo.</span><span class="sxs-lookup"><span data-stu-id="1666e-112">This enables you to create an element that has complex content.</span></span>
- <span data-ttu-id="1666e-113">Se um objeto implementar <xref:System.Collections.Generic.IEnumerable%601>, a coleção no objeto será enumerada, e todos os itens da coleção serão adicionados.</span><span class="sxs-lookup"><span data-stu-id="1666e-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="1666e-114">Se a coleção contiver objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, cada item da coleção será adicionado separadamente.</span><span class="sxs-lookup"><span data-stu-id="1666e-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="1666e-115">Isso é importante porque permite que você passe os resultados de uma consulta LINQ para o construtor.</span><span class="sxs-lookup"><span data-stu-id="1666e-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>

## <a name="example-create-an-xml-tree"></a><span data-ttu-id="1666e-116">Exemplo: criar uma árvore XML</span><span class="sxs-lookup"><span data-stu-id="1666e-116">Example: Create an XML tree</span></span>

<span data-ttu-id="1666e-117">Você pode usar a construção funcional para escrever código para criar uma árvore XML.</span><span class="sxs-lookup"><span data-stu-id="1666e-117">You can use functional construction to write code to create an XML tree.</span></span> <span data-ttu-id="1666e-118">A seguir, é mostrado um exemplo:</span><span class="sxs-lookup"><span data-stu-id="1666e-118">The following is an example:</span></span>

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

## <a name="example-create-an-xml-tree-using-linq-query-results"></a><span data-ttu-id="1666e-119">Exemplo: criar uma árvore XML usando os resultados da consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="1666e-119">Example: Create an XML tree using LINQ query results</span></span>

<span data-ttu-id="1666e-120">Esses recursos também permitem que você escreva código que usa os resultados de consultas LINQ ao criar uma árvore XML, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1666e-120">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

<span data-ttu-id="1666e-121">Em Visual Basic, a mesma coisa é realizada com literais XML:</span><span class="sxs-lookup"><span data-stu-id="1666e-121">In Visual Basic, the same thing is accomplished with XML literals:</span></span>

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where CInt(el) > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="1666e-122">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="1666e-122">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="1666e-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="1666e-123">See also</span></span>

- [<span data-ttu-id="1666e-124">Criar árvores XML em C #</span><span class="sxs-lookup"><span data-stu-id="1666e-124">Create XML Trees in C#</span></span>](create-xml-trees.md)
- [<span data-ttu-id="1666e-125">Literais XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1666e-125">XML literals in Visual Basic</span></span>](xml-literals.md)
