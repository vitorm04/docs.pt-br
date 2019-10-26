---
title: Elementos (propriedade dinâmica de XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.openlocfilehash: 812adabd3bfb01fd9313ce3f35e6cb0a5e23344e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920849"
---
# <a name="elements-xelement-dynamic-property"></a><span data-ttu-id="baace-102">Elementos (propriedade dinâmica de XElement)</span><span class="sxs-lookup"><span data-stu-id="baace-102">Elements (XElement dynamic property)</span></span>

<span data-ttu-id="baace-103">Obtém um indexador usado para recuperar elementos filho do elemento atual que corresponde ao nome especificado expandido.</span><span class="sxs-lookup"><span data-stu-id="baace-103">Gets an indexer used to retrieve the child elements of the current element that match the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="baace-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="baace-104">Syntax</span></span>

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="baace-105">Valor da propriedade/valor retornado</span><span class="sxs-lookup"><span data-stu-id="baace-105">Property value/return value</span></span>

<span data-ttu-id="baace-106">Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="baace-106">An indexer of the type `IEnumerable<XElement> Item(String expandedName)`.</span></span> <span data-ttu-id="baace-107">Esse marcador utiliza o nome expandido de elementos filhos desejados e retorna os elementos filho correspondentes em uma coleção de <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` .</span><span class="sxs-lookup"><span data-stu-id="baace-107">This indexer takes the expanded name of the desired child elements and returns the matching child elements in an <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="baace-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="baace-108">Remarks</span></span>

<span data-ttu-id="baace-109">Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> da classe de <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="baace-109">This property is equivalent to the <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> method of the <xref:System.Xml.Linq.XContainer> class.</span></span>

<span data-ttu-id="baace-110">Os elementos na coleção retornada estão na ordem de documento-fonte XML.</span><span class="sxs-lookup"><span data-stu-id="baace-110">The elements in the returned collection are in XML source document order.</span></span>

<span data-ttu-id="baace-111">Esta propriedade usa a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="baace-111">This property uses deferred execution.</span></span>

## <a name="see-also"></a><span data-ttu-id="baace-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="baace-112">See also</span></span>

- [<span data-ttu-id="baace-113">Propriedades dinâmicas da classe XElement</span><span class="sxs-lookup"><span data-stu-id="baace-113">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="baace-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="baace-114">Element</span></span>](element-xelement-dynamic-property.md)
- [<span data-ttu-id="baace-115">Descendentes</span><span class="sxs-lookup"><span data-stu-id="baace-115">Descendants</span></span>](descendants-xelement-dynamic-property.md)
