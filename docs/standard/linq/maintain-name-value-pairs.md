---
title: Manter pares de nome-valor-LINQ to XML
description: Saiba como usar os métodos de LINQ to XML para manter um conjunto de pares de nome-valor.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 681df91d42f8bdb403dcf6f735104301c4a0c9ba
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551964"
---
# <a name="maintain-name-value-pairs-linq-to-xml"></a><span data-ttu-id="833a9-103">Manter pares de nome-valor (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="833a9-103">Maintain name-value pairs (LINQ to XML)</span></span>

<span data-ttu-id="833a9-104">Muitos aplicativos precisam manter as informações que são mais bem mantidas como pares de nome-valor.</span><span class="sxs-lookup"><span data-stu-id="833a9-104">Many applications have to maintain information that is best kept as name-value pairs.</span></span> <span data-ttu-id="833a9-105">Essas informações podem ser informações de configuração ou configurações globais.</span><span class="sxs-lookup"><span data-stu-id="833a9-105">This information might be configuration information or global settings.</span></span> <span data-ttu-id="833a9-106">LINQ to XML contém métodos que facilitam a manutenção de um conjunto de pares de nome-valor.</span><span class="sxs-lookup"><span data-stu-id="833a9-106">LINQ to XML contains methods that make it easy to maintain a set of name-value pairs.</span></span> <span data-ttu-id="833a9-107">É possível manter informações como atributos ou como um conjunto de elementos filho.</span><span class="sxs-lookup"><span data-stu-id="833a9-107">You can either keep the information as attributes or as a set of child elements.</span></span>

<span data-ttu-id="833a9-108">Uma das diferenças entre manter as informações como atributos ou como elementos filho é que os atributos possuem a restrição de que pode existir apenas um atributo com um nome específico para um elemento.</span><span class="sxs-lookup"><span data-stu-id="833a9-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="833a9-109">Essa limitação não se aplica a elementos filho.</span><span class="sxs-lookup"><span data-stu-id="833a9-109">This limitation doesn't apply to child elements.</span></span>

## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="833a9-110">SetAttributeValue e SetElementValue</span><span class="sxs-lookup"><span data-stu-id="833a9-110">SetAttributeValue and SetElementValue</span></span>

<span data-ttu-id="833a9-111">Os dois métodos que facilitam a manutenção de pares de nome-valor são <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> e <xref:System.Xml.Linq.XElement.SetElementValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="833a9-111">The two methods that facilitate keeping name-value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="833a9-112">Esses dois métodos possuem semântica semelhante.</span><span class="sxs-lookup"><span data-stu-id="833a9-112">These two methods have similar semantics.</span></span>

<span data-ttu-id="833a9-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> pode adicionar, modificar e remover atributos de um elemento.</span><span class="sxs-lookup"><span data-stu-id="833a9-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, and remove attributes of an element.</span></span>

- <span data-ttu-id="833a9-114">Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com um nome de um atributo que não existe, o método criará um novo atributo e o adicionará ao elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="833a9-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that doesn't exist, the method creates a new attribute and adds it to the specified element.</span></span>
- <span data-ttu-id="833a9-115">Ao designar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com o nome de um atributo existente e algum conteúdo especificado, o conteúdo do atributo é substituído pelo conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="833a9-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>
- <span data-ttu-id="833a9-116">Se você chamar <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> com um nome de um atributo existente e especificar `null` para o conteúdo, o atributo será removido de seu pai.</span><span class="sxs-lookup"><span data-stu-id="833a9-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify `null` for the content, the attribute is removed from its parent.</span></span>

<span data-ttu-id="833a9-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> pode adicionar, modificar e remover elementos filho de um elemento.</span><span class="sxs-lookup"><span data-stu-id="833a9-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, and remove child elements of an element.</span></span>

