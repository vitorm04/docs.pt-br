---
title: Propriedade de eixo descendente XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: e2c3e01808d3eeb18f6753a5fc79b8627e7f323b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582224"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="dc375-102">Propriedade de eixo descendente XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc375-102">XML Descendant Axis Property (Visual Basic)</span></span>

<span data-ttu-id="dc375-103">Fornece acesso aos descendentes dos seguintes: um objeto <xref:System.Xml.Linq.XElement>, um objeto <xref:System.Xml.Linq.XDocument>, uma coleção de objetos <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="dc375-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="dc375-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc375-104">Syntax</span></span>

```vb
object...<descendant>
```

## <a name="parts"></a><span data-ttu-id="dc375-105">Partes</span><span class="sxs-lookup"><span data-stu-id="dc375-105">Parts</span></span>

<span data-ttu-id="dc375-106">`object` Necessário.</span><span class="sxs-lookup"><span data-stu-id="dc375-106">`object` Required.</span></span> <span data-ttu-id="dc375-107">Um objeto <xref:System.Xml.Linq.XElement>, um objeto <xref:System.Xml.Linq.XDocument>, uma coleção de objetos <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="dc375-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>

<span data-ttu-id="dc375-108">`...<` Necessário.</span><span class="sxs-lookup"><span data-stu-id="dc375-108">`...<` Required.</span></span> <span data-ttu-id="dc375-109">Denota o início de uma propriedade de eixo descendente.</span><span class="sxs-lookup"><span data-stu-id="dc375-109">Denotes the start of a descendant axis property.</span></span>

<span data-ttu-id="dc375-110">`descendant` Necessário.</span><span class="sxs-lookup"><span data-stu-id="dc375-110">`descendant` Required.</span></span> <span data-ttu-id="dc375-111">Nome dos nós descendentes a serem acessados, no formato [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="dc375-111">Name of the descendant nodes to access, of the form [`prefix:]name`.</span></span>

|<span data-ttu-id="dc375-112">Parte</span><span class="sxs-lookup"><span data-stu-id="dc375-112">Part</span></span>|<span data-ttu-id="dc375-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc375-113">Description</span></span>|
|----------|-----------------|
|`prefix`|<span data-ttu-id="dc375-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="dc375-114">Optional.</span></span> <span data-ttu-id="dc375-115">Prefixo do namespace XML para o nó descendente.</span><span class="sxs-lookup"><span data-stu-id="dc375-115">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="dc375-116">Deve ser um namespace XML global que é definido usando uma instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="dc375-116">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|
|`name`|<span data-ttu-id="dc375-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="dc375-117">Required.</span></span> <span data-ttu-id="dc375-118">Nome local do nó descendente.</span><span class="sxs-lookup"><span data-stu-id="dc375-118">Local name of the descendant node.</span></span> <span data-ttu-id="dc375-119">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="dc375-119">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|

<span data-ttu-id="dc375-120">`>` Necessário.</span><span class="sxs-lookup"><span data-stu-id="dc375-120">`>` Required.</span></span> <span data-ttu-id="dc375-121">Denota o final de uma propriedade de eixo descendente.</span><span class="sxs-lookup"><span data-stu-id="dc375-121">Denotes the end of a descendant axis property.</span></span>

## <a name="return-value"></a><span data-ttu-id="dc375-122">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dc375-122">Return Value</span></span>

<span data-ttu-id="dc375-123">Uma coleção de objetos <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="dc375-123">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc375-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc375-124">Remarks</span></span>

<span data-ttu-id="dc375-125">Você pode usar uma propriedade de eixo descendente XML para acessar nós descendentes por nome de um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto ou de uma coleção de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="dc375-125">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="dc375-126">Use a propriedade XML `Value` para acessar o valor do primeiro nó descendente na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="dc375-126">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="dc375-127">Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="dc375-127">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>

<span data-ttu-id="dc375-128">O compilador Visual Basic converte Propriedades do eixo descendente em chamadas para o método <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc375-128">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>

## <a name="xml-namespaces"></a><span data-ttu-id="dc375-129">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="dc375-129">XML Namespaces</span></span>

<span data-ttu-id="dc375-130">O nome em uma propriedade de eixo descendente pode usar somente namespaces XML declarados globalmente com a instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="dc375-130">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="dc375-131">Ele não pode usar namespaces XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="dc375-131">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="dc375-132">Para obter mais informações, consulte [instrução Imports (namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="dc375-132">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>

## <a name="example"></a><span data-ttu-id="dc375-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc375-133">Example</span></span>

<span data-ttu-id="dc375-134">O exemplo a seguir mostra como acessar o valor do primeiro nó descendente chamado `name` e os valores de todos os nós descendentes chamados `phone` do objeto `contacts`.</span><span class="sxs-lookup"><span data-stu-id="dc375-134">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

<span data-ttu-id="dc375-135">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="dc375-135">This code displays the following text:</span></span>

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a><span data-ttu-id="dc375-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc375-136">Example</span></span>

<span data-ttu-id="dc375-137">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="dc375-137">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="dc375-138">Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o valor do primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="dc375-138">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

<span data-ttu-id="dc375-139">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="dc375-139">This code displays the following text:</span></span>

`Name: Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="dc375-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc375-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="dc375-141">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="dc375-141">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="dc375-142">Literais XML</span><span class="sxs-lookup"><span data-stu-id="dc375-142">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="dc375-143">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc375-143">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="dc375-144">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="dc375-144">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
