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
# <a name="attribute-xelement-dynamic-property"></a>Atributo (propriedade dinâmica de XElement)

Obtém um indexador usado para recuperar a instância do atributo que corresponde ao nome especificado expandido.

## <a name="syntax"></a>Sintaxe

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor retornado

Um indicador de tipo `XAttribute Item(String expandedName)`. Esse marcador utiliza o nome do atributo especificado e retorna <xref:System.Xml.Linq.XAttribute>correspondente, ou `null` se não houver nenhum atributo com o nome especificado.

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement?displayProperty=fullName> .

## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Propriedades dinâmicas da classe XElement](attribute-xelement-dynamic-property.md)
- [Value](value-xattribute-dynamic-property.md)
