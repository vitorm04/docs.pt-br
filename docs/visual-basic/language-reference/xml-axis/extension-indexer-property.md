---
title: "Propriedade do indexador de extensão (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionIndexer
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
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
ms.openlocfilehash: 71c16d3f1b93647154bdead4a85d1117b5f6c463
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="55d81-102">Propriedade do indexador de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55d81-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="55d81-103">Fornece acesso aos elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="55d81-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55d81-104">Syntax</span></span>  
  
```  
  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="55d81-105">Partes</span><span class="sxs-lookup"><span data-stu-id="55d81-105">Parts</span></span>  
  
|<span data-ttu-id="55d81-106">Termo</span><span class="sxs-lookup"><span data-stu-id="55d81-106">Term</span></span>|<span data-ttu-id="55d81-107">Definição</span><span class="sxs-lookup"><span data-stu-id="55d81-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="55d81-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="55d81-108">Required.</span></span> <span data-ttu-id="55d81-109">Uma coleção consultável.</span><span class="sxs-lookup"><span data-stu-id="55d81-109">A queryable collection.</span></span> <span data-ttu-id="55d81-110">Ou seja, uma coleção que implementa <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="55d81-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="55d81-111">(</span><span class="sxs-lookup"><span data-stu-id="55d81-111">(</span></span>|<span data-ttu-id="55d81-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="55d81-112">Required.</span></span> <span data-ttu-id="55d81-113">Indica o início da propriedade do indexador.</span><span class="sxs-lookup"><span data-stu-id="55d81-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="55d81-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="55d81-114">Required.</span></span> <span data-ttu-id="55d81-115">Uma expressão de inteiro que especifica a posição de um elemento da coleção baseada em zero.</span><span class="sxs-lookup"><span data-stu-id="55d81-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="55d81-116">)</span><span class="sxs-lookup"><span data-stu-id="55d81-116">)</span></span>|<span data-ttu-id="55d81-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="55d81-117">Required.</span></span> <span data-ttu-id="55d81-118">Indica o fim da propriedade do indexador.</span><span class="sxs-lookup"><span data-stu-id="55d81-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="55d81-119">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="55d81-119">Return Value</span></span>  
 <span data-ttu-id="55d81-120">O objeto do local especificado na coleção, ou `Nothing` se o índice está fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="55d81-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55d81-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="55d81-121">Remarks</span></span>  
 <span data-ttu-id="55d81-122">Você pode usar a propriedade do indexador de extensão para acessar elementos individuais em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="55d81-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="55d81-123">Esta propriedade do indexador normalmente é usada na saída das propriedades do eixo XML.</span><span class="sxs-lookup"><span data-stu-id="55d81-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="55d81-124">O filho do XML e propriedades de eixo descendente XML retornam coleções de <xref:System.Xml.Linq.XElement>objetos ou um valor de atributo.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="55d81-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="55d81-125">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte propriedades do indexador de extensão para chamadas para o`ElementAtOrDefault` método.</span><span class="sxs-lookup"><span data-stu-id="55d81-125">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts extension indexer properties to calls to the`ElementAtOrDefault` method.</span></span> <span data-ttu-id="55d81-126">Ao contrário de um indexador de matriz, o`ElementAtOrDefault` método retorna `Nothing` se o índice está fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="55d81-126">Unlike an array indexer, the`ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="55d81-127">Esse comportamento é útil quando você não consegue determinar o número de elementos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="55d81-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="55d81-128">Esta propriedade do indexador é como uma propriedade de extensão para coleções que implementam <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>: ele é usado somente se a coleção não possui um indexador ou uma propriedade padrão.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="55d81-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="55d81-129">Para acessar o valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>objetos, você pode usar o XML `Value` propriedade.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="55d81-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="55d81-130">Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="55d81-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55d81-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55d81-131">Example</span></span>  
 <span data-ttu-id="55d81-132">O exemplo a seguir mostra como usar o indexador de extensão para acessar o segundo nó filho em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="55d81-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="55d81-133">A coleção é acessada usando a propriedade de eixo filho, que obtém todos os elementos filho chamados `phone` no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="55d81-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 <span data-ttu-id="55d81-134">[!code-vb[VbXMLSamples&#24;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="55d81-134">[!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]</span></span>  
  
 <span data-ttu-id="55d81-135">Esse código exibe o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="55d81-135">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="55d81-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55d81-136">See Also</span></span>  
 <span data-ttu-id="55d81-137"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="55d81-137"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="55d81-138"> [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="55d81-138"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="55d81-139"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="55d81-139"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="55d81-140"> [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="55d81-140"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="55d81-141"> [Propriedade do Valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)</span><span class="sxs-lookup"><span data-stu-id="55d81-141"> [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)</span></span>
