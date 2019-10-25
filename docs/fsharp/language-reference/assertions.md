---
title: Asserções
description: Saiba como usar a expressão ' Assert ' como um recurso de depuração para testar expressões na linguagem F# de programação.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799068"
---
# <a name="assertions"></a>Asserções

A expressão de `assert` é um recurso de depuração que você pode usar para testar uma expressão. Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.

## <a name="syntax"></a>Sintaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Comentários

A expressão de `assert` tem `bool -> unit`de tipo.

A função `assert` resolve para <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>. Isso significa que seu comportamento é idêntico a ter chamado <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> diretamente.

A verificação de asserção é habilitada somente quando você compila no modo de depuração; ou seja, se a constante `DEBUG` for definida. No sistema do projeto, por padrão, a constante `DEBUG` é definida na configuração de depuração, mas não na configuração da versão.

O erro de falha de asserção não pode ser F# capturado usando a manipulação de exceção.

## <a name="example"></a>Exemplo

O exemplo de código a seguir ilustra o uso da expressão `assert`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
