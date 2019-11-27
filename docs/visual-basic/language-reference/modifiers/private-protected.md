---
title: Protegido de forma particular
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351342"
---
# <a name="private-protected-visual-basic"></a>Privado protegido (Visual Basic)

A combinação de palavras-chave `Private Protected` é um modificador de acesso de membro. Um membro `Private Protected` é acessível por todos os membros em sua classe que o contém, bem como por tipos derivados da classe que a contém, mas somente se eles forem encontrados em seu assembly de contenção.

Você pode especificar `Private Protected` somente em membros de classes; Você não pode aplicar `Private Protected` aos membros de uma estrutura porque as estruturas não podem ser herdadas.

O `Private Protected` modificador de acesso é suportado pelo Visual Basic 15,5 e posterior. Para usá-lo, você pode adicionar o seguinte elemento ao seu arquivo de Visual Basic projeto (\*. vbproj). Desde que Visual Basic 15,5 ou posterior esteja instalado no seu sistema, ele permite que você aproveite todos os recursos de linguagem suportados pela versão mais recente do compilador de Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Para obter mais informações, consulte [definindo a versão do idioma do Visual Basic](../../language-reference/configure-language-version.md).

> [!NOTE]
> No Visual Studio, a seleção de ajuda F1 no `private protected` fornece ajuda para [privado](private.md) ou [protegido](protected.md). O IDE escolhe o único token sob o cursor em vez da palavra composta.

## <a name="rules"></a>Regras

- **Contexto de declaração.** Você pode usar `Private Protected` apenas no nível de classe. Isso significa que o contexto de declaração para um elemento de `Protected` deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.

## <a name="behavior"></a>Comportamento

- **Nível de acesso.** Todo o código em uma classe pode acessar seus elementos. O código em qualquer classe que deriva de uma classe base e está contido no mesmo assembly pode acessar todos os elementos de `Private Protected` da classe base. No entanto, o código em qualquer classe derivada de uma classe base e está contido em um assembly diferente não pode acessar os elementos de `Private Protected` da classe base.

- **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas de *modificadores de acesso*. Para obter uma comparação dos modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

O modificador de `Private Protected` pode ser usado nesses contextos:

- [Declaração de classe](../../../visual-basic/language-reference/statements/class-statement.md) de uma classe aninhada

- [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)

- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) de um delegado aninhado em uma classe

- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Instrução enum](../../../visual-basic/language-reference/statements/enum-statement.md) de uma enumeração aninhada em uma classe

- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)

- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Declaração de interface](../../../visual-basic/language-reference/statements/interface-statement.md) de uma interface aninhada em uma classe

- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Instrução de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md) de uma estrutura aninhada em uma classe

- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Consulte também

- [Público](../../../visual-basic/language-reference/modifiers/public.md)
- [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Amigo Protegido](./protected-friend.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
