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
ms.openlocfilehash: 728c17cd2ed8661e0a5f1f2b8e929059713a1edf
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545122"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="5727f-102">Propriedade do eixo filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5727f-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="5727f-103">Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="5727f-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5727f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5727f-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="5727f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5727f-105">Parts</span></span>  
  
|<span data-ttu-id="5727f-106">Termo</span><span class="sxs-lookup"><span data-stu-id="5727f-106">Term</span></span>|<span data-ttu-id="5727f-107">Definição</span><span class="sxs-lookup"><span data-stu-id="5727f-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="5727f-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="5727f-108">Required.</span></span> <span data-ttu-id="5727f-109">Um objeto <xref:System.Xml.Linq.XElement>, um objeto <xref:System.Xml.Linq.XDocument>, uma coleção de objetos <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5727f-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="5727f-110">.<</span><span class="sxs-lookup"><span data-stu-id="5727f-110">.<</span></span>|<span data-ttu-id="5727f-111">Necessária.</span><span class="sxs-lookup"><span data-stu-id="5727f-111">Required.</span></span> <span data-ttu-id="5727f-112">Denota o início de uma propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="5727f-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="5727f-113">Necessária.</span><span class="sxs-lookup"><span data-stu-id="5727f-113">Required.</span></span> <span data-ttu-id="5727f-114">Nome dos nós filho a serem acessados, do formulário `[prefix:]name`.</span><span class="sxs-lookup"><span data-stu-id="5727f-114">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="5727f-115">-   `Prefix`-opcional.</span><span class="sxs-lookup"><span data-stu-id="5727f-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="5727f-116">Prefixo do namespace XML para o nó filho.</span><span class="sxs-lookup"><span data-stu-id="5727f-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="5727f-117">Deve ser um namespace XML global definido com uma instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="5727f-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="5727f-118">-   `Name`-obrigatório.</span><span class="sxs-lookup"><span data-stu-id="5727f-118">-   `Name` - Required.</span></span> <span data-ttu-id="5727f-119">Nome do nó filho local.</span><span class="sxs-lookup"><span data-stu-id="5727f-119">Local child node name.</span></span> <span data-ttu-id="5727f-120">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5727f-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="5727f-121">Necessária.</span><span class="sxs-lookup"><span data-stu-id="5727f-121">Required.</span></span> <span data-ttu-id="5727f-122">Denota o final de uma propriedade do eixo filho.</span><span class="sxs-lookup"><span data-stu-id="5727f-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="5727f-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5727f-123">Return Value</span></span>  
 <span data-ttu-id="5727f-124">Uma coleção de objetos <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="5727f-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5727f-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="5727f-125">Remarks</span></span>  
 <span data-ttu-id="5727f-126">Você pode usar uma propriedade de eixo filho XML para acessar nós filho pelo nome de um objeto <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> ou de uma coleção de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5727f-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="5727f-127">Use a propriedade XML `Value` para acessar o valor do primeiro nó filho na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="5727f-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="5727f-128">Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="5727f-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="5727f-129">O compilador Visual Basic converte Propriedades de eixo filho em chamadas para o método <xref:System.Xml.Linq.XContainer.Elements%2A>.</span><span class="sxs-lookup"><span data-stu-id="5727f-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5727f-130">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="5727f-130">XML Namespaces</span></span>  
 <span data-ttu-id="5727f-131">O nome em uma propriedade de eixo filho pode usar somente os prefixos de namespace XML declarados globalmente com a instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="5727f-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="5727f-132">Ele não pode usar prefixos de namespace XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="5727f-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="5727f-133">Para obter mais informações, consulte [instrução Imports (namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5727f-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5727f-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5727f-134">Example</span></span>  
 <span data-ttu-id="5727f-135">O exemplo a seguir mostra como acessar os nós filho chamados `phone` do objeto `contact`.</span><span class="sxs-lookup"><span data-stu-id="5727f-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="5727f-136">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5727f-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="5727f-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5727f-137">Example</span></span>  
 <span data-ttu-id="5727f-138">O exemplo a seguir mostra como acessar os nós filho chamados `phone` da coleção retornada pela propriedade eixo filho `contact` do objeto `contacts`.</span><span class="sxs-lookup"><span data-stu-id="5727f-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="5727f-139">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5727f-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="5727f-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5727f-140">Example</span></span>  
 <span data-ttu-id="5727f-141">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5727f-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5727f-142">Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="5727f-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="5727f-143">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5727f-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="5727f-144">Veja também</span><span class="sxs-lookup"><span data-stu-id="5727f-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="5727f-145">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="5727f-145">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="5727f-146">Literais XML</span><span class="sxs-lookup"><span data-stu-id="5727f-146">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="5727f-147">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5727f-147">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="5727f-148">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="5727f-148">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
