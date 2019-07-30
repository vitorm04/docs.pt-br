---
title: Abreviações de tipo
description: Saiba mais F# sobre abreviações de tipo para dar a um tipo um nome mais significativo a fim de facilitar a leitura do código.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630206"
---
# <a name="type-abbreviations"></a>Abreviações de tipo

Uma *abreviação de tipo* é um alias ou nome alternativo para um tipo.

## <a name="syntax"></a>Sintaxe

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>Comentários

Você pode usar abreviações de tipo para dar a um tipo um nome mais significativo, a fim de facilitar a leitura do código. Você também pode usá-los para criar um nome fácil de usar para um tipo que, de outra forma, é difícil de gravar. Além disso, você pode usar abreviações de tipo para facilitar a alteração de um tipo subjacente sem alterar todo o código que usa o tipo. A seguir está uma abreviação de tipo simples.

A acessibilidade do tipo abreviações usa como `public`padrão.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

As abreviações de tipo podem incluir parâmetros genéricos, como no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

No código anterior, `Transform` é uma abreviação de tipo que representa uma função que usa um único argumento de qualquer tipo e que retorna um único valor desse mesmo tipo.

As abreviações de tipo não são preservadas no código .NET Framework MSIL. Portanto, ao usar um F# assembly de outro idioma de .NET Framework, você deve usar o nome de tipo subjacente para uma abreviação de tipo.

As abreviações de tipo também podem ser usadas em unidades de medida. Para obter mais informações, consulte [unidades de medida](units-of-measure.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
