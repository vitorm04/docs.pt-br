---
title: Palavras-chave C#
ms.date: 03/07/2017
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: f325d8ba09e3c3d1c1b3436f758e8fc1696c7f49
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167849"
---
# <a name="c-keywords"></a>Palavras-chave C#

As palavras-chave são identificadores reservados predefinidos com significados especiais para o compilador. Elas não podem ser usadas como identificadores em seu programa, a não ser que incluam `@` como prefixo. Por exemplo, `@if` é um identificador válido, mas `if` não é porque `if` é uma palavra-chave.  
  
 A primeira tabela neste tópico lista as palavras-chave que são identificadores reservados em qualquer parte de um programa C#. A segunda tabela neste tópico lista as palavras-chave contextuais em C#. As palavras-chave contextuais têm significado especial somente em um contexto limitado de programa e podem ser usadas como identificadores fora de contexto. Em geral, à medida que novas palavras-chave são adicionadas na linguagem C#, elas são adicionadas como palavras-chave contextuais para evitar a interrupção de programas escritos em versões anteriores.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[case](switch.md)|[catch](try-catch.md)|  
|[char](char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](delegate.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[enum](enum.md)|  
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](false-literal.md)|  
|[finally](try-finally.md)|[fixed](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[null](null.md)|[object](object.md)|[operator](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](string.md)|
|[struct](struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](true-literal.md)|[try](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[using static](using-static.md)|[virtual](virtual.md)|[void](void.md)|
|[volatile](volatile.md)|[while](while.md)|

## <a name="contextual-keywords"></a>Palavras-chave contextuais

 Uma palavra-chave contextual é usada para fornecer um significado específico no código, mas não é uma palavra reservada no C#. Algumas palavras-chave contextuais, como `partial` e `where`, têm significados especiais em dois ou mais contextos.  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[dynamic](dynamic.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[global](../operators/namespace-alias-qualifier.md)|
|[group](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[let](let-clause.md)|[nameof](../operators/nameof.md)|[on](on.md)|
|[orderby](orderby-clause.md)|[parcial (tipo)](partial-type.md)|[partial (método)](partial-method.md)|
|[remove](remove.md)|[select](select-clause.md)|[set](set.md)|
|[value](value.md)|[var](var.md)|[when (condição de filtro)](when.md)|
|[where (restrição de tipo genérico)](where-generic-type-constraint.md)|[where (cláusula de consulta)](where-clause.md)|[yield](yield.md)|
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
