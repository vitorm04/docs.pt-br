---
title: Tipos flexíveis
description: Saiba como usar F# anotação de tipo flexível, que indica que um parâmetro, variável ou valor tem um tipo que é compatível com um tipo especificado.
ms.date: 05/16/2016
ms.openlocfilehash: 32857cc317bc6b4b7baf53b623b551e8e0733e41
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613668"
---
# <a name="flexible-types"></a>Tipos flexíveis

Um *anotação de tipo flexível* indica que um parâmetro, variável ou valor tem um tipo que é compatível com um tipo especificado, onde a compatibilidade é determinada pela posição em uma hierarquia orientada a objeto de classes ou interfaces. Tipos flexíveis são úteis, especialmente quando a conversão automática para tipos mais altos na hierarquia de tipos não ocorrerá, mas você ainda deseja habilitar sua funcionalidade trabalhar com qualquer tipo na hierarquia ou qualquer tipo que implementa uma interface.

## <a name="syntax"></a>Sintaxe

```fsharp
#type
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *tipo* representa um tipo base ou uma interface.

Um tipo flexível é equivalente a um tipo genérico que tem uma restrição que limita os tipos permitidos para tipos que são compatíveis com o tipo base ou interface. Ou seja, as duas linhas de código a seguir são equivalentes.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Tipos flexíveis são úteis em vários tipos de situações. Por exemplo, quando você tem uma função de ordem superior (uma função que usa uma função como um argumento), muitas vezes é útil ter a função retornar um tipo flexível. No exemplo a seguir, o uso de um tipo flexível com um argumento de sequência no `iterate2` permite que a função de ordem superior trabalhar com funções que geram sequências, matrizes, listas e qualquer outro tipo enumerável.

Considere duas funções a seguir, um de que retorna uma sequência, o outro retorna um tipo flexível.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Como outro exemplo, considere a [SEQ. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) função de biblioteca:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Você pode passar qualquer uma das seguintes sequências enumeráveis para essa função:

- Uma lista de listas
- Uma lista de matrizes
- Uma matriz de listas
- Uma matriz de sequências
- Qualquer outra combinação de sequências enumeráveis

O seguinte código usa `Seq.concat` para demonstrar os cenários que você pode suportar usando tipos flexíveis.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

A saída é a seguinte.

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

No F#, como em outras linguagens orientadas a objeto, há tipos derivados de contextos nos quais ou tipos que implementam interfaces são automaticamente convertidos para um tipo base ou interface. Dessas conversões automáticas ocorrem nos argumentos diretos, mas não quando o tipo é em uma posição subordinada, como parte de um tipo mais complexo, como um tipo de retorno de um tipo de função, ou como um argumento de tipo. Portanto, a notação de tipo flexível é útil principalmente quando o tipo que você está aplicando-o para é parte de um tipo mais complexo.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Genéricos](generics/index.md)