---
title: Propriedade de eixo descendente XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 6040401ce3e98c835677be3c4cc7698013348f37
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128989"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="ed557-102">Propriedade de eixo descendente XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed557-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="ed557-103">Fornece acesso aos descendentes dos seguintes: uma <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.</span><span class="sxs-lookup"><span data-stu-id="ed557-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed557-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed557-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="ed557-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ed557-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="ed557-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed557-106">Required.</span></span> <span data-ttu-id="ed557-107">Uma <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.</span><span class="sxs-lookup"><span data-stu-id="ed557-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="ed557-108">...<</span><span class="sxs-lookup"><span data-stu-id="ed557-108">...<</span></span>  
 <span data-ttu-id="ed557-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed557-109">Required.</span></span> <span data-ttu-id="ed557-110">Indica o início de uma propriedade de eixo descendente.</span><span class="sxs-lookup"><span data-stu-id="ed557-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="ed557-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed557-111">Required.</span></span> <span data-ttu-id="ed557-112">Nome de nós descendentes para acessar, do formulário [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="ed557-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="ed557-113">Parte</span><span class="sxs-lookup"><span data-stu-id="ed557-113">Part</span></span>|<span data-ttu-id="ed557-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed557-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="ed557-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ed557-115">Optional.</span></span> <span data-ttu-id="ed557-116">Prefixo de namespace XML para o nó descendente.</span><span class="sxs-lookup"><span data-stu-id="ed557-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="ed557-117">Deve ser um namespace XML global que é definido usando um `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="ed557-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="ed557-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed557-118">Required.</span></span> <span data-ttu-id="ed557-119">Nome local do nó descendente.</span><span class="sxs-lookup"><span data-stu-id="ed557-119">Local name of the descendant node.</span></span> <span data-ttu-id="ed557-120">Ver [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ed557-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="ed557-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed557-121">Required.</span></span> <span data-ttu-id="ed557-122">Indica o início de uma propriedade de eixo descendente.</span><span class="sxs-lookup"><span data-stu-id="ed557-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed557-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ed557-123">Return Value</span></span>  
 <span data-ttu-id="ed557-124">Uma coleção de objetos <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="ed557-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed557-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed557-125">Remarks</span></span>  
 <span data-ttu-id="ed557-126">Você pode usar uma propriedade de eixo descendente XML para acessar nós descendentes pelo nome de um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objetos.</span><span class="sxs-lookup"><span data-stu-id="ed557-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="ed557-127">Use o XML `Value` propriedade para acessar o valor do primeiro nó descendente na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="ed557-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="ed557-128">Para obter mais informações, consulte [propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="ed557-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="ed557-129">O compilador do Visual Basic converte propriedades de eixo descendente em chamadas para o <xref:System.Xml.Linq.XContainer.Descendants%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ed557-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="ed557-130">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="ed557-130">XML Namespaces</span></span>  
 <span data-ttu-id="ed557-131">O nome em uma propriedade de eixo descendente pode usar somente namespaces XML declarados globalmente com o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="ed557-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="ed557-132">Ele não é possível usar namespaces XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ed557-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="ed557-133">Para obter mais informações, consulte [instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ed557-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed557-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed557-134">Example</span></span>  
 <span data-ttu-id="ed557-135">O exemplo a seguir mostra como acessar o valor do primeiro nó descendente chamado `name` e os valores de todos os nós descendentes chamados `phone` do `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="ed557-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="ed557-136">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="ed557-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="ed557-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed557-137">Example</span></span>  
 <span data-ttu-id="ed557-138">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="ed557-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="ed557-139">Ele usa o prefixo de namespace para criar um literal XML e acessar o valor do primeiro nó filho com o nome qualificado `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="ed557-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="ed557-140">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="ed557-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="ed557-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed557-141">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="ed557-142">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="ed557-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="ed557-143">Literais XML</span><span class="sxs-lookup"><span data-stu-id="ed557-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="ed557-144">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed557-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="ed557-145">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="ed557-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