- <span data-ttu-id="833a9-118">Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com um nome de um elemento filho que não existe, o método criará um novo elemento e o adicionará ao elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="833a9-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that doesn't exist, the method creates a new element and adds it to the specified element.</span></span>
- <span data-ttu-id="833a9-119">Ao designar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com o nome de um elemento existente e algum conteúdo especificado, o conteúdo do elemento é substituído pelo conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="833a9-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>
- <span data-ttu-id="833a9-120">Se você chamar <xref:System.Xml.Linq.XElement.SetElementValue%2A> com um nome de um elemento existente e especificar `null` para o conteúdo, o elemento será removido de seu pai.</span><span class="sxs-lookup"><span data-stu-id="833a9-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify `null` for the content, the element is removed from its parent.</span></span>

## <a name="example-use-setattributevalue-to-create-and-maintain-a-list-of-name-value-pairs"></a><span data-ttu-id="833a9-121">Exemplo: use `SetAttributeValue` para criar e manter uma lista de pares de nome-valor</span><span class="sxs-lookup"><span data-stu-id="833a9-121">Example: Use `SetAttributeValue` to create and maintain a list of name-value pairs</span></span>

<span data-ttu-id="833a9-122">O exemplo a seguir cria um elemento sem atributos.</span><span class="sxs-lookup"><span data-stu-id="833a9-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="833a9-123">Em seguida, ele usa o <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> método para criar e manter uma lista de pares de nome-valor.</span><span class="sxs-lookup"><span data-stu-id="833a9-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name-value pairs.</span></span>

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22);
root.SetAttributeValue("Left", 20);
root.SetAttributeValue("Bottom", 122);
root.SetAttributeValue("Right", 300);
root.SetAttributeValue("DefaultColor", "Color.Red");
Console.WriteLine(root);

// Replace the value of Top.
root.SetAttributeValue("Top", 10);
Console.WriteLine(root);

// Remove DefaultColor.
root.SetAttributeValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22)
root.SetAttributeValue("Left", 20)
root.SetAttributeValue("Bottom", 122)
root.SetAttributeValue("Right", 300)
root.SetAttributeValue("DefaultColor", "Color.Red")
Console.WriteLine(root)

' Replace the value of Top.
root.SetAttributeValue("Top", 10)
Console.WriteLine(root)

' Remove DefaultColor.
root.SetAttributeValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

<span data-ttu-id="833a9-124">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="833a9-124">This example produces the following output:</span></span>

```xml
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" />
```

## <a name="example-use-setelementvalue-to-create-and-maintain-a-list-of-name-value-pairs"></a><span data-ttu-id="833a9-125">Exemplo: use `SetElementValue` para criar e manter uma lista de pares de nome-valor</span><span class="sxs-lookup"><span data-stu-id="833a9-125">Example: Use `SetElementValue` to create and maintain a list of name-value pairs</span></span>

<span data-ttu-id="833a9-126">O exemplo a seguir cria um elemento sem elementos filho.</span><span class="sxs-lookup"><span data-stu-id="833a9-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="833a9-127">Em seguida, ele usa o <xref:System.Xml.Linq.XElement.SetElementValue%2A> método para criar e manter uma lista de pares de nome-valor.</span><span class="sxs-lookup"><span data-stu-id="833a9-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name-value pairs.</span></span>

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22);
root.SetElementValue("Left", 20);
root.SetElementValue("Bottom", 122);
root.SetElementValue("Right", 300);
root.SetElementValue("DefaultColor", "Color.Red");
Console.WriteLine(root);
Console.WriteLine("----");

// Replace the value of Top.
root.SetElementValue("Top", 10);
Console.WriteLine(root);
Console.WriteLine("----");

// Remove DefaultColor.
root.SetElementValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22)
root.SetElementValue("Left", 20)
root.SetElementValue("Bottom", 122)
root.SetElementValue("Right", 300)
root.SetElementValue("DefaultColor", "Color.Red")
Console.WriteLine(root)
Console.WriteLine("----")

' Replace the value of Top.
root.SetElementValue("Top", 10)
Console.WriteLine(root)
Console.WriteLine("----")

' Remove DefaultColor.
root.SetElementValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

<span data-ttu-id="833a9-128">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="833a9-128">This example produces the following output:</span></span>

```xml
<Root>
  <Top>22</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="833a9-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="833a9-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
