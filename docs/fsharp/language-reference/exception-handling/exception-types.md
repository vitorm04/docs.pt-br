---
title: Tipos de exceção
description: Saiba como definir e usar F# tipos de exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630315"
---
# <a name="exception-types"></a>Tipos de exceção

Há duas categorias de exceções no: F#tipos de exceção do .NET F# e tipos de exceção. Este tópico descreve como definir e usar F# tipos de exceção.

## <a name="syntax"></a>Sintaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, o *tipo de exceção* é o nome de um novo F# tipo de exceção, e o *tipo de argumento* representa o tipo de um argumento que pode ser fornecido quando você gera uma exceção desse tipo. Você pode especificar vários argumentos usando um tipo de tupla para o *tipo de argumento*.

Uma definição típica para uma F# exceção é semelhante à seguinte.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Você pode gerar uma exceção desse tipo usando a função, `raise` da seguinte maneira.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Você pode usar um F# tipo de exceção diretamente nos filtros em uma `try...with` expressão, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

O tipo de exceção que você define com `exception` a palavra F# -chave in é um novo tipo `System.Exception`que herda de.

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Exceções: a função `raise`](the-raise-function.md)
- [Hierarquia de exceções](https://msdn.microsoft.com/library/z4c5tckx.aspx)
