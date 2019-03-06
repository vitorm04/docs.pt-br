---
title: Private protegida (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: fea43558ac0fe8181f2786b69f2621346d446b2e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376384"
---
# <a name="private-protected-visual-basic"></a>Private protegida (Visual Basic)

A combinação de palavras-chave `Private Protected` é um modificador de acesso de membro. Um `Private Protected` membro é acessível por todos os membros em sua classe recipiente, bem como por tipos derivados da classe recipiente, mas somente se forem encontrados em seu assembly recipiente.

Você pode especificar `Private Protected` somente em membros de classes; não é possível aplicar `Private Protected` aos membros de uma estrutura porque as estruturas não podem ser herdadas.

O `Private Protected` modificador de acesso é suportado pelo Visual Basic 15.5 e posteriores. Para usá-lo, você pode adicionar o seguinte elemento ao seu projeto do Visual Basic (\*. vbproj) arquivos. Como desde que o Visual Basic 15.5 ou posterior estiver instalado no seu sistema, ele permite que você aproveite todos os recursos de idioma com suporte pela versão mais recente do compilador do Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Para obter mais informações, consulte [definindo a versão da linguagem Visual Basic](../../language-reference/configure-language-version.md).

> [!NOTE]
> No Visual Studio, selecionando a Ajuda de F1 na `private protected` fornece ajuda para o [privada](private.md) ou [protegido](protected.md). O IDE escolherá o token único sob o cursor em vez da palavra composta.

## <a name="rules"></a>Regras

- **Contexto da declaração.** Você pode usar `Private Protected` somente no nível de classe. Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, estrutura, módulo ou procedimento.

## <a name="behavior"></a>Comportamento

- **Nível de acesso.** Todo o código em uma classe pode acessar seus elementos. Código em qualquer classe que deriva de uma classe base e está contido no mesmo assembly pode acessar todos os `Private Protected` elementos da classe base. No entanto, o código em qualquer classe que deriva de uma classe base e está contido em um assembly diferente não é possível acessar a classe base `Private Protected` elementos.

- **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. Para obter uma comparação os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

O `Private Protected` modificador pode ser usado nestes contextos:

- [Instrução class](../../../visual-basic/language-reference/statements/class-statement.md) de uma classe aninhada

- [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)

- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) de um delegado aninhado em uma classe

- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md) de uma enumeração aninhado em uma classe

- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)

- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) de uma interface aninhada em uma classe

- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Estrutura da instrução](../../../visual-basic/language-reference/statements/structure-statement.md) de uma estrutura aninhada em uma classe

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
