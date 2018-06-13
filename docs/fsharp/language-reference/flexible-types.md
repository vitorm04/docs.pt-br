---
title: Tipos flexíveis (F#)
description: 'Saiba como usar o F # anotação de tipo flexível, que indica que um valor, variável ou parâmetro tem um tipo que é compatível com um tipo especificado.'
ms.date: 05/16/2016
ms.openlocfilehash: a54d462d04e4e65680a4612f58da72173f04d1f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563344"
---
# <a name="flexible-types"></a>Tipos flexíveis

Um *anotação de tipo flexível* indica que um valor, variável ou parâmetro tem um tipo que é compatível com um tipo especificado, onde a compatibilidade é determinada pela posição em uma hierarquia orientado a objeto de classes ou interfaces. Tipos flexíveis são úteis, especialmente quando a conversão automática para tipos superiores na hierarquia de tipo não ocorrer, mas você ainda deseja habilitar a funcionalidade trabalhar com qualquer tipo na hierarquia ou qualquer tipo que implementa uma interface.

## <a name="syntax"></a>Sintaxe

```fsharp
#type
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *tipo* representa um tipo base ou interface.

Um tipo flexível é equivalente a um tipo genérico que tem uma restrição que limita os tipos permitidos para tipos que são compatíveis com o tipo base ou interface. Ou seja, as duas linhas de código a seguir são equivalentes.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Tipos flexíveis são úteis em vários tipos de situações. Por exemplo, quando você tem uma função de ordem superior (uma função que usa uma função como um argumento), geralmente é útil para que a função retornar um tipo flexível. No exemplo a seguir, o uso de um tipo flexível com um argumento de sequência em `iterate2` permite que a função de ordem superior trabalhar com funções que geram sequências, matrizes, listas e qualquer outro tipo enumerável.

Considere duas funções a seguir, um dos quais retorna uma sequência, outro que retorna um tipo de flexível.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Como outro exemplo, considere o [SEQ](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) função de biblioteca:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Você pode transmitir qualquer uma das seguintes sequências enumeráveis para esta função:

- Uma lista de listas
- Uma lista de matrizes
- Uma matriz das listas
- Uma matriz de sequências
- Qualquer outra combinação de sequências enumeráveis

O código a seguir usa `Seq.concat` para demonstrar os cenários que você pode suportar usando tipos flexíveis.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

A saída é a seguinte.

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

Em F #, como em outros idiomas e orientada a objeto, há contextos em que tipos derivados ou tipos que implementam as interfaces são automaticamente convertidos em um tipo base ou interface. Essas conversões automático ocorrerem nos argumentos diretos, mas não quando o tipo é em uma posição subordinada, como parte de um tipo mais complexo, como um tipo de retorno de um tipo de função, ou como um argumento de tipo. Assim, a notação de tipo flexível é útil principalmente quando o tipo a que estiver aplicando é parte de um tipo mais complexo.

## <a name="see-also"></a>Consulte também

[Referência da Linguagem F#](index.md)

[Genéricos](generics/index.md)
