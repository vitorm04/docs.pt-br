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
ms.openlocfilehash: 928917d25b5f3f97c4b8cdff85efdaa1957be41e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399311"
---
# <a name="c-keywords"></a>Palavras-chave C#

As palavras-chave são identificadores reservados predefinidos com significados especiais para o compilador. Elas não podem ser usadas como identificadores em seu programa, a não ser que incluam `@` como prefixo. Por exemplo, `@if` é um identificador válido, mas `if` não é porque `if` é uma palavra-chave.  
  
 A primeira tabela neste tópico lista as palavras-chave que são identificadores reservados em qualquer parte de um programa C#. A segunda tabela neste tópico lista as palavras-chave contextuais em C#. As palavras-chave contextuais têm significado especial somente em um contexto limitado de programa e podem ser usadas como identificadores fora de contexto. Em geral, à medida que novas palavras-chave são adicionadas na linguagem C#, elas são adicionadas como palavras-chave contextuais para evitar a interrupção de programas escritos em versões anteriores.  
  
|||||  
|---|---|---|---|  
|[Abstrata](abstract.md)|[Como](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[Bool](../builtin-types/bool.md)|  
|[Quebrar](break.md)|[Byte](../builtin-types/integral-numeric-types.md)|[Caso](switch.md)|[catch](try-catch.md)|  
|[Char](../builtin-types/char.md)|[verificado](checked.md)|[class](class.md)|[const](const.md)|  
|[continuar](continue.md)|[Decimal](../builtin-types/floating-point-numeric-types.md)|[Padrão](default.md)|[Delegado](../builtin-types/reference-types.md)|  
|[fazer](do.md)|[Duplo](../builtin-types/floating-point-numeric-types.md)|[Mais](if-else.md)|[Enum](../builtin-types/enum.md)|  
|[Evento](event.md)|[Explícita](../operators/user-defined-conversion-operators.md)|[Extern](extern.md)|[false](../builtin-types/bool.md)|  
|[Finalmente](try-finally.md)|[Fixo](fixed-statement.md)|[Flutuar](../builtin-types/floating-point-numeric-types.md)|[Para](for.md)|  
|[Foreach](foreach-in.md)|[Goto](goto.md)|[Se](if-else.md)|[Implícita](../operators/user-defined-conversion-operators.md)|  
|[Em](in.md)|[Int](../builtin-types/integral-numeric-types.md)|[Interface](interface.md)|[Interno](internal.md)|
|[É](is.md)|[Bloqueio](lock-statement.md)|[Longas](../builtin-types/integral-numeric-types.md)|[Namespace](namespace.md)|
|[Novo](../operators/new-operator.md)|[Null](null.md)|[Objeto](../builtin-types/reference-types.md)|[Operador](../operators/operator-overloading.md)|
|[fora](out.md)|[Substituir](override.md)|[Params](params.md)|[Privada](private.md)|
|[Protegido](protected.md)|[público](public.md)|[Readonly](readonly.md)|[ref](ref.md)|
|[Retorno](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[Curto](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[Estático](static.md)|[String](../builtin-types/reference-types.md)|
|[struct](../builtin-types/struct.md)|[Interruptor](switch.md)|[Este](this.md)|[Jogar](throw.md)|
|[true](../builtin-types/bool.md)|[Tentar](try-catch.md)|[Typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[Ulong](../builtin-types/integral-numeric-types.md)|[desmarcado](unchecked.md)|[Inseguro](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[Usando](using.md)|[usando estática](using-static.md)|[Virtual](virtual.md)|[Vazio](../builtin-types/void.md)|
|[Volátil](volatile.md)|[Enquanto](while.md)|

## <a name="contextual-keywords"></a>Palavras-chave contextuais

 Uma palavra-chave contextual é usada para fornecer um significado específico no código, mas não é uma palavra reservada no C#. Algumas palavras-chave contextuais, como `partial` e `where`, têm significados especiais em dois ou mais contextos.  
  
||||  
|---|---|---|  
|[adicionar](add.md)|[Alias](extern-alias.md)|[Crescente](ascending.md)|
|[Async](async.md)|[Aguardam](../operators/await.md)|[Por](by.md)|
|[Descendente](descending.md)|[dinâmico](../builtin-types/reference-types.md)|[Equals](equals.md)|
|[De](from-clause.md)|[get](get.md)|[Global](../operators/namespace-alias-qualifier.md)|
|[grupo](group-clause.md)|[Em](into.md)|[Juntar](join-clause.md)|
|[Deixe](let-clause.md)|[nameof](../operators/nameof.md)|[Em](on.md)|
|[Orderby](orderby-clause.md)|[parcial (tipo)](partial-type.md)|[partial (método)](partial-method.md)|
|[remover](remove.md)|[Selecione](select-clause.md)|[Definir](set.md)|
|[não gerenciado (restrição de tipo genérico)](where-generic-type-constraint.md)|[value](value.md)|[Var](var.md)|
|[when (condição de filtro)](when.md)|[where (restrição de tipo genérico)](where-generic-type-constraint.md)|[where (cláusula de consulta)](where-clause.md)|
|[Rendimento](yield.md)| | |
  
## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
