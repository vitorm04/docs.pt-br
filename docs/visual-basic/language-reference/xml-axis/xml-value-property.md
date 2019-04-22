---
title: Propriedade do valor XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 1c7aa1cc32bc1c5ef637f7a606db7e695f1dfaee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821941"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="fffc6-102">Propriedade do valor XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fffc6-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="fffc6-103">Fornece acesso ao valor do primeiro elemento de uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="fffc6-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fffc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fffc6-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="fffc6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="fffc6-105">Parts</span></span>  
  
|<span data-ttu-id="fffc6-106">Termo</span><span class="sxs-lookup"><span data-stu-id="fffc6-106">Term</span></span>|<span data-ttu-id="fffc6-107">Definição</span><span class="sxs-lookup"><span data-stu-id="fffc6-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="fffc6-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fffc6-108">Required.</span></span> <span data-ttu-id="fffc6-109">Coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="fffc6-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="fffc6-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fffc6-110">Return Value</span></span>  
 <span data-ttu-id="fffc6-111">Um `String` que contém o valor do primeiro elemento da coleção, ou `Nothing` se a coleção está vazia.</span><span class="sxs-lookup"><span data-stu-id="fffc6-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fffc6-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="fffc6-112">Remarks</span></span>  
 <span data-ttu-id="fffc6-113">O <xref:System.Xml.Linq.XElement.Value%2A> propriedade torna mais fácil acessar o valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="fffc6-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="fffc6-114">Essa propriedade primeiro verifica se a coleção contém pelo menos um objeto.</span><span class="sxs-lookup"><span data-stu-id="fffc6-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="fffc6-115">Se a coleção está vazia, essa propriedade retornará `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fffc6-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="fffc6-116">Caso contrário, essa propriedade retorna o valor da <xref:System.Xml.Linq.XElement.Value%2A> propriedade do primeiro elemento na coleção.</span><span class="sxs-lookup"><span data-stu-id="fffc6-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fffc6-117">Quando você acessa o valor de um atributo XML usando o '\@' identificador, o valor do atributo é retornado como um `String` e você não precisa especificar explicitamente o <xref:System.Xml.Linq.XAttribute.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fffc6-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="fffc6-118">Para acessar outros elementos em uma coleção, você pode usar a propriedade do indexador de extensão XML.</span><span class="sxs-lookup"><span data-stu-id="fffc6-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="fffc6-119">Para obter mais informações, consulte [propriedade do indexador de extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="fffc6-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="fffc6-120">Herança</span><span class="sxs-lookup"><span data-stu-id="fffc6-120">Inheritance</span></span>  
 <span data-ttu-id="fffc6-121">A maioria dos usuários não precisará implementar <xref:System.Collections.Generic.IEnumerable%601>e, portanto, pode ignorar esta seção.</span><span class="sxs-lookup"><span data-stu-id="fffc6-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="fffc6-122">O <xref:System.Xml.Linq.XElement.Value%2A> propriedade é uma propriedade de extensão para tipos que implementam `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="fffc6-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="fffc6-123">A associação dessa propriedade de extensão é como a associação de métodos de extensão: se um tipo implementa uma das interfaces e define uma propriedade que tem o nome "Valor", essa propriedade tem precedência sobre a propriedade de extensão.</span><span class="sxs-lookup"><span data-stu-id="fffc6-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="fffc6-124">Em outras palavras, isso <xref:System.Xml.Linq.XElement.Value%2A> propriedade pode ser substituída, definindo uma nova propriedade em uma classe que implementa `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="fffc6-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fffc6-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fffc6-125">Example</span></span>  
 <span data-ttu-id="fffc6-126">O exemplo a seguir mostra como usar o <xref:System.Xml.Linq.XElement.Value%2A> propriedade para acessar o primeiro nó em uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="fffc6-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="fffc6-127">O exemplo usa a propriedade de eixo filho para obter a coleção de todos os nós filho denominado `phone` que estão no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="fffc6-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 <span data-ttu-id="fffc6-128">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="fffc6-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="fffc6-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fffc6-129">Example</span></span>  
 <span data-ttu-id="fffc6-130">O exemplo a seguir mostra como obter o valor de um atributo XML de uma coleção de <xref:System.Xml.Linq.XAttribute> objetos.</span><span class="sxs-lookup"><span data-stu-id="fffc6-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="fffc6-131">O exemplo usa a propriedade de eixo de atributo para exibir o valor da `type` atributo para todos os `phone` elementos.</span><span class="sxs-lookup"><span data-stu-id="fffc6-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 <span data-ttu-id="fffc6-132">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="fffc6-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="fffc6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fffc6-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="fffc6-134">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="fffc6-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="fffc6-135">Literais XML</span><span class="sxs-lookup"><span data-stu-id="fffc6-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="fffc6-136">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fffc6-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="fffc6-137">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="fffc6-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="fffc6-138">Propriedade do Indexador de Extensão</span><span class="sxs-lookup"><span data-stu-id="fffc6-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [<span data-ttu-id="fffc6-139">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="fffc6-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="fffc6-140">Propriedade de Eixo do Atributo XML</span><span class="sxs-lookup"><span data-stu-id="fffc6-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
