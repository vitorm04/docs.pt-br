---
title: Propriedade de eixo filho XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyChildAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2ccdacdadf219b9c928558f07e0890be6471d40a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="df7e6-102">Propriedade do eixo filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df7e6-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="df7e6-103">Fornece acesso aos descendentes de um dos seguintes: um <xref:System.Xml.Linq.XElement>objeto, um <xref:System.Xml.Linq.XDocument>objeto, uma coleção de <xref:System.Xml.Linq.XElement>objetos ou uma coleção de <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7e6-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df7e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df7e6-104">Syntax</span></span>  
  
```  
  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="df7e6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="df7e6-105">Parts</span></span>  
  
|<span data-ttu-id="df7e6-106">Termo</span><span class="sxs-lookup"><span data-stu-id="df7e6-106">Term</span></span>|<span data-ttu-id="df7e6-107">Definição</span><span class="sxs-lookup"><span data-stu-id="df7e6-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="df7e6-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7e6-108">Required.</span></span> <span data-ttu-id="df7e6-109">Um <xref:System.Xml.Linq.XElement>objeto, um <xref:System.Xml.Linq.XDocument>objeto, uma coleção de <xref:System.Xml.Linq.XElement>objetos ou uma coleção de <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7e6-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="df7e6-110">.<</span><span class="sxs-lookup"><span data-stu-id="df7e6-110">.<</span></span>|<span data-ttu-id="df7e6-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7e6-111">Required.</span></span> <span data-ttu-id="df7e6-112">Indica o início de uma propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="df7e6-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="df7e6-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7e6-113">Required.</span></span> <span data-ttu-id="df7e6-114">Nome de nós filho para acessar, do formulário [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="df7e6-114">Name of the child nodes to access, of the form [`prefix``:`]`name`.</span></span><br /><br /><span data-ttu-id="df7e6-115"> -   `Prefix`-Opcional.</span><span class="sxs-lookup"><span data-stu-id="df7e6-115"> -   `Prefix` - Optional.</span></span> <span data-ttu-id="df7e6-116">Prefixo de namespace XML para o nó filho.</span><span class="sxs-lookup"><span data-stu-id="df7e6-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="df7e6-117">Deve ser um namespace XML global definido com um `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="df7e6-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="df7e6-118">-   `Name`-Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7e6-118">-   `Name` - Required.</span></span> <span data-ttu-id="df7e6-119">Nome do nó filho local.</span><span class="sxs-lookup"><span data-stu-id="df7e6-119">Local child node name.</span></span> <span data-ttu-id="df7e6-120">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="df7e6-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="df7e6-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7e6-121">Required.</span></span> <span data-ttu-id="df7e6-122">Indica o início de uma propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="df7e6-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="df7e6-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="df7e6-123">Return Value</span></span>  
 <span data-ttu-id="df7e6-124">Uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7e6-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df7e6-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="df7e6-125">Remarks</span></span>  
 <span data-ttu-id="df7e6-126">Você pode usar uma propriedade de eixo filho XML para acessar os nós filho por nome de um <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7e6-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="df7e6-127">Usar o XML `Value` propriedade para acessar o valor do primeiro nó filho na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="df7e6-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="df7e6-128">Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="df7e6-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="df7e6-129">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte propriedades de eixo filho em chamadas para o <xref:System.Xml.Linq.XContainer.Elements%2A>método.</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="df7e6-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="df7e6-130">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="df7e6-130">XML Namespaces</span></span>  
 <span data-ttu-id="df7e6-131">O nome em uma propriedade de eixo filho pode usar somente prefixos de namespace XML declarados globalmente com a `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="df7e6-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="df7e6-132">Ele não é possível usar prefixos de namespace XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="df7e6-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="df7e6-133">Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="df7e6-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df7e6-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df7e6-134">Example</span></span>  
 <span data-ttu-id="df7e6-135">O exemplo a seguir mostra como acessar os nós filho chamados `phone` do `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="df7e6-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 <span data-ttu-id="df7e6-136">[!code-vb[17 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="df7e6-136">[!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="df7e6-137">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="df7e6-137">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="df7e6-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df7e6-138">Example</span></span>  
 <span data-ttu-id="df7e6-139">O exemplo a seguir mostra como acessar os nós filho chamados `phone` da coleção retornada pelo `contact` propriedade de eixo filho do `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="df7e6-139">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 <span data-ttu-id="df7e6-140">[!code-vb[VbXMLSamples n º&18;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="df7e6-140">[!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="df7e6-141">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="df7e6-141">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="df7e6-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df7e6-142">Example</span></span>  
 <span data-ttu-id="df7e6-143">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="df7e6-143">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="df7e6-144">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="df7e6-144">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 <span data-ttu-id="df7e6-145">[!code-vb[19 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="df7e6-145">[!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]</span></span>  
  
 <span data-ttu-id="df7e6-146">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="df7e6-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="df7e6-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df7e6-147">See Also</span></span>  
 <span data-ttu-id="df7e6-148"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7e6-148"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="df7e6-149"> [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="df7e6-149"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="df7e6-150"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="df7e6-150"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="df7e6-151"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="df7e6-151"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="df7e6-152"> [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="df7e6-152"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
