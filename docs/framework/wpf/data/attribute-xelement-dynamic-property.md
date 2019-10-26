---
title: Atributo (propriedade dinâmica de XElement)
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 2b645575a5b6876ffbb52a999c4e05a2de037493
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920912"
---
# <a name="attribute-xelement-dynamic-property"></a><span data-ttu-id="83ff4-102">Atributo (propriedade dinâmica de XElement)</span><span class="sxs-lookup"><span data-stu-id="83ff4-102">Attribute (XElement dynamic property)</span></span>

<span data-ttu-id="83ff4-103">Obtém um indexador usado para recuperar a instância do atributo que corresponde ao nome especificado expandido.</span><span class="sxs-lookup"><span data-stu-id="83ff4-103">Gets an indexer used to retrieve the attribute instance that corresponds to the specified expanded name.</span></span>

## <a name="syntax"></a><span data-ttu-id="83ff4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83ff4-104">Syntax</span></span>

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a><span data-ttu-id="83ff4-105">Valor da propriedade/valor retornado</span><span class="sxs-lookup"><span data-stu-id="83ff4-105">Property value/return value</span></span>

<span data-ttu-id="83ff4-106">Um indicador de tipo `XAttribute Item(String expandedName)`.</span><span class="sxs-lookup"><span data-stu-id="83ff4-106">An indexer of the type `XAttribute Item(String expandedName)`.</span></span> <span data-ttu-id="83ff4-107">Esse marcador utiliza o nome do atributo especificado e retorna <xref:System.Xml.Linq.XAttribute>correspondente, ou `null` se não houver nenhum atributo com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="83ff4-107">This indexer takes the expanded name of the specified attribute and returns the corresponding <xref:System.Xml.Linq.XAttribute>, or `null` if there is no attribute with the specified name.</span></span>

## <a name="remarks"></a><span data-ttu-id="83ff4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="83ff4-108">Remarks</span></span>

<span data-ttu-id="83ff4-109">Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="83ff4-109">This property is equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement?displayProperty=fullName> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="83ff4-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83ff4-110">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [<span data-ttu-id="83ff4-111">Propriedades dinâmicas da classe XElement</span><span class="sxs-lookup"><span data-stu-id="83ff4-111">XElement Class Dynamic Properties</span></span>](attribute-xelement-dynamic-property.md)
- [<span data-ttu-id="83ff4-112">Value</span><span class="sxs-lookup"><span data-stu-id="83ff4-112">Value</span></span>](value-xattribute-dynamic-property.md)
