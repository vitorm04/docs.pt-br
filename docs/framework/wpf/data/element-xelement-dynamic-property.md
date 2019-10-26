---
title: Elemento (propriedade dinâmica de XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.openlocfilehash: fc0277d0dc38574696f01e6915e5382744345771
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920891"
---
# <a name="element-xelement-dynamic-property"></a><span data-ttu-id="b804d-102">Elemento (propriedade dinâmica de XElement)</span><span class="sxs-lookup"><span data-stu-id="b804d-102">Element (XElement dynamic property)</span></span>

<span data-ttu-id="b804d-103">Obtém um indexador usado para recuperar a instância do elemento filho que corresponde ao nome especificado expandido.</span><span class="sxs-lookup"><span data-stu-id="b804d-103">Gets an indexer used to retrieve the child element instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="b804d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b804d-104">Syntax</span></span>

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="b804d-105">Valor da propriedade/valor retornado</span><span class="sxs-lookup"><span data-stu-id="b804d-105">Property value/return value</span></span>

<span data-ttu-id="b804d-106">Um indicador de tipo `XElement Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="b804d-106">An indexer of the type `XElement Item(String expandedName)`.</span></span> <span data-ttu-id="b804d-107">Esse marcador aceita um parâmetro expandido de nome e retorna <xref:System.Xml.Linq.XElement>correspondente, ou `null` se não houver nenhum elemento com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="b804d-107">This indexer takes an expanded name parameter and returns the corresponding <xref:System.Xml.Linq.XElement>, or `null` if there is no element with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="b804d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b804d-108">Remarks</span></span>

<span data-ttu-id="b804d-109">Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Element%2A> da classe de <xref:System.Xml.Linq.XContainer?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="b804d-109">This property is equivalent to <xref:System.Xml.Linq.XContainer.Element%2A> method of the <xref:System.Xml.Linq.XContainer?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b804d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b804d-110">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [<span data-ttu-id="b804d-111">Propriedades dinâmicas da classe XElement</span><span class="sxs-lookup"><span data-stu-id="b804d-111">XElement class dynamic properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="b804d-112">Elementos</span><span class="sxs-lookup"><span data-stu-id="b804d-112">Elements</span></span>](elements-xelement-dynamic-property.md)
