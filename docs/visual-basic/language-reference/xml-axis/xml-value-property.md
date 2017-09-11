---
title: Propriedade de valor XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionValue
dev_langs:
- VB
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
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
ms.openlocfilehash: f858b5a40485b25446b72ac45876e1d9d53caad7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="f986d-102">Propriedade do valor XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f986d-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="f986d-103">Fornece acesso ao valor do primeiro elemento de uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f986d-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f986d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f986d-104">Syntax</span></span>  
  
```  
  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="f986d-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f986d-105">Parts</span></span>  
  
|<span data-ttu-id="f986d-106">Termo</span><span class="sxs-lookup"><span data-stu-id="f986d-106">Term</span></span>|<span data-ttu-id="f986d-107">Definição</span><span class="sxs-lookup"><span data-stu-id="f986d-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="f986d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f986d-108">Required.</span></span> <span data-ttu-id="f986d-109">Coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f986d-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f986d-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f986d-110">Return Value</span></span>  
 <span data-ttu-id="f986d-111">A `String` que contém o valor do primeiro elemento da coleção, ou `Nothing` se a coleção estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="f986d-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f986d-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f986d-112">Remarks</span></span>  
 <span data-ttu-id="f986d-113">O <xref:System.Xml.Linq.XElement.Value%2A>propriedade torna mais fácil acessar o valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="f986d-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f986d-114">Essa propriedade primeiro verifica se a coleção contém pelo menos um objeto.</span><span class="sxs-lookup"><span data-stu-id="f986d-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="f986d-115">Se a coleção está vazia, essa propriedade retornará `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="f986d-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="f986d-116">Caso contrário, essa propriedade retorna o valor de <xref:System.Xml.Linq.XElement.Value%2A>propriedade do primeiro elemento na coleção.</xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="f986d-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f986d-117">Quando você acessa o valor de um atributo XML usando o ' @' identificador, o valor do atributo é retornado como um `String` e você não precisa especificar explicitamente o <xref:System.Xml.Linq.XAttribute.Value%2A>propriedade.</xref:System.Xml.Linq.XAttribute.Value%2A></span><span class="sxs-lookup"><span data-stu-id="f986d-117">When you access the value of an XML attribute using the '@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="f986d-118">Para acessar outros elementos em uma coleção, você pode usar a propriedade do indexador de extensão XML.</span><span class="sxs-lookup"><span data-stu-id="f986d-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="f986d-119">Para obter mais informações, consulte [propriedade do indexador de extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="f986d-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="f986d-120">Herança</span><span class="sxs-lookup"><span data-stu-id="f986d-120">Inheritance</span></span>  
 <span data-ttu-id="f986d-121">A maioria dos usuários não precisará implementar <xref:System.Collections.Generic.IEnumerable%601>e, portanto, pode ignorar esta seção.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="f986d-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="f986d-122">O <xref:System.Xml.Linq.XElement.Value%2A>propriedade é uma propriedade de extensão para tipos que implementam `IEnumerable(Of XElement)`.</xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="f986d-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="f986d-123">A vinculação da propriedade extensão é como a associação de métodos de extensão: se um tipo implementa uma das interfaces e define uma propriedade que tem o nome "Valor", essa propriedade tem precedência sobre a propriedade de extensão.</span><span class="sxs-lookup"><span data-stu-id="f986d-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="f986d-124">Em outras palavras, isso <xref:System.Xml.Linq.XElement.Value%2A>propriedade pode ser substituída ao definir uma nova propriedade em uma classe que implementa `IEnumerable(Of XElement)`.</xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="f986d-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f986d-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f986d-125">Example</span></span>  
 <span data-ttu-id="f986d-126">O exemplo a seguir mostra como usar o <xref:System.Xml.Linq.XElement.Value%2A>propriedade para acessar o primeiro nó em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="f986d-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f986d-127">O exemplo usa a propriedade do eixo filho para obter a coleção de todos os nós filho chamados `phone` que estão na `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="f986d-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 <span data-ttu-id="f986d-128">[!code-vb[VbXMLSamples&#15;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f986d-128">[!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]</span></span>  
  
 <span data-ttu-id="f986d-129">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="f986d-129">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="f986d-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f986d-130">Example</span></span>  
 <span data-ttu-id="f986d-131">O exemplo a seguir mostra como obter o valor de um atributo XML de uma coleção de <xref:System.Xml.Linq.XAttribute>objetos.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="f986d-131">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="f986d-132">O exemplo usa a propriedade de eixo de atributo para exibir o valor da `type` atributo para todos os o `phone` elementos.</span><span class="sxs-lookup"><span data-stu-id="f986d-132">The example uses the attribute axis property to display the value of the `type` attribute for all of the the `phone` elements.</span></span>  
  
 <span data-ttu-id="f986d-133">[!code-vb[VbXMLSamples n º&16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f986d-133">[!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]</span></span>  
  
 <span data-ttu-id="f986d-134">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="f986d-134">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="f986d-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f986d-135">See Also</span></span>  
 <span data-ttu-id="f986d-136"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f986d-136"><xref:System.Xml.Linq.XElement></span></span>   
 <span data-ttu-id="f986d-137"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="f986d-137"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="f986d-138"> [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f986d-138"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="f986d-139"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="f986d-139"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="f986d-140"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f986d-140"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="f986d-141"> [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="f986d-141"> [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span></span>  
<span data-ttu-id="f986d-142"> [Propriedade do indexador de extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md) </span><span class="sxs-lookup"><span data-stu-id="f986d-142"> [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md) </span></span>  
<span data-ttu-id="f986d-143"> [Propriedade de eixo filho XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="f986d-143"> [XML Child Axis Property](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span></span>  
<span data-ttu-id="f986d-144"> [Propriedade de Eixo do Atributo XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)</span><span class="sxs-lookup"><span data-stu-id="f986d-144"> [XML Attribute Axis Property](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)</span></span>
