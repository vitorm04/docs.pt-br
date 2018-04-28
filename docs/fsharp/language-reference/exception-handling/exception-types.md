---
title: Tipos de exceção (F#)
description: 'Saiba como definir e usar tipos de exceção F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 6aaa5cd1b94f829b98d5aed5dcf6e30472a8b751
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="exception-types"></a>Tipos de exceção

Há duas categorias de exceções em F #: tipos de exceção do .NET e tipos de exceção F #. Este tópico descreve como definir e usar tipos de exceção F #.


## <a name="syntax"></a>Sintaxe

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>Comentários
Na sintaxe anterior, *tipo de exceção* é o nome de um novo F # tipo de exceção, e *tipo de argumento* representa o tipo de um argumento que pode ser fornecido quando você gera uma exceção desse tipo. Você pode especificar vários argumentos usando um tipo de tupla para *tipo de argumento*.

Uma definição típica para uma exceção F # é semelhante à seguinte.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

Você pode gerar uma exceção desse tipo usando o `raise` função, da seguinte maneira.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

Você pode usar um tipo de exceção F # diretamente nos filtros em um `try...with` expressão, conforme mostrado no exemplo a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

O tipo de exceção que você definir com a `exception` palavra-chave em F # é um novo tipo que herda de `System.Exception`.


## <a name="see-also"></a>Consulte também
[Tratamento de Exceção](index.md)

[Exceções: a função `raise`](the-raise-function.md)

[Hierarquia de exceções](https://msdn.microsoft.com/library/z4c5tckx.aspx)
