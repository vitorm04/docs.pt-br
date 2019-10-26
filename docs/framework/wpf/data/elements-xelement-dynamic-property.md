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
# <a name="elements-xelement-dynamic-property"></a>Elementos (propriedade dinâmica de XElement)

Obtém um indexador usado para recuperar elementos filho do elemento atual que corresponde ao nome especificado expandido.

## <a name="syntax"></a>Sintaxe

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor retornado

Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`. Esse marcador utiliza o nome expandido de elementos filhos desejados e retorna os elementos filho correspondentes em uma coleção de <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` .

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> da classe de <xref:System.Xml.Linq.XContainer> .

Os elementos na coleção retornada estão na ordem de documento-fonte XML.

Esta propriedade usa a execução adiada.

## <a name="see-also"></a>Consulte também

- [Propriedades dinâmicas da classe XElement](attribute-xelement-dynamic-property.md)
- [Elemento](element-xelement-dynamic-property.md)
- [Descendentes](descendants-xelement-dynamic-property.md)
