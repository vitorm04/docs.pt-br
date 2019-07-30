---
title: Parâmetros de tipo resolvidos estaticamente
description: Saiba como usar um F# parâmetro de tipo estaticamente resolvido, que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução.
ms.date: 05/16/2016
ms.openlocfilehash: 43ed79b6e5f43a499a27b05e26472b021c455e44
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630587"
---
# <a name="statically-resolved-type-parameters"></a>Parâmetros de tipo resolvidos estaticamente

Um *parâmetro de tipo estaticamente resolvido* é um parâmetro de tipo que é substituído por um tipo real em tempo de compilação em vez de em tempo de execução. Elas são precedidas por um símbolo de acento circunflexo (^).

## <a name="syntax"></a>Sintaxe

```
ˆtype-parameter
```

## <a name="remarks"></a>Comentários

No F# idioma, há dois tipos distintos de parâmetros de tipo. O primeiro tipo é o parâmetro de tipo genérico padrão. Elas são indicadas por um apóstrofo ('), como em `'T` e `'U`. Eles são equivalentes a parâmetros de tipo genérico em outras linguagens de .NET Framework. O outro tipo é resolvido estaticamente e é indicado por um símbolo de cursor, como em `^T` e `^U`.

Parâmetros de tipo estaticamente resolvidos são úteis principalmente em conjunto com restrições de membro, que são restrições que permitem especificar que um argumento de tipo deve ter um membro específico ou membros para serem usados. Não é possível criar esse tipo de restrição usando um parâmetro de tipo genérico regular.

A tabela a seguir resume as semelhanças e diferenças entre os dois tipos de parâmetros de tipo.

|Recurso|Genérico|Resolvido estaticamente|
|-------|-------|-------------------|
|Sintaxe|`'T`, `'U`|`^T`, `^U`|
|Tempo de resolução|Tempo de execução|Tempo de compilação|
|Restrições de membro|Não pode ser usado com restrições de membro.|Pode ser usado com restrições de membro.|
|Geração de código|Um tipo (ou método) com parâmetros de tipo genérico padrão resulta na geração de um único tipo ou método genérico.|Várias instanciações de tipos e métodos são geradas, uma para cada tipo necessário.|
|Usar com tipos|Pode ser usado em tipos.|Não pode ser usado em tipos.|
|Usar com funções embutidas|Nº Uma função embutida não pode ser parametrizada com um parâmetro de tipo genérico padrão.|Sim. Parâmetros de tipo estaticamente resolvidos não podem ser usados em funções ou métodos que não são embutidos.|

Muitas F# funções de biblioteca principal, especialmente operadores, têm parâmetros de tipo estaticamente resolvidos. Essas funções e operadores são embutidos e resultam em uma geração de código eficiente para cálculos numéricos.

Os métodos embutidos e as funções que usam operadores ou usam outras funções que têm parâmetros de tipo estaticamente resolvidos também podem usar parâmetros de tipo estaticamente resolvidos. Geralmente, a inferência de tipos infere essas funções embutidas para ter parâmetros de tipo estaticamente resolvidos. O exemplo a seguir ilustra uma definição de operador que é inferida para ter um parâmetro de tipo estaticamente resolvido.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

O tipo resolvido de `(+@)` é baseado no uso `(+)` de e `(*)`, ambos, causam a inferência de tipos para inferir restrições de membro nos parâmetros de tipo estaticamente resolvidos. O tipo resolvido, conforme mostrado no F# intérprete, é o seguinte.

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

A F# partir do 4,1, você também pode especificar nomes de tipo concreto em assinaturas de parâmetro de tipo estaticamente resolvidas.  Nas versões anteriores do idioma, o nome do tipo poderia ser realmente inferido pelo compilador, mas não poderia ser realmente especificado na assinatura.  A partir F# de 4,1, você também pode especificar nomes de tipo concreto em assinaturas de parâmetro de tipo estaticamente resolvidas. Veja um exemplo:

```fsharp
let inline konst x _ = x

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

- [Genéricos](index.md)
- [Inferência de Tipos](../type-inference.md)
- [Generalização Automática](automatic-generalization.md)
- [Restrições](constraints.md)
- [Funções Embutidas](../functions/inline-functions.md)
