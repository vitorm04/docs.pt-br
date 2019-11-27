---
title: Sombras
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351269"
---
# <a name="shadows-visual-basic"></a>Sombras (Visual Basic)

Especifica que um elemento de programação declarado redeclara e oculta um elemento de nome idêntico ou conjunto de elementos sobrecarregados, em uma classe base.

## <a name="remarks"></a>Comentários

A principal finalidade do sombreamento (que também é conhecido como *ocultar por nome*) é preservar a definição de seus membros de classe. A classe base pode passar por uma alteração que cria um elemento com o mesmo nome de um que você já definiu. Se isso acontecer, o modificador `Shadows` força referências por meio de sua classe a ser resolvida para o membro que você definiu, em vez de para o novo elemento de classe base.

Sombreamento e substituição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Regras

- **Contexto de declaração.** Você pode usar `Shadows` somente no nível de classe. Isso significa que o contexto de declaração para um elemento de `Shadows` deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.

  Você pode declarar apenas um elemento de sombreamento em uma única instrução de declaração.

- **Modificadores combinados.** Não é possível especificar `Shadows` junto com `Overloads`, `Overrides`ou `Static` na mesma declaração.

- **Tipos de elemento.** Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo. Se você sombrear uma propriedade ou um procedimento com outra propriedade ou procedimento, os parâmetros e o tipo de retorno não precisarão corresponder àqueles na propriedade ou procedimento da classe base.

- **Acess.** O elemento sombreado na classe base normalmente não está disponível de dentro da classe derivada que a sombreia. No entanto, as considerações a seguir se aplicam.

  - Se o elemento de sombreamento não estiver acessível a partir do código que se refere a ele, a referência será resolvida para o elemento sombreado. Por exemplo, se um elemento `Private` sombreia um elemento de classe base, o código que não tem permissão para acessar o elemento `Private` acessa o elemento da classe base em vez disso.

  - Se você sombrear um elemento, ainda poderá acessar o elemento sombreado por meio de um objeto declarado com o tipo da classe base. Você também pode acessá-lo por meio de `MyBase`.

O modificador de `Shadows` pode ser usado nesses contextos:

- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)

- [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)

- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)

- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Consulte também

- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Estático](../../../visual-basic/language-reference/modifiers/static.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
