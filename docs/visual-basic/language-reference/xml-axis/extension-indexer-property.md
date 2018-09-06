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
ms.openlocfilehash: ab9eacc3fb3796139d8ed8382146a4a6c2b28a97
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736614"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="0bc97-102">Propriedade do indexador de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bc97-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="0bc97-103">Fornece acesso aos elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0bc97-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bc97-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="0bc97-105">Partes</span><span class="sxs-lookup"><span data-stu-id="0bc97-105">Parts</span></span>  
  
|<span data-ttu-id="0bc97-106">Termo</span><span class="sxs-lookup"><span data-stu-id="0bc97-106">Term</span></span>|<span data-ttu-id="0bc97-107">Definição</span><span class="sxs-lookup"><span data-stu-id="0bc97-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="0bc97-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0bc97-108">Required.</span></span> <span data-ttu-id="0bc97-109">Uma coleção passível de consulta.</span><span class="sxs-lookup"><span data-stu-id="0bc97-109">A queryable collection.</span></span> <span data-ttu-id="0bc97-110">Ou seja, uma coleção que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="0bc97-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="0bc97-111">(</span><span class="sxs-lookup"><span data-stu-id="0bc97-111">(</span></span>|<span data-ttu-id="0bc97-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0bc97-112">Required.</span></span> <span data-ttu-id="0bc97-113">Indica o início da propriedade do indexador.</span><span class="sxs-lookup"><span data-stu-id="0bc97-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="0bc97-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0bc97-114">Required.</span></span> <span data-ttu-id="0bc97-115">Uma expressão de inteiro que especifica a posição de base zero de um elemento da coleção.</span><span class="sxs-lookup"><span data-stu-id="0bc97-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="0bc97-116">)</span><span class="sxs-lookup"><span data-stu-id="0bc97-116">)</span></span>|<span data-ttu-id="0bc97-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0bc97-117">Required.</span></span> <span data-ttu-id="0bc97-118">Indica o fim da propriedade do indexador.</span><span class="sxs-lookup"><span data-stu-id="0bc97-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="0bc97-119">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0bc97-119">Return Value</span></span>  
 <span data-ttu-id="0bc97-120">O objeto do local especificado na coleção, ou `Nothing` se o índice está fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="0bc97-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bc97-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="0bc97-121">Remarks</span></span>  
 <span data-ttu-id="0bc97-122">Você pode usar a propriedade do indexador de extensão para acessar elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0bc97-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="0bc97-123">Essa propriedade do indexador normalmente é usada na saída das propriedades do eixo XML.</span><span class="sxs-lookup"><span data-stu-id="0bc97-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="0bc97-124">O filho do XML e propriedades de eixo descendente XML retornam coleções de <xref:System.Xml.Linq.XElement> objetos ou um valor de atributo.</span><span class="sxs-lookup"><span data-stu-id="0bc97-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="0bc97-125">O compilador do Visual Basic converte as propriedades do indexador de extensão em chamadas para o `ElementAtOrDefault` método.</span><span class="sxs-lookup"><span data-stu-id="0bc97-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="0bc97-126">Ao contrário de um indexador de matriz, o `ElementAtOrDefault` método retorna `Nothing` se o índice está fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="0bc97-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="0bc97-127">Esse comportamento é útil quando você não pode determinar facilmente o número de elementos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="0bc97-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="0bc97-128">Esta propriedade do indexador é como uma propriedade de extensão para coleções que implementam <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>: ele é usado somente se a coleção não tem um indexador ou uma propriedade padrão.</span><span class="sxs-lookup"><span data-stu-id="0bc97-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="0bc97-129">Para acessar o valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> objetos, você pode usar o XML `Value` propriedade.</span><span class="sxs-lookup"><span data-stu-id="0bc97-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="0bc97-130">Para obter mais informações, consulte [propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="0bc97-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bc97-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0bc97-131">Example</span></span>  
 <span data-ttu-id="0bc97-132">O exemplo a seguir mostra como usar o indexador de extensão para acessar o segundo nó filho em uma coleção de <xref:System.Xml.Linq.XElement> objetos.</span><span class="sxs-lookup"><span data-stu-id="0bc97-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="0bc97-133">A coleção é acessada usando a propriedade de eixo filho, que obtém todos os elementos filho chamados `phone` no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="0bc97-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 <span data-ttu-id="0bc97-134">Esse código exibe o texto a seguir:</span><span class="sxs-lookup"><span data-stu-id="0bc97-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="0bc97-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bc97-135">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="0bc97-136">Propriedades do Eixo XML</span><span class="sxs-lookup"><span data-stu-id="0bc97-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="0bc97-137">Literais XML</span><span class="sxs-lookup"><span data-stu-id="0bc97-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="0bc97-138">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0bc97-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="0bc97-139">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="0bc97-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
