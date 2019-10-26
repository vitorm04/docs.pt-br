---
title: Valor (propriedade dinâmica de XAttribute)
ms.date: 10/22/2019
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.openlocfilehash: 32c15a89a976b5f9af12f040c43e724a25357ead
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920646"
---
# <a name="value-xattribute-dynamic-property"></a>Valor (propriedade dinâmica de XAttribute)

Obtém ou define o valor de atributo XML.

## <a name="syntax"></a>Sintaxe

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor retornado

<xref:System.String> que contém o valor deste atributo.

## <a name="exceptions"></a>Exceções

|Tipo de exceção|Condição|
| - |---------------|
|<xref:System.ArgumentNullException>|Ao definir, `value` é `null`.|

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente à propriedade de <xref:System.Xml.Linq.XAttribute.Value%2A> da classe de <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> , mas suporta essa propriedade dinâmica também alterar notificações.

## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Propriedades dinâmicas da classe XAttribute](value-xattribute-dynamic-property.md)
- [Attribute](attribute-xelement-dynamic-property.md)
