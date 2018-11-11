---
title: Tipos de exceção (F#)
description: Saiba como definir e usar tipos de exceção do F#.
ms.date: 05/16/2016
ms.openlocfilehash: b8d648a3649153a3604856deb61ce41db8c40bf2
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858815"
---
# <a name="exception-types"></a>Tipos de exceção

Há duas categorias de exceções em F#: tipos de exceção do .NET e tipos de exceção do F#. Este tópico descreve como definir e usar tipos de exceção do F#.

## <a name="syntax"></a>Sintaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *tipo de exceção* é o nome de um nova linguagem F# tipo de exceção, e *tipo de argumento* representa o tipo de um argumento que pode ser fornecido quando você gerar uma exceção desse tipo. Você pode especificar vários argumentos usando um tipo de tupla para *tipo de argumento*.

Uma definição típica para uma exceção do F# é semelhante à seguinte.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Você pode gerar uma exceção desse tipo usando o `raise` de função, da seguinte maneira.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Você pode usar um tipo de exceção do F# diretamente em filtros em um `try...with` expressão, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

O tipo de exceção que você define com as `exception` palavra-chave em F# é um novo tipo que herda de `System.Exception`.

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Exceções: a função `raise`](the-raise-function.md)
- [Hierarquia de exceções](https://msdn.microsoft.com/library/z4c5tckx.aspx)
