---
title: Tipos flexíveis
description: Saiba como usar F# a anotação de tipo flexível, que indica que um parâmetro, uma variável ou um valor tem um tipo compatível com um tipo especificado.
ms.date: 05/16/2016
ms.openlocfilehash: bf05f78f163d1f9c73c667df60925b66a5315627
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083071"
---
# <a name="flexible-types"></a>Tipos flexíveis

Uma *anotação de tipo flexível* indica que um parâmetro, uma variável ou um valor tem um tipo compatível com um tipo especificado, onde a compatibilidade é determinada pela posição em uma hierarquia orientada a objeto de classes ou interfaces. Tipos flexíveis são úteis especificamente quando a conversão automática para tipos mais altos na hierarquia de tipos não ocorre, mas você ainda deseja habilitar sua funcionalidade para trabalhar com qualquer tipo na hierarquia ou qualquer tipo que implemente uma interface.

## <a name="syntax"></a>Sintaxe

```fsharp
#type
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, *Type* representa um tipo base ou uma interface.

Um tipo flexível é equivalente a um tipo genérico que tem uma restrição que limita os tipos permitidos a tipos que são compatíveis com o tipo base ou de interface. Ou seja, as duas linhas de código a seguir são equivalentes.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Tipos flexíveis são úteis em vários tipos de situações. Por exemplo, quando você tem uma função de ordem mais alta (uma função que usa uma função como um argumento), muitas vezes é útil fazer com que a função retorne um tipo flexível. No exemplo a seguir, o uso de um tipo flexível com um argumento Sequence em `iterate2` permite que a função de ordem superior funcione com funções que geram sequências, matrizes, listas e qualquer outro tipo enumerável.

Considere as duas funções a seguir, uma das quais retorna uma sequência, a outra que retorna um tipo flexível.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Como outro exemplo, considere a função de biblioteca [Seq. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) :

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Você pode passar qualquer uma das sequências enumeráveis a seguir para esta função:

- Uma lista de listas
- Uma lista de matrizes
- Uma matriz de listas
- Uma matriz de sequências
- Qualquer outra combinação de sequências enumeráveis

O código a seguir `Seq.concat` usa o para demonstrar os cenários para os quais você pode dar suporte usando tipos flexíveis.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

A saída é a seguinte.

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

No F#, como em outras linguagens orientadas a objeto, há contextos nos quais tipos ou tipos derivados que implementam interfaces são convertidos automaticamente em um tipo base ou tipo de interface. Essas conversões automáticas ocorrem em argumentos diretos, mas não quando o tipo está em uma posição subordinada, como parte de um tipo mais complexo, como um tipo de retorno de um tipo de função, ou como um argumento de tipo. Assim, a notação de tipo flexível é útil principalmente quando o tipo para o qual você está aplicando faz parte de um tipo mais complexo.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Genéricos](./generics/index.md)
