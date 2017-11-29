---
title: "Exceções: a função raise (F#)"
description: "Saiba como a F # 'raise' função é usada para indicar que ocorreu um erro ou uma condição excepcional."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: dc524a06d075b982a6aa1fd266769bfc7d883517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-raise-function"></a>Exceções: a função raise

O `raise` função é usada para indicar que ocorreu um erro ou uma condição excepcional. Informações sobre o erro são capturadas em um objeto de exceção.


## <a name="syntax"></a>Sintaxe

```fsharp
raise (expression)
```

## <a name="remarks"></a>Comentários
O `raise` função gera um objeto de exceção e inicia uma processo de desenrolamento da pilha. O processo de desenrolamento de pilha é gerenciado pelo common language runtime (CLR), o comportamento desse processo é o mesmo, pois ele está em qualquer outra linguagem .NET. O processo de desenrolamento de pilha é uma pesquisa para um manipulador de exceção que coincide com a exceção gerada. A pesquisa inicia no atual `try...with` expressão, se houver um. Cada padrão no `with` bloco estiver marcado, em ordem. Quando um manipulador de exceção de correspondência for encontrado, a exceção será considerada tratada; Caso contrário, a pilha é organizada e `with` blocos a cadeia de chamada são verificados, até que um manipulador correspondente foi encontrado. Qualquer `finally` blocos que são encontrados na cadeia de chamada também são executados em sequência conforme a pilha esvazia.

O `raise` função é o equivalente de `throw` em c# ou C++. Use `reraise` em um manipulador catch para propagar a mesma exceção a cadeia de chamada.

Os exemplos de código a seguir ilustram o uso do `raise` função para gerar uma exceção.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

O `raise` função também pode ser usada para gerar exceções .NET, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a>Consulte também
[Tratamento de Exceção](index.md)

[Tipos de Exceção](exception-types.md)

[Exceções: a expressão `try...with`](the-try-with-expression.md)

[Exceções: a expressão `try...finally`](the-try-finally-expression.md)

[Exceções: a função `failwith`](the-failwith-function.md)

[Exceções: a função `invalidArg`](the-invalidArg-function.md)
