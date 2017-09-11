---
title: Propriedade de eixo descendente XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
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
ms.openlocfilehash: e84a8bb989ebbed57595ebf93cef620027a04328
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="df7d9-102">Propriedade de eixo descendente XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df7d9-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="df7d9-103">Fornece acesso aos descendentes dos seguintes: um <xref:System.Xml.Linq.XElement>objeto, um <xref:System.Xml.Linq.XDocument>objeto, uma coleção de <xref:System.Xml.Linq.XElement>objetos ou uma coleção de <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7d9-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df7d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df7d9-104">Syntax</span></span>  
  
```  
  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="df7d9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="df7d9-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="df7d9-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7d9-106">Required.</span></span> <span data-ttu-id="df7d9-107">Um <xref:System.Xml.Linq.XElement>objeto, um <xref:System.Xml.Linq.XDocument>objeto, uma coleção de <xref:System.Xml.Linq.XElement>objetos ou uma coleção de <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7d9-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="df7d9-108">...<</span><span class="sxs-lookup"><span data-stu-id="df7d9-108">...<</span></span>  
 <span data-ttu-id="df7d9-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7d9-109">Required.</span></span> <span data-ttu-id="df7d9-110">Indica o início de uma propriedade de eixo descendente.</span><span class="sxs-lookup"><span data-stu-id="df7d9-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="df7d9-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7d9-111">Required.</span></span> <span data-ttu-id="df7d9-112">Nome de nós descendentes a serem acessados, do formulário [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="df7d9-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="df7d9-113">Parte</span><span class="sxs-lookup"><span data-stu-id="df7d9-113">Part</span></span>|<span data-ttu-id="df7d9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="df7d9-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="df7d9-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="df7d9-115">Optional.</span></span> <span data-ttu-id="df7d9-116">Prefixo de namespace XML para o nó descendente.</span><span class="sxs-lookup"><span data-stu-id="df7d9-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="df7d9-117">Deve ser um namespace XML global que é definido usando um `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="df7d9-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="df7d9-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7d9-118">Required.</span></span> <span data-ttu-id="df7d9-119">Nome local do nó descendente.</span><span class="sxs-lookup"><span data-stu-id="df7d9-119">Local name of the descendant node.</span></span> <span data-ttu-id="df7d9-120">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="df7d9-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="df7d9-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="df7d9-121">Required.</span></span> <span data-ttu-id="df7d9-122">Indica o início de uma propriedade de eixo descendente.</span><span class="sxs-lookup"><span data-stu-id="df7d9-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df7d9-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="df7d9-123">Return Value</span></span>  
 <span data-ttu-id="df7d9-124">Uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7d9-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df7d9-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="df7d9-125">Remarks</span></span>  
 <span data-ttu-id="df7d9-126">Você pode usar uma propriedade de eixo descendente XML para acessar nós descendentes pelo nome de uma <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7d9-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="df7d9-127">Usar o XML `Value` propriedade para acessar o valor do primeiro nó descendente na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="df7d9-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="df7d9-128">Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="df7d9-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="df7d9-129">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte as propriedades de eixo descendente em chamadas para o <xref:System.Xml.Linq.XContainer.Descendants%2A>método.</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="df7d9-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="df7d9-130">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="df7d9-130">XML Namespaces</span></span>  
 <span data-ttu-id="df7d9-131">O nome em uma propriedade de eixo descendente pode usar somente namespaces XML declarados globalmente com a `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="df7d9-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="df7d9-132">Ele não pode usar namespaces XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="df7d9-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="df7d9-133">Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="df7d9-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df7d9-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df7d9-134">Example</span></span>  
 <span data-ttu-id="df7d9-135">O exemplo a seguir mostra como acessar o valor do primeiro nó descendente chamado `name` e os valores de todos os nós descendentes chamados `phone` do `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="df7d9-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 <span data-ttu-id="df7d9-136">[!code-vb[25 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="df7d9-136">[!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="df7d9-137">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="df7d9-137">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="df7d9-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df7d9-138">Example</span></span>  
 <span data-ttu-id="df7d9-139">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="df7d9-139">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="df7d9-140">Ele usa o prefixo de namespace para criar um literal XML e acessar o valor do primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="df7d9-140">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 <span data-ttu-id="df7d9-141">[!code-vb[VbXMLSamples&#26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="df7d9-141">[!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="df7d9-142">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="df7d9-142">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="df7d9-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df7d9-143">See Also</span></span>  
 <span data-ttu-id="df7d9-144"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="df7d9-144"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="df7d9-145"> [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="df7d9-145"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="df7d9-146"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="df7d9-146"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="df7d9-147"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="df7d9-147"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="df7d9-148"> [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="df7d9-148"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
