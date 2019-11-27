---
title: Propriedade do valor XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 571d9130ef69df580bbba5d90bc8758b4b627196
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349416"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="63c74-102">Propriedade do valor XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63c74-102">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="63c74-103">Fornece acesso ao valor do primeiro elemento de uma coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="63c74-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="63c74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63c74-104">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="63c74-105">Partes</span><span class="sxs-lookup"><span data-stu-id="63c74-105">Parts</span></span>

|<span data-ttu-id="63c74-106">Termo</span><span class="sxs-lookup"><span data-stu-id="63c74-106">Term</span></span>|<span data-ttu-id="63c74-107">Definição</span><span class="sxs-lookup"><span data-stu-id="63c74-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="63c74-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="63c74-108">Required.</span></span> <span data-ttu-id="63c74-109">Coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="63c74-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="63c74-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="63c74-110">Return Value</span></span>

 <span data-ttu-id="63c74-111">Um `String` que contém o valor do primeiro elemento da coleção ou `Nothing` se a coleção estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="63c74-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="63c74-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="63c74-112">Remarks</span></span>

 <span data-ttu-id="63c74-113">A propriedade <xref:System.Xml.Linq.XElement.Value%2A> torna fácil acessar o valor do primeiro elemento em uma coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="63c74-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="63c74-114">Essa propriedade verifica primeiro se a coleção contém pelo menos um objeto.</span><span class="sxs-lookup"><span data-stu-id="63c74-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="63c74-115">Se a coleção estiver vazia, essa propriedade retornará `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="63c74-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="63c74-116">Caso contrário, essa propriedade retornará o valor da propriedade <xref:System.Xml.Linq.XElement.Value%2A> do primeiro elemento na coleção.</span><span class="sxs-lookup"><span data-stu-id="63c74-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="63c74-117">Quando você acessa o valor de um atributo XML usando o identificador '\@', o valor do atributo é retornado como um `String` e você não precisa especificar explicitamente a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="63c74-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="63c74-118">Para acessar outros elementos em uma coleção, você pode usar a propriedade do indexador de extensão XML.</span><span class="sxs-lookup"><span data-stu-id="63c74-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="63c74-119">Para obter mais informações, consulte [Propriedade do indexador de extensão](extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="63c74-119">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="63c74-120">{1&gt;Herança&lt;1}</span><span class="sxs-lookup"><span data-stu-id="63c74-120">Inheritance</span></span>

 <span data-ttu-id="63c74-121">A maioria dos usuários não precisará implementar <xref:System.Collections.Generic.IEnumerable%601>e, portanto, pode ignorar esta seção.</span><span class="sxs-lookup"><span data-stu-id="63c74-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="63c74-122">A propriedade <xref:System.Xml.Linq.XElement.Value%2A> é uma propriedade de extensão para tipos que implementam `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="63c74-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="63c74-123">A associação dessa propriedade de extensão é como a associação de métodos de extensão: se um tipo implementar uma das interfaces e definir uma propriedade com o nome "valor", essa propriedade terá precedência sobre a propriedade de extensão.</span><span class="sxs-lookup"><span data-stu-id="63c74-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="63c74-124">Em outras palavras, essa propriedade <xref:System.Xml.Linq.XElement.Value%2A> pode ser substituída definindo-se uma nova propriedade em uma classe que implementa `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="63c74-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="63c74-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63c74-125">Example</span></span>

 <span data-ttu-id="63c74-126">O exemplo a seguir mostra como usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A> para acessar o primeiro nó em uma coleção de objetos <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="63c74-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="63c74-127">O exemplo usa a propriedade do eixo filho para obter a coleção de todos os nós filho chamados `phone` que estão no objeto `contact`.</span><span class="sxs-lookup"><span data-stu-id="63c74-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="63c74-128">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="63c74-128">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="63c74-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63c74-129">Example</span></span>

 <span data-ttu-id="63c74-130">O exemplo a seguir mostra como obter o valor de um atributo XML de uma coleção de objetos <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="63c74-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="63c74-131">O exemplo usa a Propriedade Axis de atributo para exibir o valor do atributo `type` para todos os elementos `phone`.</span><span class="sxs-lookup"><span data-stu-id="63c74-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="63c74-132">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="63c74-132">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="63c74-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63c74-133">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="63c74-134">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="63c74-134">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="63c74-135">Literais XML</span><span class="sxs-lookup"><span data-stu-id="63c74-135">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="63c74-136">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63c74-136">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="63c74-137">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="63c74-137">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="63c74-138">Propriedade do Indexador de Extensão</span><span class="sxs-lookup"><span data-stu-id="63c74-138">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="63c74-139">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="63c74-139">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="63c74-140">Propriedade de Eixo do Atributo XML</span><span class="sxs-lookup"><span data-stu-id="63c74-140">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
