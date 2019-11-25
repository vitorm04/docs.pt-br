---
title: Propriedade do eixo filho XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 968154908bc6cb62bb221d42a1f71b329aa7096f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349463"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="b8cd8-102">Propriedade do eixo filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8cd8-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="b8cd8-103">Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8cd8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8cd8-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="b8cd8-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b8cd8-105">Parts</span></span>  
  
|<span data-ttu-id="b8cd8-106">Termo</span><span class="sxs-lookup"><span data-stu-id="b8cd8-106">Term</span></span>|<span data-ttu-id="b8cd8-107">Definição</span><span class="sxs-lookup"><span data-stu-id="b8cd8-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="b8cd8-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-108">Required.</span></span> <span data-ttu-id="b8cd8-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="b8cd8-110">.<</span><span class="sxs-lookup"><span data-stu-id="b8cd8-110">.<</span></span>|<span data-ttu-id="b8cd8-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-111">Required.</span></span> <span data-ttu-id="b8cd8-112">Denotes the start of a child axis property.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="b8cd8-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-113">Required.</span></span> <span data-ttu-id="b8cd8-114">Name of the child nodes to access, of the form [`prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-114">Name of the child nodes to access, of the form [`prefix:]name`.</span></span><br /><br /> <span data-ttu-id="b8cd8-115">-   `Prefix` - Optional.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="b8cd8-116">XML namespace prefix for the child node.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="b8cd8-117">Must be a global XML namespace defined with an `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="b8cd8-118">-   `Name` - Required.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-118">-   `Name` - Required.</span></span> <span data-ttu-id="b8cd8-119">Local child node name.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-119">Local child node name.</span></span> <span data-ttu-id="b8cd8-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b8cd8-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="b8cd8-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-121">Required.</span></span> <span data-ttu-id="b8cd8-122">Denotes the end of a child axis property.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="b8cd8-123">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b8cd8-123">Return Value</span></span>  
 <span data-ttu-id="b8cd8-124">Uma coleção de objetos <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="b8cd8-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8cd8-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8cd8-125">Remarks</span></span>  
 <span data-ttu-id="b8cd8-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="b8cd8-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="b8cd8-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="b8cd8-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="b8cd8-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="b8cd8-130">XML Namespaces</span><span class="sxs-lookup"><span data-stu-id="b8cd8-130">XML Namespaces</span></span>  
 <span data-ttu-id="b8cd8-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="b8cd8-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="b8cd8-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b8cd8-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8cd8-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8cd8-134">Example</span></span>  
 <span data-ttu-id="b8cd8-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="b8cd8-136">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="b8cd8-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="b8cd8-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8cd8-137">Example</span></span>  
 <span data-ttu-id="b8cd8-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="b8cd8-139">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="b8cd8-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="b8cd8-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8cd8-140">Example</span></span>  
 <span data-ttu-id="b8cd8-141">The following example declares `ns` as an XML namespace prefix.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b8cd8-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="b8cd8-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="b8cd8-143">This code displays the following text:</span><span class="sxs-lookup"><span data-stu-id="b8cd8-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="b8cd8-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8cd8-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="b8cd8-145">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="b8cd8-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="b8cd8-146">Literais XML</span><span class="sxs-lookup"><span data-stu-id="b8cd8-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="b8cd8-147">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8cd8-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="b8cd8-148">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="b8cd8-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
