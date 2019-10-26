---
title: Descendentes (propriedade dinâmica de XElement)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 8d14b0a94d1a2028a56f649a574f157264ba50fa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920884"
---
# <a name="descendants-xelement-dynamic-property"></a><span data-ttu-id="97463-102">Descendentes (propriedade dinâmica de XElement)</span><span class="sxs-lookup"><span data-stu-id="97463-102">Descendants (XElement dynamic property)</span></span>

<span data-ttu-id="97463-103">Obtém um indexador usado para recuperar todos os elementos descendentes do elemento atual que corresponde ao nome especificado expandido.</span><span class="sxs-lookup"><span data-stu-id="97463-103">Gets an indexer used to retrieve all the descendant elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="97463-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97463-104">Syntax</span></span>

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="97463-105">Valor da propriedade/valor retornado</span><span class="sxs-lookup"><span data-stu-id="97463-105">Property value/return value</span></span>

<span data-ttu-id="97463-106">Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="97463-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="97463-107">Esse marcador utiliza o nome expandido de elementos especificados descendente e retorna os elementos filho correspondentes em uma coleção de <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` .</span><span class="sxs-lookup"><span data-stu-id="97463-107">This indexer takes the expanded name of the specified descendant elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="97463-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="97463-108">Remarks</span></span>

<span data-ttu-id="97463-109">Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> da classe de <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="97463-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="97463-110">Os elementos na coleção retornada estão na ordem de documento-fonte XML.</span><span class="sxs-lookup"><span data-stu-id="97463-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="97463-111">Esta propriedade usa a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="97463-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="97463-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97463-112">See also</span></span>

- [<span data-ttu-id="97463-113">Propriedades dinâmicas da classe XElement</span><span class="sxs-lookup"><span data-stu-id="97463-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="97463-114">Elementos</span><span class="sxs-lookup"><span data-stu-id="97463-114">Elements</span></span>](elements-xelement-dynamic-property.md)
