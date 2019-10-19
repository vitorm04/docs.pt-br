---
title: Propriedade do indexador de extensão (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 660cebadc78d260350f2849f7f4926f9cef7c8d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582191"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="5afe9-102">Propriedade do indexador de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5afe9-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="5afe9-103">Fornece acesso aos elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="5afe9-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5afe9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5afe9-104">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="5afe9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5afe9-105">Parts</span></span>  
  
|<span data-ttu-id="5afe9-106">Termo</span><span class="sxs-lookup"><span data-stu-id="5afe9-106">Term</span></span>|<span data-ttu-id="5afe9-107">Definição</span><span class="sxs-lookup"><span data-stu-id="5afe9-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="5afe9-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5afe9-108">Required.</span></span> <span data-ttu-id="5afe9-109">Uma coleção passível de consulta.</span><span class="sxs-lookup"><span data-stu-id="5afe9-109">A queryable collection.</span></span> <span data-ttu-id="5afe9-110">Ou seja, uma coleção que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="5afe9-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="5afe9-111">(</span><span class="sxs-lookup"><span data-stu-id="5afe9-111">(</span></span>|<span data-ttu-id="5afe9-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5afe9-112">Required.</span></span> <span data-ttu-id="5afe9-113">Denota o início da Propriedade do indexador.</span><span class="sxs-lookup"><span data-stu-id="5afe9-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="5afe9-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5afe9-114">Required.</span></span> <span data-ttu-id="5afe9-115">Uma expressão de inteiro que especifica a posição de base zero de um elemento da coleção.</span><span class="sxs-lookup"><span data-stu-id="5afe9-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="5afe9-116">)</span><span class="sxs-lookup"><span data-stu-id="5afe9-116">)</span></span>|<span data-ttu-id="5afe9-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5afe9-117">Required.</span></span> <span data-ttu-id="5afe9-118">Denota o final da Propriedade do indexador.</span><span class="sxs-lookup"><span data-stu-id="5afe9-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="5afe9-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5afe9-119">Return Value</span></span>  
 <span data-ttu-id="5afe9-120">O objeto do local especificado na coleção ou `Nothing` se o índice está fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="5afe9-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5afe9-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="5afe9-121">Remarks</span></span>  
 <span data-ttu-id="5afe9-122">Você pode usar a propriedade do indexador de extensão para acessar elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="5afe9-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="5afe9-123">Essa propriedade do indexador normalmente é usada na saída das propriedades do eixo XML.</span><span class="sxs-lookup"><span data-stu-id="5afe9-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="5afe9-124">As propriedades do eixo XML filho e do XML descendente retornam coleções de objetos <xref:System.Xml.Linq.XElement> ou um valor de atributo.</span><span class="sxs-lookup"><span data-stu-id="5afe9-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="5afe9-125">O compilador Visual Basic converte Propriedades do indexador de extensão em chamadas para o método `ElementAtOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="5afe9-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="5afe9-126">Ao contrário de um indexador de matriz, o método `ElementAtOrDefault` retornará `Nothing` se o índice estiver fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="5afe9-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="5afe9-127">Esse comportamento é útil quando você não pode determinar facilmente o número de elementos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="5afe9-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="5afe9-128">Essa propriedade do indexador é como uma propriedade de extensão para coleções que implementam <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>: ela será usada somente se a coleção não tiver um indexador ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="5afe9-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="5afe9-129">Para acessar o valor do primeiro elemento em uma coleção de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, você pode usar a propriedade XML `Value`.</span><span class="sxs-lookup"><span data-stu-id="5afe9-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="5afe9-130">Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="5afe9-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5afe9-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5afe9-131">Example</span></span>  
 <span data-ttu-id="5afe9-132">O exemplo a seguir mostra como usar o indexador de extensão para acessar o segundo nó filho em uma coleção de objetos de <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5afe9-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="5afe9-133">A coleção é acessada usando a propriedade do eixo filho, que obtém todos os elementos filho chamados `phone` no objeto `contact`.</span><span class="sxs-lookup"><span data-stu-id="5afe9-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="5afe9-134">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="5afe9-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="5afe9-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5afe9-135">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="5afe9-136">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="5afe9-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="5afe9-137">Literais XML</span><span class="sxs-lookup"><span data-stu-id="5afe9-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="5afe9-138">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5afe9-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="5afe9-139">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="5afe9-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
