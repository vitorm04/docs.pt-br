---
title: Asserções (F#)
description: "Saiba como usar a expressão 'assert' como um recurso de depuração para testar expressões em F # linguagem de programação."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 195b4a34977a63d92559003b5cd0bb89490a1e7a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="assertions"></a>Asserções

O `assert` expressão é um recurso de depuração que você pode usar para testar uma expressão. Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.

## <a name="syntax"></a>Sintaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Comentários

O `assert` expressão tem tipo `bool -> unit`.

Na sintaxe anterior, *condição* representa uma expressão booleana que deve ser testado. Se a expressão for avaliada como `true`, a execução continua afetados. Se ele for avaliada como `false`, uma caixa de diálogo de erro do sistema é gerada. A caixa de diálogo de erro tem uma legenda que contém a cadeia de caracteres **falha de asserção**. A caixa de diálogo contém um rastreamento de pilha que indica onde ocorreu a falha de asserção.

A verificação de asserção é habilitada somente quando você compilar no modo de depuração; ou seja, se a constante `DEBUG` está definido. No sistema de projeto, por padrão, o `DEBUG` constante é definida na configuração de depuração, mas não na versão de configuração.

O erro de falha de asserção não pode ser capturado por meio de tratamento de exceção F #.

>[!NOTE]
O `assert` função resolve para <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo de código a seguir ilustra o uso do `assert` expressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a>Consulte também

[Referência da Linguagem F#](index.md)
