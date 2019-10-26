---
title: XML (propriedade dinâmica de XElement)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XElement.Xml
ms.openlocfilehash: 9bac9797f397a0bea1dda36bf864f88293061893
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920716"
---
# <a name="xml-xelement-dynamic-property"></a>XML (propriedade dinâmica de XElement)

Obtém o conteúdo sem formatação XML do elemento.

## <a name="syntax"></a>Sintaxe

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor retornado

<xref:System.String> que representa o conteúdo sem formatação XML do elemento.

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> da classe de <xref:System.Xml.Linq.XNode?displayProperty=fullName> , com o parâmetro de `SaveOptions` definido como <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Consulte também

- [Propriedades dinâmicas da classe XElement](attribute-xelement-dynamic-property.md)
- [Value](value-xelement-dynamic-property.md)
