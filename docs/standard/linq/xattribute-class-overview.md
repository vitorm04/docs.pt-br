---
title: Visão geral da classe XAttribute
description: A classe XAttribute representa atributos XML. Trabalhar com atributos em LINQ to XML é semelhante a trabalhar com elementos.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551860"
---
# <a name="xattribute-class-overview"></a><span data-ttu-id="fadc6-104">Visão geral da classe XAttribute</span><span class="sxs-lookup"><span data-stu-id="fadc6-104">XAttribute class overview</span></span>

<span data-ttu-id="fadc6-105">Os atributos são pares de nome-valor associados a um elemento.</span><span class="sxs-lookup"><span data-stu-id="fadc6-105">Attributes are name-value pairs that are associated with an element.</span></span> <span data-ttu-id="fadc6-106">A classe de <xref:System.Xml.Linq.XAttribute> representa atributos XML.</span><span class="sxs-lookup"><span data-stu-id="fadc6-106">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>

<span data-ttu-id="fadc6-107">Trabalhar com atributos em LINQ to XML é semelhante a trabalhar com elementos.</span><span class="sxs-lookup"><span data-stu-id="fadc6-107">Working with attributes in LINQ to XML is similar to working with elements.</span></span> <span data-ttu-id="fadc6-108">Os construtores são semelhantes.</span><span class="sxs-lookup"><span data-stu-id="fadc6-108">Their constructors are similar.</span></span> <span data-ttu-id="fadc6-109">Os métodos que você usa para recuperar coleções deless são semelhantes.</span><span class="sxs-lookup"><span data-stu-id="fadc6-109">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="fadc6-110">Uma expressão de consulta LINQ para uma coleção de atributos é semelhante a uma expressão de consulta LINQ para uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="fadc6-110">A LINQ query expression for a collection of attributes looks similar to a LINQ query expression for a collection of elements.</span></span>

<span data-ttu-id="fadc6-111">A ordem em que os atributos foram adicionados a um elemento é preservada.</span><span class="sxs-lookup"><span data-stu-id="fadc6-111">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="fadc6-112">Isto é, quando você itera através de atributos, você ver na mesma ordem que foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="fadc6-112">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>

## <a name="the-xattribute-constructor"></a><span data-ttu-id="fadc6-113">O Construtor XAttribute</span><span class="sxs-lookup"><span data-stu-id="fadc6-113">The XAttribute constructor</span></span>

<span data-ttu-id="fadc6-114">O seguinte construtor da <xref:System.Xml.Linq.XAttribute> classe é aquele que você usará com mais frequência:</span><span class="sxs-lookup"><span data-stu-id="fadc6-114">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you'll most commonly use:</span></span>

|<span data-ttu-id="fadc6-115">Construtor</span><span class="sxs-lookup"><span data-stu-id="fadc6-115">Constructor</span></span>|<span data-ttu-id="fadc6-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fadc6-116">Description</span></span>|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|<span data-ttu-id="fadc6-117">Cria um objeto de <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="fadc6-117">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="fadc6-118">O argumento de `name` especifica o nome do atributo; `content` especifica o conteúdo de atributo.</span><span class="sxs-lookup"><span data-stu-id="fadc6-118">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|

## <a name="example-create-an-element-with-an-attribute"></a><span data-ttu-id="fadc6-119">Exemplo: criar um elemento com um atributo</span><span class="sxs-lookup"><span data-stu-id="fadc6-119">Example: Create an element with an attribute</span></span>

<span data-ttu-id="fadc6-120">O exemplo a seguir mostra a tarefa comum de criar um elemento que contém um atributo.</span><span class="sxs-lookup"><span data-stu-id="fadc6-120">The following example shows the common task of creating an element that contains an attribute.</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

<span data-ttu-id="fadc6-121">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="fadc6-121">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a><span data-ttu-id="fadc6-122">Exemplo: construção funcional de atributos</span><span class="sxs-lookup"><span data-stu-id="fadc6-122">Example: Functional construction of attributes</span></span>

<span data-ttu-id="fadc6-123">Você pode construir <xref:System.Xml.Linq.XAttribute> objetos em linha com a construção de <xref:System.Xml.Linq.XElement> objetos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="fadc6-123">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as shown in the following example:</span></span>

```csharp
XElement c = new XElement("Customers",
    new XElement("Customer",
        new XElement("Name", "John Doe"),
        new XElement("PhoneNumbers",
            new XElement("Phone",
                new XAttribute("type", "home"),
                "555-555-5555"),
            new XElement("Phone",
                new XAttribute("type", "work"),
                "666-666-6666")
        )
    )
);
Console.WriteLine(c);
```

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
```

<span data-ttu-id="fadc6-124">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="fadc6-124">This example produces the following output:</span></span>

```xml
<Customers>
  <Customer>
    <Name>John Doe</Name>
    <PhoneNumbers>
      <Phone type="home">555-555-5555</Phone>
      <Phone type="work">666-666-6666</Phone>
    </PhoneNumbers>
  </Customer>
</Customers>
```

## <a name="attributes-arent-nodes"></a><span data-ttu-id="fadc6-125">Atributos não são nós</span><span class="sxs-lookup"><span data-stu-id="fadc6-125">Attributes aren't nodes</span></span>

<span data-ttu-id="fadc6-126">Há algumas diferenças entre atributos e elementos.</span><span class="sxs-lookup"><span data-stu-id="fadc6-126">There are some differences between attributes and elements.</span></span> <span data-ttu-id="fadc6-127"><xref:System.Xml.Linq.XAttribute> objetos não são nós na árvore XML.</span><span class="sxs-lookup"><span data-stu-id="fadc6-127"><xref:System.Xml.Linq.XAttribute> objects aren't nodes in the XML tree.</span></span> <span data-ttu-id="fadc6-128">Eles são pares de nome-valor associados a um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="fadc6-128">They're name-value pairs associated with an XML element.</span></span> <span data-ttu-id="fadc6-129">Em contraste com Document Object Model (DOM), este reflete mais apertadamente a estrutura XML.</span><span class="sxs-lookup"><span data-stu-id="fadc6-129">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="fadc6-130">Embora os <xref:System.Xml.Linq.XAttribute> objetos não sejam realmente nós na árvore XML, trabalhar com <xref:System.Xml.Linq.XAttribute> objetos é semelhante a trabalhar com <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="fadc6-130">Although <xref:System.Xml.Linq.XAttribute> objects aren't actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="fadc6-131">Essa distinção importante é primeiro somente para os desenvolvedores que estão escrevendo código que funciona com as árvores XML no nível do nó.</span><span class="sxs-lookup"><span data-stu-id="fadc6-131">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="fadc6-132">Muitos desenvolvedores não se preocupam com essa distinção.</span><span class="sxs-lookup"><span data-stu-id="fadc6-132">Many developers won't be concerned with this distinction.</span></span>

## <a name="see-also"></a><span data-ttu-id="fadc6-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="fadc6-133">See also</span></span>

- [<span data-ttu-id="fadc6-134">Visão geral de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="fadc6-134">LINQ to XML overview</span></span>](linq-xml-overview.md)
