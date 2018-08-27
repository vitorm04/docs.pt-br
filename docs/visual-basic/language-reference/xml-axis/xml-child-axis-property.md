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
ms.openlocfilehash: 0b504a9e368e5179d5f91faf7256445d7da47b1d
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929607"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="a564e-102">Propriedade do eixo filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a564e-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="a564e-103">Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="a564e-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a564e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a564e-104">Syntax</span></span>  
  
```  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="a564e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a564e-105">Parts</span></span>  
  
|<span data-ttu-id="a564e-106">Termo</span><span class="sxs-lookup"><span data-stu-id="a564e-106">Term</span></span>|<span data-ttu-id="a564e-107">Definição</span><span class="sxs-lookup"><span data-stu-id="a564e-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="a564e-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a564e-108">Required.</span></span> <span data-ttu-id="a564e-109">Uma <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.</span><span class="sxs-lookup"><span data-stu-id="a564e-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="a564e-110">.<</span><span class="sxs-lookup"><span data-stu-id="a564e-110">.<</span></span>|<span data-ttu-id="a564e-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a564e-111">Required.</span></span> <span data-ttu-id="a564e-112">Indica o início de uma propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="a564e-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="a564e-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a564e-113">Required.</span></span> <span data-ttu-id="a564e-114">Nome de nós filho para acessar, do formulário [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="a564e-114">Name of the child nodes to access, of the form [`prefix``:`]`name`.</span></span><br /><br /> <span data-ttu-id="a564e-115">-   `Prefix` -Opcional.</span><span class="sxs-lookup"><span data-stu-id="a564e-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="a564e-116">Prefixo de namespace XML para o nó filho.</span><span class="sxs-lookup"><span data-stu-id="a564e-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="a564e-117">Deve ser um namespace XML global definido com um `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="a564e-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="a564e-118">-   `Name` -Required.</span><span class="sxs-lookup"><span data-stu-id="a564e-118">-   `Name` - Required.</span></span> <span data-ttu-id="a564e-119">Nome do nó filho local.</span><span class="sxs-lookup"><span data-stu-id="a564e-119">Local child node name.</span></span> <span data-ttu-id="a564e-120">Ver [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a564e-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="a564e-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a564e-121">Required.</span></span> <span data-ttu-id="a564e-122">Indica o início de uma propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="a564e-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="a564e-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a564e-123">Return Value</span></span>  
 <span data-ttu-id="a564e-124">Uma coleção de objetos <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="a564e-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a564e-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="a564e-125">Remarks</span></span>  
 <span data-ttu-id="a564e-126">Você pode usar uma propriedade de eixo filho XML para acessar os nós filho pelo nome de um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objetos.</span><span class="sxs-lookup"><span data-stu-id="a564e-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="a564e-127">Use o XML `Value` propriedade para acessar o valor do primeiro nó filho na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="a564e-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="a564e-128">Para obter mais informações, consulte [propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="a564e-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="a564e-129">O compilador do Visual Basic converte propriedades de eixo filho em chamadas para o <xref:System.Xml.Linq.XContainer.Elements%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a564e-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="a564e-130">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="a564e-130">XML Namespaces</span></span>  
 <span data-ttu-id="a564e-131">O nome em uma propriedade de eixo filho pode usar somente prefixos de namespace XML declarados globalmente com o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="a564e-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="a564e-132">Ele não é possível usar prefixos de namespace XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="a564e-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="a564e-133">Para obter mais informações, consulte [instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="a564e-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a564e-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a564e-134">Example</span></span>  
 <span data-ttu-id="a564e-135">O exemplo a seguir mostra como acessar os nós filho chamados `phone` do `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="a564e-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 <span data-ttu-id="a564e-136">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="a564e-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="a564e-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a564e-137">Example</span></span>  
 <span data-ttu-id="a564e-138">O exemplo a seguir mostra como acessar os nós filho chamados `phone` da coleção retornada pela `contact` propriedade de eixo filho do `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="a564e-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 <span data-ttu-id="a564e-139">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="a564e-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="a564e-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a564e-140">Example</span></span>  
 <span data-ttu-id="a564e-141">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="a564e-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="a564e-142">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="a564e-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 <span data-ttu-id="a564e-143">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="a564e-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="a564e-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a564e-144">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="a564e-145">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="a564e-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="a564e-146">Literais XML</span><span class="sxs-lookup"><span data-stu-id="a564e-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="a564e-147">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a564e-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="a564e-148">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="a564e-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
