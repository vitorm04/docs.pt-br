---
title: Propriedade do Eixo Filho XML
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
ms.openlocfilehash: 90dc22d12be5566fa1ee40f6b0e48eff8088e67b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400260"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="48507-102">Propriedade do eixo filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48507-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="48507-103">Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.</span><span class="sxs-lookup"><span data-stu-id="48507-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48507-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48507-104">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="48507-105">Partes</span><span class="sxs-lookup"><span data-stu-id="48507-105">Parts</span></span>  
  
|<span data-ttu-id="48507-106">Termo</span><span class="sxs-lookup"><span data-stu-id="48507-106">Term</span></span>|<span data-ttu-id="48507-107">Definição</span><span class="sxs-lookup"><span data-stu-id="48507-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="48507-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="48507-108">Required.</span></span> <span data-ttu-id="48507-109">Um <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.</span><span class="sxs-lookup"><span data-stu-id="48507-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="48507-110">. <</span><span class="sxs-lookup"><span data-stu-id="48507-110">.<</span></span>|<span data-ttu-id="48507-111">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="48507-111">Required.</span></span> <span data-ttu-id="48507-112">Denota o início de uma propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="48507-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="48507-113">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="48507-113">Required.</span></span> <span data-ttu-id="48507-114">Nome dos nós filho a serem acessados, do formulário `[prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="48507-114">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="48507-115">-   `Prefix`Adicional.</span><span class="sxs-lookup"><span data-stu-id="48507-115">-   `Prefix` - Optional.</span></span> <span data-ttu-id="48507-116">Prefixo do namespace XML para o nó filho.</span><span class="sxs-lookup"><span data-stu-id="48507-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="48507-117">Deve ser um namespace XML global definido com uma `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="48507-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="48507-118">-   `Name`Necessária.</span><span class="sxs-lookup"><span data-stu-id="48507-118">-   `Name` - Required.</span></span> <span data-ttu-id="48507-119">Nome do nó filho local.</span><span class="sxs-lookup"><span data-stu-id="48507-119">Local child node name.</span></span> <span data-ttu-id="48507-120">Consulte [nomes de elementos e atributos XML declarados](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="48507-120">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="48507-121">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="48507-121">Required.</span></span> <span data-ttu-id="48507-122">Denota o final de uma propriedade do eixo filho.</span><span class="sxs-lookup"><span data-stu-id="48507-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="48507-123">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="48507-123">Return Value</span></span>  
 <span data-ttu-id="48507-124">Uma coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="48507-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48507-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="48507-125">Remarks</span></span>  
 <span data-ttu-id="48507-126">Você pode usar uma propriedade de eixo filho XML para acessar nós filho pelo nome de <xref:System.Xml.Linq.XElement> um <xref:System.Xml.Linq.XDocument> objeto ou ou de uma coleção de <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objetos ou.</span><span class="sxs-lookup"><span data-stu-id="48507-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="48507-127">Use a `Value` propriedade XML para acessar o valor do primeiro nó filho na coleção retornada.</span><span class="sxs-lookup"><span data-stu-id="48507-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="48507-128">Para obter mais informações, consulte [propriedade de valor XML](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="48507-128">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
 <span data-ttu-id="48507-129">O compilador Visual Basic converte Propriedades de eixo filho em chamadas para o <xref:System.Xml.Linq.XContainer.Elements%2A> método.</span><span class="sxs-lookup"><span data-stu-id="48507-129">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="48507-130">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="48507-130">XML Namespaces</span></span>  
 <span data-ttu-id="48507-131">O nome em uma propriedade de eixo filho pode usar somente os prefixos de namespace XML declarados globalmente com a `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="48507-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="48507-132">Ele não pode usar prefixos de namespace XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="48507-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="48507-133">Para obter mais informações, consulte [instrução Imports (namespace XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="48507-133">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48507-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48507-134">Example</span></span>  
 <span data-ttu-id="48507-135">O exemplo a seguir mostra como acessar os nós filho chamados `phone` a partir do `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="48507-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="48507-136">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="48507-136">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="48507-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48507-137">Example</span></span>  
 <span data-ttu-id="48507-138">O exemplo a seguir mostra como acessar os nós filho chamados `phone` da coleção retornada pela `contact` Propriedade eixo filho do `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="48507-138">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="48507-139">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="48507-139">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="48507-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48507-140">Example</span></span>  
 <span data-ttu-id="48507-141">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="48507-141">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="48507-142">Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="48507-142">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="48507-143">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="48507-143">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="48507-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="48507-144">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="48507-145">Propriedades do eixo XML</span><span class="sxs-lookup"><span data-stu-id="48507-145">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="48507-146">Literais XML</span><span class="sxs-lookup"><span data-stu-id="48507-146">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="48507-147">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48507-147">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="48507-148">Nomes de elementos e atributos XML declarados</span><span class="sxs-lookup"><span data-stu-id="48507-148">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
