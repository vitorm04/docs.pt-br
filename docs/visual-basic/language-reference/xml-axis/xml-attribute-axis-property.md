---
title: Propriedade de eixo do atributo XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a286c70f57128d0406b3a300610fea5e1c44b32d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="5a5b2-102">Propriedade de eixo do atributo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a5b2-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="5a5b2-103">Fornece acesso ao valor de um atributo para um <xref:System.Xml.Linq.XElement> objeto ou para o primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a5b2-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="5a5b2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5a5b2-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="5a5b2-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-106">Required.</span></span> <span data-ttu-id="5a5b2-107">Um <xref:System.Xml.Linq.XElement> objeto ou uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="5a5b2-108">.@</span><span class="sxs-lookup"><span data-stu-id="5a5b2-108">.@</span></span>  
 <span data-ttu-id="5a5b2-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-109">Required.</span></span> <span data-ttu-id="5a5b2-110">Indica o início de uma propriedade de eixo de atributo.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="5a5b2-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-111">Optional.</span></span> <span data-ttu-id="5a5b2-112">Indica o início do nome do atributo quando `attribute` não é um identificador válido no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a5b2-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 `attribute`  
 <span data-ttu-id="5a5b2-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-113">Required.</span></span> <span data-ttu-id="5a5b2-114">Nome do atributo para acessar, no formato [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="5a5b2-115">Parte</span><span class="sxs-lookup"><span data-stu-id="5a5b2-115">Part</span></span>|<span data-ttu-id="5a5b2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a5b2-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="5a5b2-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-117">Optional.</span></span> <span data-ttu-id="5a5b2-118">Prefixo de namespace XML para o atributo.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="5a5b2-119">Deve ser um namespace XML global definido com um `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="5a5b2-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-120">Required.</span></span> <span data-ttu-id="5a5b2-121">Nome do atributo local.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-121">Local attribute name.</span></span> <span data-ttu-id="5a5b2-122">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5a5b2-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="5a5b2-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-123">Optional.</span></span> <span data-ttu-id="5a5b2-124">Indica o início do nome do atributo quando `attribute` não é um identificador válido no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a5b2-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a5b2-125">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5a5b2-125">Return Value</span></span>  
 <span data-ttu-id="5a5b2-126">Uma cadeia de caracteres que contém o valor de `attribute`.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="5a5b2-127">Se não existir, o nome do atributo `Nothing` é retornado.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a5b2-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a5b2-128">Remarks</span></span>  
 <span data-ttu-id="5a5b2-129">Você pode usar uma propriedade de eixo de atributo XML para acessar o valor de um atributo pelo nome de um <xref:System.Xml.Linq.XElement> objeto ou a partir do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="5a5b2-130">Você pode recuperar um valor de atributo por nome ou adicionar um novo atributo para um elemento especificando um novo nome precedido de @ identificador.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="5a5b2-131">Quando você se referir a um atributo XML usando o @ identificador, o valor do atributo é retornado como uma cadeia de caracteres e você não precisa especificar explicitamente o <xref:System.Xml.Linq.XAttribute.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="5a5b2-132">As regras de nomenclatura para atributos XML são diferentes das regras de nomeação para [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] identificadores.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-132">The naming rules for XML attributes differ from the naming rules for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] identifiers.</span></span> <span data-ttu-id="5a5b2-133">Para acessar um atributo XML que tem um nome que não é um identificador válido do Visual Basic, coloque o nome entre colchetes angulares (\< e >).</span><span class="sxs-lookup"><span data-stu-id="5a5b2-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5a5b2-134">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="5a5b2-134">XML Namespaces</span></span>  
 <span data-ttu-id="5a5b2-135">O nome em uma propriedade de eixo de atributo pode usar somente prefixos de namespace XML declarados globalmente usando o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="5a5b2-136">Ele não é possível usar prefixos de namespace XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="5a5b2-137">Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5a5b2-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5b2-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5b2-138">Example</span></span>  
 <span data-ttu-id="5a5b2-139">O exemplo a seguir mostra como obter os valores dos atributos XML chamados `type` de uma coleção de elementos XML que são nomeados `phone`.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 <span data-ttu-id="5a5b2-140">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5a5b2-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="5a5b2-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5b2-141">Example</span></span>  
 <span data-ttu-id="5a5b2-142">O exemplo a seguir mostra como criar atributos para um elemento XML tanto declarativamente, como parte do XML e dinamicamente adicionando um atributo a uma instância de um <xref:System.Xml.Linq.XElement> objeto.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="5a5b2-143">O `type` atributo é criado declarativamente e `owner` atributo é criado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 <span data-ttu-id="5a5b2-144">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5a5b2-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="5a5b2-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5b2-145">Example</span></span>  
 <span data-ttu-id="5a5b2-146">O exemplo a seguir usa a sintaxe colchete angular para obter o valor do atributo XML chamado `number-type`, que não é um identificador válido no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a5b2-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 <span data-ttu-id="5a5b2-147">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5a5b2-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="5a5b2-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5b2-148">Example</span></span>  
 <span data-ttu-id="5a5b2-149">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="5a5b2-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5a5b2-150">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="5a5b2-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 <span data-ttu-id="5a5b2-151">Este código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5a5b2-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="5a5b2-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a5b2-152">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="5a5b2-153">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="5a5b2-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="5a5b2-154">Literais XML</span><span class="sxs-lookup"><span data-stu-id="5a5b2-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="5a5b2-155">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a5b2-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="5a5b2-156">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="5a5b2-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
