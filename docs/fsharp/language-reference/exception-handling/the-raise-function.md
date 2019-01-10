---
title: 'Exceções: a função raise'
description: Saiba como o F# 'raise' função é usada para indicar que um erro ou uma condição excepcional ocorreu.
ms.date: 05/16/2016
ms.openlocfilehash: 87773ead7773c62a325c7e7ff105c729e10dd69c
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610145"
---
# <a name="exceptions-the-raise-function"></a>Exceções: a função raise

O `raise` função é usada para indicar que um erro ou uma condição excepcional ocorreu. Informações sobre o erro são capturadas em um objeto de exceção.

## <a name="syntax"></a>Sintaxe

```fsharp
raise (expression)
```

## <a name="remarks"></a>Comentários

O `raise` função gera um objeto de exceção e inicia uma processo de desenrolamento de pilha. O processo de desenrolamento de pilha é gerenciado pelo common language runtime (CLR), portanto, o comportamento desse processo é o mesmo que ele esteja em qualquer outra linguagem .NET. O processo de desenrolamento de pilha é uma pesquisa por um manipulador de exceção que coincide com a exceção gerada. A pesquisa inicia no atual `try...with` expressão, se houver um. Cada padrão no `with` bloco estiver marcado, em ordem. Quando um manipulador de exceção correspondente for encontrado, a exceção será considerada tratada; Caso contrário, a pilha é desenrolada e `with` blocos de cadeia de chamadas são verificados até que um manipulador correspondente for encontrado. Qualquer `finally` blocos que são encontrados na cadeia de chamadas também são executados em sequência, conforme a pilha esvazia.

O `raise` função é o equivalente de `throw` em c# ou C++. Use `reraise` em um manipulador catch para propagar a mesma exceção na cadeia de chamada.

Os exemplos de código a seguir ilustram o uso do `raise` função para gerar uma exceção.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

O `raise` função também pode ser usada para gerar exceções .NET, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Tipos de Exceção](exception-types.md)
- [Exceções: O `try...with` expressão](the-try-with-expression.md)
- [Exceções: O `try...finally` expressão](the-try-finally-expression.md)
- [Exceções: O `failwith` função](the-failwith-function.md)
- [Exceções: O `invalidArg` função](the-invalidArg-function.md)