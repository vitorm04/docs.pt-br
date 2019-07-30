---
title: 'Exceções: a função raise'
description: Saiba como a F# função ' raise ' é usada para indicar que ocorreu um erro ou uma condição excepcional.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630292"
---
# <a name="exceptions-the-raise-function"></a>Exceções: a função raise

A `raise` função é usada para indicar que ocorreu um erro ou uma condição excepcional. As informações sobre o erro são capturadas em um objeto de exceção.

## <a name="syntax"></a>Sintaxe

```fsharp
raise (expression)
```

## <a name="remarks"></a>Comentários

A `raise` função gera um objeto de exceção e inicia um processo de desenrolamento de pilha. O processo de desenrolamento de pilha é gerenciado pelo Common Language Runtime (CLR), portanto, o comportamento desse processo é o mesmo que em qualquer outra linguagem .NET. O processo de desenrolamento de pilha é uma pesquisa por um manipulador de exceção que corresponda à exceção gerada. A pesquisa começa na expressão atual `try...with` , se houver uma. Cada padrão no `with` bloco é verificado, em ordem. Quando um manipulador de exceção correspondente é encontrado, a exceção é considerada tratada; caso contrário, a pilha será desbobinada e `with` bloqueará a cadeia de chamadas será verificada até que um manipulador correspondente seja encontrado. Todos `finally` os blocos encontrados na cadeia de chamadas também são executados em sequência à medida que a pilha se desenrola.

A `raise` função é o equivalente de `throw` em C# ou C++. Use `reraise` em um manipulador catch para propagar a mesma exceção da cadeia de chamadas.

Os exemplos de código a seguir ilustram o `raise` uso da função para gerar uma exceção.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

A `raise` função também pode ser usada para gerar exceções .net, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: A `try...with` expressão](the-try-with-expression.md)
- [Exceções: A `try...finally` expressão](the-try-finally-expression.md)
- [Exceções: A `failwith` função](the-failwith-function.md)
- [Exceções: A `invalidArg` função](the-invalidArg-function.md)
