---
title: Propriedade de eixo do atributo XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 896081c3dc7ca9e50b4dc4bd87675e957c34b649
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582156"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="e84e4-102">Propriedade de eixo do atributo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e84e4-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="e84e4-103">Fornece acesso ao valor de um atributo para um objeto <xref:System.Xml.Linq.XElement> ou para o primeiro elemento em uma coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e84e4-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e84e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e84e4-104">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="e84e4-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e84e4-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="e84e4-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e84e4-106">Required.</span></span> <span data-ttu-id="e84e4-107">Um objeto <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e84e4-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="e84e4-108">. @</span><span class="sxs-lookup"><span data-stu-id="e84e4-108">.@</span></span>  
 <span data-ttu-id="e84e4-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e84e4-109">Required.</span></span> <span data-ttu-id="e84e4-110">Denota o início de uma propriedade de eixo de atributo.</span><span class="sxs-lookup"><span data-stu-id="e84e4-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="e84e4-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e84e4-111">Optional.</span></span> <span data-ttu-id="e84e4-112">Indica o início do nome do atributo quando `attribute` não é um identificador válido no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e84e4-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="e84e4-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e84e4-113">Required.</span></span> <span data-ttu-id="e84e4-114">Nome do atributo a acessar, do formato [`prefix`:] `name`.</span><span class="sxs-lookup"><span data-stu-id="e84e4-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="e84e4-115">Parte</span><span class="sxs-lookup"><span data-stu-id="e84e4-115">Part</span></span>|<span data-ttu-id="e84e4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e84e4-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="e84e4-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e84e4-117">Optional.</span></span> <span data-ttu-id="e84e4-118">Prefixo do namespace XML para o atributo.</span><span class="sxs-lookup"><span data-stu-id="e84e4-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="e84e4-119">Deve ser um namespace XML global definido com uma instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="e84e4-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="e84e4-120">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e84e4-120">Required.</span></span> <span data-ttu-id="e84e4-121">Nome do atributo local.</span><span class="sxs-lookup"><span data-stu-id="e84e4-121">Local attribute name.</span></span> <span data-ttu-id="e84e4-122">Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e84e4-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="e84e4-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e84e4-123">Optional.</span></span> <span data-ttu-id="e84e4-124">Indica o final do nome do atributo quando `attribute` não é um identificador válido no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e84e4-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e84e4-125">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e84e4-125">Return Value</span></span>  
 <span data-ttu-id="e84e4-126">Uma cadeia de caracteres que contém o valor de `attribute`.</span><span class="sxs-lookup"><span data-stu-id="e84e4-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="e84e4-127">Se o nome do atributo não existir, `Nothing` será retornado.</span><span class="sxs-lookup"><span data-stu-id="e84e4-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e84e4-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="e84e4-128">Remarks</span></span>  
 <span data-ttu-id="e84e4-129">Você pode usar uma propriedade de eixo de atributo XML para acessar o valor de um atributo pelo nome de um objeto <xref:System.Xml.Linq.XElement> ou do primeiro elemento em uma coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e84e4-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e84e4-130">Você pode recuperar um valor de atributo por nome ou adicionar um novo atributo a um elemento especificando um novo nome precedido pelo identificador @.</span><span class="sxs-lookup"><span data-stu-id="e84e4-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="e84e4-131">Quando você faz referência a um atributo XML usando o identificador @, o valor do atributo é retornado como uma cadeia de caracteres e você não precisa especificar explicitamente a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="e84e4-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="e84e4-132">As regras de nomenclatura para atributos XML diferem das regras de nomenclatura para identificadores de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e84e4-132">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="e84e4-133">Para acessar um atributo XML que tem um nome que não é um identificador de Visual Basic válido, coloque o nome entre colchetes angulares (\< e >).</span><span class="sxs-lookup"><span data-stu-id="e84e4-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="e84e4-134">Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="e84e4-134">XML Namespaces</span></span>  
 <span data-ttu-id="e84e4-135">O nome em uma propriedade de eixo de atributo pode usar somente os prefixos de namespace XML declarados globalmente usando a instrução `Imports`.</span><span class="sxs-lookup"><span data-stu-id="e84e4-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="e84e4-136">Ele não pode usar prefixos de namespace XML declarados localmente em literais de elemento XML.</span><span class="sxs-lookup"><span data-stu-id="e84e4-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="e84e4-137">Para obter mais informações, consulte [instrução Imports (namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e84e4-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e84e4-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e84e4-138">Example</span></span>  
 <span data-ttu-id="e84e4-139">O exemplo a seguir mostra como obter os valores dos atributos XML chamados `type` de uma coleção de elementos XML que são nomeados `phone`.</span><span class="sxs-lookup"><span data-stu-id="e84e4-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="e84e4-140">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="e84e4-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="e84e4-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e84e4-141">Example</span></span>  
 <span data-ttu-id="e84e4-142">O exemplo a seguir mostra como criar atributos para um elemento XML de forma declarativa, como parte do XML, e dinamicamente adicionando um atributo a uma instância de um objeto <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e84e4-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="e84e4-143">O atributo `type` é criado declarativamente e o atributo `owner` é criado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="e84e4-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="e84e4-144">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="e84e4-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="e84e4-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e84e4-145">Example</span></span>  
 <span data-ttu-id="e84e4-146">O exemplo a seguir usa a sintaxe de colchete angular para obter o valor do atributo XML chamado `number-type`, que não é um identificador válido no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e84e4-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="e84e4-147">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="e84e4-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="e84e4-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e84e4-148">Example</span></span>  
 <span data-ttu-id="e84e4-149">O exemplo a seguir declara `ns` como um prefixo de namespace XML.</span><span class="sxs-lookup"><span data-stu-id="e84e4-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="e84e4-150">Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado "`ns:name`".</span><span class="sxs-lookup"><span data-stu-id="e84e4-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="e84e4-151">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="e84e4-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="e84e4-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e84e4-152">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="e84e4-153">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="e84e4-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="e84e4-154">Literais XML</span><span class="sxs-lookup"><span data-stu-id="e84e4-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="e84e4-155">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e84e4-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="e84e4-156">Nomes de Elementos e Atributos XML Declarados</span><span class="sxs-lookup"><span data-stu-id="e84e4-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
