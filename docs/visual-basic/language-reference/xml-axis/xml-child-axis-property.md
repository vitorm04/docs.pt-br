---
title: Propriedade do eixo filho XML (Visual Basic)
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
ms.openlocfilehash: 696d14630240dce094ace7d595232e1a210ea78e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527140"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="92d7f-102">Propriedade do eixo filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92d7f-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="92d7f-103">Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="92d7f-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92d7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92d7f-104">Syntax</span></span>  
  
```  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="92d7f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="92d7f-105">Parts</span></span>  
  
|<span data-ttu-id="92d7f-106">Termo</span><span class="sxs-lookup"><span data-stu-id="92d7f-106">Term</span></span>|<span data-ttu-id="92d7f-107">Definição</span><span class="sxs-lookup"><span data-stu-id="92d7f-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="92d7f-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="92d7f-108">Required.</span></span> <span data-ttu-id="92d7f-109">Uma <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.</span><span class="sxs-lookup"><span data-stu-id="92d7f-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="92d7f-110">.<</span><span class="sxs-lookup"><span data-stu-id="92d7f-110">.<</span></span>|<span data-ttu-id="92d7f-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="92d7f-111">Required.</span></span> <span data-ttu-id="92d7f-112">Indica o início de uma propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="92d7f-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="92d7f-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="92d7f-113">Required.</span></span> <span data-ttu-id="92d7f-114">Nome de nós filho para acessar, do formulário [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="92d7f-114">Name of the child nodes to access, of the form [`prefix``:`]`name`.</span></span><br /><br /> <span data-ttu-id="92d7f-115">-   `Prefix` -Opcional.</span><span class="sxs-lookup"><span data-stu-id="92d7f-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="92d7f-116">Prefixo de namespace XML para o nó filho.</span><span class="sxs-lookup"><span data-stu-id="92d7f-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="92d7f-117">Deve ser um namespace XML global definido com um `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="92d7f-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="92d7f-118">-   `Name` -Required.</span><span class="sxs-lookup"><span data-stu-id="92d7f-118">-   `Name` - Required.</span></span> <span data-ttu-id="92d7f-119">Nome do nó filho local.</span><span class="sxs-lookup"><span data-stu-id="92d7f-119">Local child node name.</span></span> <span data-ttu-id="92d7f-120">Ver [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="92d7f-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="92d7f-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="92d7f-121">Required.</span></span> <span data-ttu-id="92d7f-122">Indica o início de uma propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="92d7f-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="92d7f-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="92d7f-123">Return Value</span></span>  
 <span data-ttu-id="92d7f-124">Uma coleção de objetos <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="92d7f-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92d7f-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="92d7f-125">Remarks</span></span>  
 <span data-ttu-id="92d7f-126">Você pode usar uma propriedade de eixo filho XML para acessar os nós filho pelo nome de um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objetos.</span><span class="sxs-lookup"><span data-stu-id="92d7f-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="92d7f-127">Use o XML `Value` propriedade para acessar o valor do primeiro nó filho na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="92d7f-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="92d7f-128">Para obter mais informações, consulte [propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="92d7f-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="92d7f-129">O compilador do Visual Basic converte propriedades de eixo filho em chamadas para o <xref:System.Xml.Linq.XContainer.Elements%2A> método.</span><span class="sxs-lookup"><span data-stu-id="92d7f-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="92d7f-130">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="92d7f-130">XML Namespaces</span></span>  
 <span data-ttu-id="92d7f-131">O nome em uma propriedade de eixo filho pode usar somente prefixos de namespace XML declarados globalmente com o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="92d7f-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="92d7f-132">Ele não é possível usar prefixos de namespace XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="92d7f-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="92d7f-133">Para obter mais informações, consulte [instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="92d7f-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92d7f-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92d7f-134">Example</span></span>  
 <span data-ttu-id="92d7f-135">O exemplo a seguir mostra como acessar os nós filho chamados `phone` do `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="92d7f-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 <span data-ttu-id="92d7f-136">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="92d7f-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="92d7f-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92d7f-137">Example</span></span>  
 <span data-ttu-id="92d7f-138">O exemplo a seguir mostra como acessar os nós filho chamados `phone` da coleção retornada pela `contact` propriedade de eixo filho do `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="92d7f-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 <span data-ttu-id="92d7f-139">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="92d7f-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="92d7f-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92d7f-140">Example</span></span>  
 <span data-ttu-id="92d7f-141">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="92d7f-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="92d7f-142">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="92d7f-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 <span data-ttu-id="92d7f-143">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="92d7f-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="92d7f-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92d7f-144">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="92d7f-145">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="92d7f-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="92d7f-146">Literais XML</span><span class="sxs-lookup"><span data-stu-id="92d7f-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="92d7f-147">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92d7f-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="92d7f-148">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="92d7f-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
