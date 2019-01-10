---
title: Tipos de exceção
description: Saiba como definir e usar F# tipos de exceção.
ms.date: 05/16/2016
ms.openlocfilehash: ed721dd0dc46a486fafeac2fa4c096800995ccb7
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612823"
---
# <a name="exception-types"></a>Tipos de exceção

Há duas categorias de exceções em F#: os tipos de exceção .NET e F# tipos de exceção. Este tópico descreve como definir e usar F# tipos de exceção.

## <a name="syntax"></a>Sintaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *tipo de exceção* é o nome de um novo F# tipo de exceção, e *tipo de argumento* representa o tipo de um argumento que pode ser fornecido quando você gerar uma exceção desse tipo. Você pode especificar vários argumentos usando um tipo de tupla para *tipo de argumento*.

Uma definição típica para uma F# exceção semelhante à seguinte.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Você pode gerar uma exceção desse tipo usando o `raise` de função, da seguinte maneira.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Você pode usar um F# tipo de exceção diretamente em filtros em uma `try...with` expressão, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

O tipo de exceção que você define com as `exception` palavra-chave na F# é um novo tipo que herda de `System.Exception`.

## <a name="see-also"></a>Consulte também

- [Tratamento de Exceção](index.md)
- [Exceções: a função `raise`](the-raise-function.md)
- [Hierarquia de exceções](https://msdn.microsoft.com/library/z4c5tckx.aspx)