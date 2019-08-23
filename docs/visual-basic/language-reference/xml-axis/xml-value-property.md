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
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942987"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="1764f-102">Propriedade do valor XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1764f-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="1764f-103">Fornece acesso ao valor do primeiro elemento de uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="1764f-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1764f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1764f-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="1764f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1764f-105">Parts</span></span>  
  
|<span data-ttu-id="1764f-106">Termo</span><span class="sxs-lookup"><span data-stu-id="1764f-106">Term</span></span>|<span data-ttu-id="1764f-107">Definição</span><span class="sxs-lookup"><span data-stu-id="1764f-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="1764f-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1764f-108">Required.</span></span> <span data-ttu-id="1764f-109">Coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1764f-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="1764f-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1764f-110">Return Value</span></span>  
 <span data-ttu-id="1764f-111">Uma `String` que contém o valor do primeiro elemento da coleção ou `Nothing` se a coleção estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="1764f-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1764f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1764f-112">Remarks</span></span>  
 <span data-ttu-id="1764f-113">A <xref:System.Xml.Linq.XElement.Value%2A> Propriedade facilita o acesso ao valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="1764f-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="1764f-114">Essa propriedade verifica primeiro se a coleção contém pelo menos um objeto.</span><span class="sxs-lookup"><span data-stu-id="1764f-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="1764f-115">Se a coleção estiver vazia, essa propriedade retornará `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1764f-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="1764f-116">Caso contrário, essa propriedade retornará o valor da <xref:System.Xml.Linq.XElement.Value%2A> Propriedade do primeiro elemento na coleção.</span><span class="sxs-lookup"><span data-stu-id="1764f-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1764f-117">Quando você acessa o valor de um atributo XML usando o identificador\@' ', o valor do atributo é retornado como `String` um e você não precisa especificar explicitamente a <xref:System.Xml.Linq.XAttribute.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1764f-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="1764f-118">Para acessar outros elementos em uma coleção, você pode usar a propriedade do indexador de extensão XML.</span><span class="sxs-lookup"><span data-stu-id="1764f-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="1764f-119">Para obter mais informações, consulte Propriedade do indexador de [extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="1764f-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="1764f-120">Herança</span><span class="sxs-lookup"><span data-stu-id="1764f-120">Inheritance</span></span>  
 <span data-ttu-id="1764f-121">A maioria dos usuários não precisará <xref:System.Collections.Generic.IEnumerable%601>implementar e, portanto, pode ignorar esta seção.</span><span class="sxs-lookup"><span data-stu-id="1764f-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="1764f-122">A <xref:System.Xml.Linq.XElement.Value%2A> propriedade é uma propriedade de extensão para tipos que `IEnumerable(Of XElement)`implementam.</span><span class="sxs-lookup"><span data-stu-id="1764f-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="1764f-123">A associação dessa propriedade de extensão é como a associação de métodos de extensão: se um tipo implementar uma das interfaces e definir uma propriedade com o nome "valor", essa propriedade terá precedência sobre a propriedade de extensão.</span><span class="sxs-lookup"><span data-stu-id="1764f-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="1764f-124">Em outras palavras, essa <xref:System.Xml.Linq.XElement.Value%2A> propriedade pode ser substituída definindo-se uma nova propriedade em uma classe `IEnumerable(Of XElement)`que implementa.</span><span class="sxs-lookup"><span data-stu-id="1764f-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1764f-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1764f-125">Example</span></span>  
 <span data-ttu-id="1764f-126">O exemplo a seguir mostra como usar a <xref:System.Xml.Linq.XElement.Value%2A> propriedade para acessar o primeiro nó em uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="1764f-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="1764f-127">O exemplo usa a propriedade do eixo filho para obter a coleção de todos os nós `phone` filho chamados que estão `contact` no objeto.</span><span class="sxs-lookup"><span data-stu-id="1764f-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 <span data-ttu-id="1764f-128">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="1764f-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="1764f-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1764f-129">Example</span></span>  
 <span data-ttu-id="1764f-130">O exemplo a seguir mostra como obter o valor de um atributo XML de uma coleção de <xref:System.Xml.Linq.XAttribute> objetos.</span><span class="sxs-lookup"><span data-stu-id="1764f-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="1764f-131">O exemplo usa a Propriedade Axis do atributo para exibir o valor do `type` atributo para todos `phone` os elementos.</span><span class="sxs-lookup"><span data-stu-id="1764f-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 <span data-ttu-id="1764f-132">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="1764f-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="1764f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1764f-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="1764f-134">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="1764f-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="1764f-135">Literais XML</span><span class="sxs-lookup"><span data-stu-id="1764f-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="1764f-136">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1764f-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="1764f-137">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="1764f-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="1764f-138">Propriedade do Indexador de Extensão</span><span class="sxs-lookup"><span data-stu-id="1764f-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [<span data-ttu-id="1764f-139">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="1764f-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="1764f-140">Propriedade de Eixo do Atributo XML</span><span class="sxs-lookup"><span data-stu-id="1764f-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
