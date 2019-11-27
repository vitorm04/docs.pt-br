---
title: Substituições
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351380"
---
# <a name="overrides-visual-basic"></a>Substituições (Visual Basic)

Especifica que uma propriedade ou procedimento substitui uma propriedade nomeada de forma idêntica ou procedimento herdado de uma classe base.

## <a name="rules"></a>Regras

- **Contexto de declaração.** Você pode usar `Overrides` apenas em uma instrução de declaração de propriedade ou de procedimento.

- **Modificadores combinados.** Você não pode especificar `Overrides` junto com `Shadows` ou `Shared` na mesma declaração. Como um elemento de substituição é implicitamente substituível, não é possível combinar `Overridable` com `Overrides`.

- **Assinaturas correspondentes.** A assinatura dessa declaração deve corresponder exatamente à *assinatura* da propriedade ou do procedimento que ela substitui. Isso significa que as listas de parâmetros devem ter o mesmo número de parâmetros, na mesma ordem, com os mesmos tipos de dados.

  Além da assinatura, a declaração de substituição também deve corresponder exatamente ao seguinte:

  - O nível de acesso

  - O tipo de retorno, se houver

- **Assinaturas genéricas.** Para um procedimento genérico, a assinatura inclui o número de parâmetros de tipo. Portanto, a declaração de substituição também deve corresponder à versão da classe base nesse aspecto.

- **Correspondência adicional.** Além de corresponder à assinatura da versão da classe base, essa declaração também deve corresponder aos seguintes aspectos:

  - Modificador de nível de acesso (como [público](../../../visual-basic/language-reference/modifiers/public.md))

  - Mecanismo de passagem de cada parâmetro ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))

  - Listas de restrição em cada parâmetro de tipo de um procedimento genérico

- **Sombreamento e substituição.** Sombreamento e substituição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

Se você usar `Overrides`, o compilador adicionará implicitamente `Overloads` para que suas APIs de biblioteca C# funcionem com mais facilidade.

O modificador de `Overrides` pode ser usado nesses contextos:

- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Consulte também

- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
