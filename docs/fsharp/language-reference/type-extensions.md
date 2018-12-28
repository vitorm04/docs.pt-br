---
title: Extensões de tipo
description: Saiba como F# extensões de tipo permitem que você adicionar novos membros a um tipo de objeto definido anteriormente.
ms.date: 07/20/2018
ms.openlocfilehash: 9c0c6247eb5b94e9f42377859026ba7b466eb2e4
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614039"
---
# <a name="type-extensions"></a>Extensões de tipo

As extensões de tipo (também chamado de _acréscimos_) são uma família de recursos que permitem que você adicione novos membros a um tipo de objeto definido anteriormente. Os três recursos são:

* Extensões de tipo intrínseco
* Extensões de tipo opcional
* Métodos de extensão

Cada um pode ser usada em cenários diferentes e tem diferentes vantagens e desvantagens.

## <a name="syntax"></a>Sintaxe

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [static] member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a>Extensões de tipo intrínseco

Uma extensão de tipo intrínseco é uma extensão de tipo que estende um tipo definido pelo usuário.

Extensões intrínsecas de tipo devem ser definidas no mesmo arquivo **e** no mesmo namespace ou módulo, como o tipo que estão estendendo. Qualquer outra definição resultará no que está sendo [extensões de tipo opcional](type-extensions.md#optional-type-extensions).

Extensões de tipo intrínseco, às vezes, são uma maneira mais limpa para separar a funcionalidade da declaração de tipo. O exemplo a seguir mostra como definir uma extensão de tipo intrínseco:

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

Usar uma extensão de tipo permite que você separe cada um dos seguintes:

* A declaração de um `Variant` tipo
* A funcionalidade para imprimir o `Variant` classe dependendo de sua "forma"
* Uma maneira de acessar a funcionalidade de impressão com estilo de objeto `.`-notação

Essa é uma alternativa para definir tudo como um membro em `Variant`. Embora não seja uma abordagem melhor inerentemente, ele pode ser uma representação mais clara de funcionalidade em algumas situações.

Extensões de tipo intrínseco são compiladas como membros do tipo eles aumentam e aparecem no tipo quando o tipo é examinado por reflexão.

## <a name="optional-type-extensions"></a>Extensões de tipo opcional

Uma extensão de tipo opcional é uma extensão que aparece fora do módulo, namespace ou assembly do tipo que está sendo estendido original.

Extensões de tipo opcionais são úteis para estender um tipo que você não definiu por conta própria. Por exemplo:

```fsharp
module Extensions

open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for i in 1 .. n do
                    yield x
        }
```

Agora você pode acessar `RepeatElements` como se fosse um membro do <xref:System.Collections.Generic.IEnumerable%601> desde que o `Extensions` módulo é aberto no escopo que você está trabalhando no.

As extensões opcionais não aparecem no tipo estendido quando examinado por reflexão. As extensões opcionais devem estar em módulos, e eles são somente no escopo quando o módulo que contém a extensão está aberto ou caso contrário, está no escopo.

Membros opcionais de extensão são compilados a membros estáticos para o qual a instância do objeto é transmitida implicitamente como primeiro parâmetro. No entanto, eles atuam como se fossem membros de instância ou os membros estáticos de acordo com como elas são declaradas.

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>Limitação genérica de extensões de tipo intrínseco e opcionais

É possível declarar uma extensão de tipo em um tipo genérico, em que a variável de tipo é restrito. O requisito é que a restrição da declaração de extensão corresponde à restrição do tipo declarado.

No entanto, mesmo quando as restrições são compatíveis entre um tipo de declaração e uma extensão de tipo, é possível para uma restrição ser inferido pelo corpo de um membro estendido que impõe um requisito diferente no parâmetro de tipo que o tipo declarado. Por exemplo:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

Não há nenhuma maneira de obter esse código funcione com uma extensão de tipo opcionais:

* Como é, o `Sum` membro tem uma restrição diferente no `'T` (`static member get_Zero` e `static member (+)`) que o que define a extensão de tipo.
* Modificando a extensão de tipo para ter a mesma restrição como `Sum` não será mais correspondente a restrição definida na `IEnumerable<'T>`.
* Fazer a alteração de membro a ser `member inline Sum` fornecerão um erro que restrições de tipo são incompatíveis

O que é desejado são métodos estáticos que "flutuem no espaço de" e podem ser apresentados como se eles estiverem estendendo um tipo. Isso é onde os métodos de extensão tornam-se necessário.

## <a name="extension-methods"></a>Métodos de extensão

Por fim, os métodos de extensão (às vezes chamado de "C# membros de extensão de estilo") pode ser declarado em F# como um método de membro estático em uma classe.

Métodos de extensão são úteis para quando você deseja definir as extensões em um tipo genérico que restringe a variável de tipo. Por exemplo:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Quando usado, esse código irá fazer com que pareça como se `Sum` é definido em <xref:System.Collections.Generic.IEnumerable%601>, desde que os `Extensions` foi aberto ou está no escopo.

## <a name="other-remarks"></a>Outros comentários

Extensões de tipo também tem os seguintes atributos:

* Pode ser estendido a qualquer tipo que pode ser acessado.
* Extensões de tipo intrínseco e opcional podem definir _qualquer_ tipo de membro, não apenas métodos. Portanto, as propriedades de extensão também são possíveis, por exemplo.
* O `self-identifier` token em de [sintaxe](type-extensions.md#syntax) representa a instância do tipo que está sendo invocado, assim como os membros comuns.
* Membros estendidos podem ser estáticos ou membros de instância.
* Variáveis de tipo em uma extensão de tipo devem corresponder as restrições do tipo declarado.

Também existem as seguintes limitações para extensões de tipo:

* Extensões de tipo não têm suporte para métodos virtuais ou abstratos.
* Extensões de tipo não dão suporte a métodos de substituição como acréscimos.
* Extensões de tipo não têm suporte [estaticamente parâmetros de tipo resolvidos](generics/statically-resolved-type-parameters.md).
* As extensões de tipo opcionais não têm suporte para construtores como acréscimos.
* Extensões de tipo não podem ser definidas [abreviações de tipo](type-abbreviations.md).
* Extensões de tipo não são válidas para `byref<'T>` (embora eles podem ser declarados).
* Extensões de tipo não são válidas para os atributos (embora eles podem ser declarados).
* Você pode definir as extensões que sobrecarregam outros métodos do mesmo nome, mas o F# compilador dá preferência a métodos sem extensão se não houver uma chamada ambígua.

Por fim, se existirem várias extensões de tipo intrínseco para um tipo, todos os membros devem ser exclusivos. Para extensões de tipo opcionais, membros em diferentes extensões de tipo para o mesmo tipo podem ter os mesmos nomes. Erros de ambiguidade surgem somente se o código do cliente abrir dois escopos diferentes que definem os mesmos nomes de membro.

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Membros](members/index.md)