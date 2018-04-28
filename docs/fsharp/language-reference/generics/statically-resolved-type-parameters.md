---
title: Parâmetros de tipo resolvidos estaticamente (F#)
description: 'Saiba como usar uma linguagem F # parâmetro de tipo resolvidos estaticamente, que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da730014f1c40b6c79d72e4f46a18ef36f50de36
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="statically-resolved-type-parameters"></a>Parâmetros de tipo resolvidos estaticamente

Um *parâmetro de tipo resolvidos estaticamente* é um parâmetro de tipo que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução. Eles são precedidos por um símbolo de acento circunflexo (^).


## <a name="syntax"></a>Sintaxe

```
ˆtype-parameter
```

## <a name="remarks"></a>Comentários
Na linguagem F #, há dois tipos distintos de parâmetros de tipo. O primeiro tipo é o parâmetro de tipo genérico padrão. Esses são indicadas por um apóstrofo ('), como em `'T` e `'U`. Eles são equivalentes aos parâmetros de tipo genérico em outras linguagens do .NET Framework. O outro tipo é resolvido estaticamente e é indicado por um símbolo de cursor, como em `^T` e `^U`.

Parâmetros de tipo resolvidos estaticamente são útil principalmente em conjunto com as restrições de membro, que são as restrições que permitem que você especifique que um argumento de tipo deve ter um determinado membro ou membros para ser usado. Não há nenhuma maneira de criar esse tipo de restrição usando um parâmetro de tipo genérico regular.

A tabela a seguir resume as semelhanças e diferenças entre os dois tipos de parâmetros de tipo.

|Recurso|Genérico|Resolvidos estaticamente|
|-------|-------|-------------------|
|Sintaxe|`'T`, `'U`|`^T`, `^U`|
|Tempo de resolução|Tempo de execução|Tempo de compilação|
|Restrições de membro|Não pode ser usado com restrições de membro.|Pode ser usado com restrições de membro.|
|Geração de código|Um tipo (ou método) com parâmetros de tipo genérico padrão resulta na geração de um único tipo genérico ou método.|Várias instâncias de tipos e métodos são geradas, uma para cada tipo que é necessária.|
|Use com tipos|Pode ser usada em tipos.|Não pode ser usada em tipos.|
|Use com funções embutidas|Nº Uma função embutida não pode ser parametrizada com um parâmetro de tipo genérico padrão.|Sim. Parâmetros de tipo resolvidos estaticamente não podem ser usados em funções ou métodos que não são embutidos.|

Muitos F # principais funções de biblioteca, principalmente operadores, estaticamente resolveu parâmetros de tipo. Esses operadores e funções internas e resultam na geração de código eficiente para cálculos numéricos.

Métodos embutidos e funções que usam operadores, ou usar outras funções que têm parâmetros de tipo, resolvidos estaticamente também podem usar parâmetros de tipo resolvidos estaticamente próprios. Muitas vezes, a inferência de tipo infere tais funções embutidas para ter parâmetros de tipo resolvidos estaticamente. O exemplo a seguir ilustra uma definição de operador é inferida para ter um parâmetro de tipo resolvidos estaticamente.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

O tipo resolvido de `(+@)` baseia-se no uso de ambos `(+)` e `(*)`, ambos do que fazer com que a inferência de tipos inferir restrições de membro em parâmetros de tipo resolvidos estaticamente. O tipo resolvido, conforme o interpretador de F #, é o seguinte.

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

A saída é a seguinte.

```
2
1.500000
```

A partir do F # 4.1, você pode também especificar nomes de tipo concreto em assinaturas de parâmetro de tipo resolvidos estaticamente.  Nas versões anteriores do idioma, o nome do tipo, na verdade, pode ser inferido pelo compilador, mas, na verdade, não pôde ser especificado na assinatura.  A partir do F # 4.1, você também pode especificar nomes de tipo concreto em assinaturas de parâmetro de tipo resolvidos estaticamente. Veja um exemplo:

```fsharp
type CFunctor() = 
      static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
      static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

      // default implementation of replace
      static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

      // call overridden replace if present
      static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
      ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a>Consulte também
[Genéricos](index.md)

[Inferência de Tipos](../type-inference.md)

[Generalização Automática](automatic-generalization.md)

[Restrições](constraints.md)

[Funções Embutidas](../functions/inline-functions.md)
