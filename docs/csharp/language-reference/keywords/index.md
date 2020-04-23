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
ms.openlocfilehash: 251046a8bd825a90d817965f9f747d08d4492197
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102028"
---
# <a name="c-keywords"></a>Palavras-chave C#

As palavras-chave são identificadores reservados predefinidos com significados especiais para o compilador. Elas não podem ser usadas como identificadores em seu programa, a não ser que incluam `@` como prefixo. Por exemplo, `@if` é um identificador válido, mas `if` não é porque `if` é uma palavra-chave.  
  
 A primeira tabela neste tópico lista as palavras-chave que são identificadores reservados em qualquer parte de um programa C#. A segunda tabela neste tópico lista as palavras-chave contextuais em C#. As palavras-chave contextuais têm significado especial somente em um contexto limitado de programa e podem ser usadas como identificadores fora de contexto. Em geral, à medida que novas palavras-chave são adicionadas na linguagem C#, elas são adicionadas como palavras-chave contextuais para evitar a interrupção de programas escritos em versões anteriores.  
  
|||||  
|---|---|---|---|  
|[Abstrata](abstract.md)|[Como](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[Caso](switch.md)|[catch](try-catch.md)|  
|[char](../builtin-types/char.md)|[Verificado](checked.md)|[Classe](class.md)|[const](const.md)|  
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[Padrão](default.md)|[Delegado](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[enum](../builtin-types/enum.md)|  
|[event](event.md)|[Explícita](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](../builtin-types/bool.md)|  
|[Finalmente](try-finally.md)|[Fixo](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[Implícita](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[Interface](interface.md)|[interno](internal.md)|
|[is](is.md)|[Bloqueio](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[Namespace](namespace.md)|
|[Novo](../operators/new-operator.md)|[nulo](null.md)|[objeto](../builtin-types/reference-types.md)|[Operador](../operators/operator-overloading.md)|
|[fora](out.md)|[override](override.md)|[params](params.md)|[particulares](private.md)|
|[protegidos](protected.md)|[públicos](public.md)|[Readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[Curto](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[cadeia de caracteres](../builtin-types/reference-types.md)|
|[struct](../builtin-types/struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](../builtin-types/bool.md)|[Tentar](try-catch.md)|[Typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[Ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[Inseguro](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[Usando](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[while](while.md)|

## <a name="contextual-keywords"></a>Palavras-chave contextuais

 Uma palavra-chave contextual é usada para fornecer um significado específico no código, mas não é uma palavra reservada no C#. Algumas palavras-chave contextuais, como `partial` e `where`, têm significados especiais em dois ou mais contextos.  
  
||||  
|---|---|---|  
|[adicionar](add.md)|[Alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[Aguardam](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[dinâmico](../builtin-types/reference-types.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[Global](../operators/namespace-alias-qualifier.md)|
|[grupo](group-clause.md)|[into](into.md)|[Juntar](join-clause.md)|
|[Deixe](let-clause.md)|[nameof](../operators/nameof.md)|[Em](on.md)|
|[Orderby](orderby-clause.md)|[parcial (tipo)](partial-type.md)|[parcial (método)](partial-method.md)|
|[remover](remove.md)|[Selecione](select-clause.md)|[Definir](set.md)|
|[não gerenciado (restrição de tipo genérico)](where-generic-type-constraint.md)|[value](value.md)|[var](var.md)|
|[when (condição de filtro)](when.md)|[where (restrição de tipo genérico)](where-generic-type-constraint.md)|[where (cláusula de consulta)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
