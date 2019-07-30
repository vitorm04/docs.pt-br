---
title: Asserções
description: Saiba como usar a expressão ' Assert ' como um recurso de depuração para testar expressões na linguagem F# de programação.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630031"
---
# <a name="assertions"></a>Asserções

A `assert` expressão é um recurso de depuração que você pode usar para testar uma expressão. Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.

## <a name="syntax"></a>Sintaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Comentários

A `assert` expressão tem o `bool -> unit`tipo.

Na sintaxe anterior, *Condition* representa uma expressão booliana a ser testada. Se a expressão for avaliada `true`como, a execução continuará inalterada. Se ele for avaliado como `false`, uma caixa de diálogo de erro do sistema será gerada. A caixa de diálogo de erro tem uma legenda que contém a declaração de cadeia de caracteres **com falha**. A caixa de diálogo contém um rastreamento de pilha que indica onde ocorreu a falha de asserção.

A verificação de asserção é habilitada somente quando você compila no modo de depuração; ou seja, se a constante `DEBUG` for definida. No sistema do projeto, por padrão, a `DEBUG` constante é definida na configuração de depuração, mas não na configuração da versão.

O erro de falha de asserção não pode ser F# capturado usando a manipulação de exceção.

> [!NOTE]
> A `assert` função é resolvida para <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo de código a seguir ilustra o uso `assert` da expressão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
