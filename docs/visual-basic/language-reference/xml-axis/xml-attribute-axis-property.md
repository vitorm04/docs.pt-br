---
title: Propriedade de eixo de atributo XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
dev_langs:
- VB
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
ms.openlocfilehash: a3c327f4448287bcf6c45b9b6e26a1ef9ba13c16
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="b297d-102">Propriedade de eixo do atributo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b297d-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="b297d-103">Fornece acesso ao valor de um atributo para um <xref:System.Xml.Linq.XElement>objeto ou para o primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b297d-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b297d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b297d-104">Syntax</span></span>  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="b297d-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b297d-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="b297d-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b297d-106">Required.</span></span> <span data-ttu-id="b297d-107">Um <xref:System.Xml.Linq.XElement>objeto ou uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b297d-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="b297d-108">.@</span><span class="sxs-lookup"><span data-stu-id="b297d-108">.@</span></span>  
 <span data-ttu-id="b297d-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b297d-109">Required.</span></span> <span data-ttu-id="b297d-110">Indica o início de uma propriedade de eixo de atributo.</span><span class="sxs-lookup"><span data-stu-id="b297d-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="b297d-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b297d-111">Optional.</span></span> <span data-ttu-id="b297d-112">Indica o início do nome do atributo quando `attribute` não é um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="b297d-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 `attribute`  
 <span data-ttu-id="b297d-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b297d-113">Required.</span></span> <span data-ttu-id="b297d-114">Nome do atributo para acessar, do formulário [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="b297d-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="b297d-115">Parte</span><span class="sxs-lookup"><span data-stu-id="b297d-115">Part</span></span>|<span data-ttu-id="b297d-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b297d-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="b297d-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b297d-117">Optional.</span></span> <span data-ttu-id="b297d-118">Prefixo de namespace XML para o atributo.</span><span class="sxs-lookup"><span data-stu-id="b297d-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="b297d-119">Deve ser um namespace XML global definido com um `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="b297d-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="b297d-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b297d-120">Required.</span></span> <span data-ttu-id="b297d-121">Nome do atributo local.</span><span class="sxs-lookup"><span data-stu-id="b297d-121">Local attribute name.</span></span> <span data-ttu-id="b297d-122">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b297d-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="b297d-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b297d-123">Optional.</span></span> <span data-ttu-id="b297d-124">Indica o fim do nome do atributo quando `attribute` não é um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="b297d-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b297d-125">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b297d-125">Return Value</span></span>  
 <span data-ttu-id="b297d-126">Uma cadeia de caracteres que contém o valor de `attribute`.</span><span class="sxs-lookup"><span data-stu-id="b297d-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="b297d-127">Se não existir, o nome do atributo `Nothing` é retornado.</span><span class="sxs-lookup"><span data-stu-id="b297d-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b297d-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b297d-128">Remarks</span></span>  
 <span data-ttu-id="b297d-129">Você pode usar uma propriedade de eixo de atributo XML para acessar o valor de um atributo pelo nome de uma <xref:System.Xml.Linq.XElement>objeto ou do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b297d-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="b297d-130">Você pode recuperar um valor de atributo pelo nome, ou adicionar um novo atributo a um elemento, especificando um novo nome precedido de @ identificador.</span><span class="sxs-lookup"><span data-stu-id="b297d-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="b297d-131">Quando você se referir a um atributo XML usando o @ identificador, o valor do atributo é retornado como uma cadeia de caracteres e você não precisa especificar explicitamente o <xref:System.Xml.Linq.XAttribute.Value%2A>propriedade.</xref:System.Xml.Linq.XAttribute.Value%2A></span><span class="sxs-lookup"><span data-stu-id="b297d-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="b297d-132">As regras de nomeação para XML atributos diferem das regras de nomeação de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identificadores.</span><span class="sxs-lookup"><span data-stu-id="b297d-132">The naming rules for XML attributes differ from the naming rules for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identifiers.</span></span> <span data-ttu-id="b297d-133">Para acessar um atributo XML que tem um nome que não é um identificador válido Visual Basic, coloque o nome entre colchetes angulares (\< e >).</span><span class="sxs-lookup"><span data-stu-id="b297d-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="b297d-134">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="b297d-134">XML Namespaces</span></span>  
 <span data-ttu-id="b297d-135">O nome em uma propriedade de eixo de atributo pode usar somente prefixos de namespace XML declarados globalmente usando o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="b297d-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="b297d-136">Ele não é possível usar prefixos de namespace XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="b297d-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="b297d-137">Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b297d-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b297d-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b297d-138">Example</span></span>  
 <span data-ttu-id="b297d-139">O exemplo a seguir mostra como obter os valores dos atributos XML chamados `type` de uma coleção de elementos XML que são nomeados `phone`.</span><span class="sxs-lookup"><span data-stu-id="b297d-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 <span data-ttu-id="b297d-140">[!code-vb[VbXMLSamples&#12;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b297d-140">[!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="b297d-141">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="b297d-141">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="b297d-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b297d-142">Example</span></span>  
 <span data-ttu-id="b297d-143">O exemplo a seguir mostra como criar atributos para um elemento XML tanto declarativamente, como parte do XML e dinamicamente adicionando um atributo a uma instância de um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b297d-143">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="b297d-144">O `type` atributo é criado declarativamente e o `owne`r atributo é criado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="b297d-144">The `type` attribute is created declaratively and the `owne`r attribute is created dynamically.</span></span>  
  
 <span data-ttu-id="b297d-145">[!code-vb[VbXMLSamples&#44;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b297d-145">[!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="b297d-146">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="b297d-146">This code displays the following text:</span></span>  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="b297d-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b297d-147">Example</span></span>  
 <span data-ttu-id="b297d-148">O exemplo a seguir usa a sintaxe de colchete angular para obter o valor de atributo XML chamado `number-type`, que não é um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="b297d-148">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="b297d-149">[!code-vb[VbXMLSamples&13;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b297d-149">[!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]</span></span>  
  
 <span data-ttu-id="b297d-150">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="b297d-150">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="b297d-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b297d-151">Example</span></span>  
 <span data-ttu-id="b297d-152">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="b297d-152">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b297d-153">Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="b297d-153">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 <span data-ttu-id="b297d-154">[!code-vb[VbXMLSamples&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b297d-154">[!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]</span></span>  
  
 <span data-ttu-id="b297d-155">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="b297d-155">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="b297d-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b297d-156">See Also</span></span>  
 <span data-ttu-id="b297d-157"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b297d-157"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="b297d-158"> [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b297d-158"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="b297d-159"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="b297d-159"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="b297d-160"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b297d-160"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="b297d-161"> [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="b297d-161"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
