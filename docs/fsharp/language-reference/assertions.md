---
title: Asserções (F#)
description: "Saiba como usar a expressão 'Declare' como um recurso de depuração para testar expressões na linguagem de programação F #."
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097532"
---
# <a name="assertions"></a>Asserções

O `assert` expressão é um recurso de depuração que você pode usar para testar uma expressão. Em caso de falha no modo de depuração, uma asserção gera uma caixa de diálogo de erro do sistema.

## <a name="syntax"></a>Sintaxe

```fsharp
assert condition
```

## <a name="remarks"></a>Comentários

O `assert` expressão tem o tipo `bool -> unit`.

Na sintaxe anterior, *condição* representa uma expressão booleana que deve ser testado. Se a expressão for avaliada como `true`, a execução continua sem ser afetada. Se for avaliada como `false`, uma caixa de diálogo de erro do sistema é gerada. A caixa de diálogo de erro tem uma legenda que contém a cadeia de caracteres **Falha na asserção**. A caixa de diálogo contém um rastreamento de pilha que indica onde ocorreu a falha de asserção.

Verificação de asserção é habilitada somente quando você compilar no modo de depuração; ou seja, se a constante `DEBUG` é definido. No sistema de projeto, por padrão, o `DEBUG` constante é definida na configuração de depuração, mas não na configuração de versão.

O erro de falha de asserção não pode ser detectado por meio de manipulação de exceção do F #.

>[!NOTE]
O `assert` função resolve para <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.

## <a name="example"></a>Exemplo

O exemplo de código a seguir ilustra o uso do `assert` expressão.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
