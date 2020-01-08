---
title: Extensões de tipo
description: Saiba como F# as extensões de tipo permitem adicionar novos membros a um tipo de objeto definido anteriormente.
ms.date: 11/04/2019
ms.openlocfilehash: 3e2c6971156bd562ed5d5428e6b7ffdc520c4cf5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341564"
---
# <a name="type-extensions"></a>Extensões de tipo

Extensões de tipo (também chamadas de _aumentos_) são uma família de recursos que permitem adicionar novos membros a um tipo de objeto definido anteriormente. Os três recursos são:

- Extensões de tipo intrínseco
- Extensões de tipo opcionais
- Métodos de extensão

Cada um pode ser usado em diferentes cenários e tem compensações diferentes.

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

As extensões de tipo intrínseco devem ser definidas no mesmo arquivo **e** no mesmo namespace ou módulo que o tipo que está sendo estendido. Qualquer outra definição fará com que elas sejam [extensões de tipo opcionais](type-extensions.md#optional-type-extensions).

As extensões de tipo intrínseco, às vezes, são uma maneira mais limpa de separar a funcionalidade da declaração de tipo. O exemplo a seguir mostra como definir uma extensão de tipo intrínseco:

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

O uso de uma extensão de tipo permite que você separe cada uma das seguintes opções:

- A declaração de um tipo de `Variant`
- Funcionalidade para imprimir a classe `Variant` dependendo de sua "forma"
- Uma maneira de acessar a funcionalidade de impressão com a `.`-Notation de estilo de objeto

Essa é uma alternativa à definição de tudo como um membro em `Variant`. Embora não seja uma abordagem inerentemente melhor, pode ser uma representação mais limpa da funcionalidade em algumas situações.

As extensões de tipo intrínseco são compiladas como membros do tipo que aumentam e aparecem no tipo quando o tipo é examinado por reflexão.

## <a name="optional-type-extensions"></a>Extensões de tipo opcionais

Uma extensão de tipo opcional é uma extensão que aparece fora do módulo, namespace ou assembly original do tipo que está sendo estendido.

Extensões de tipo opcional são úteis para estender um tipo que você não definiu por conta própria. Por exemplo:

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

Agora você pode acessar `RepeatElements` como se fosse membro de <xref:System.Collections.Generic.IEnumerable%601>, desde que o módulo `Extensions` seja aberto no escopo no qual você está trabalhando.

As extensões opcionais não aparecem no tipo estendido quando examinadas por reflexão. As extensões opcionais devem estar em módulos e só estão no escopo quando o módulo que contém a extensão está aberto ou está no escopo.

Membros de extensão opcionais são compilados para membros estáticos para os quais a instância do objeto é passada implicitamente como o primeiro parâmetro. No entanto, eles atuam como se fossem membros de instância ou membros estáticos de acordo com o modo como eles são declarados.

Os membros de extensão opcionais também não C# são visíveis para os consumidores do ou Visual Basic. Eles só podem ser consumidos F# em outro código.

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a>Limitação genérica de extensões de tipo intrínsecas e opcionais

É possível declarar uma extensão de tipo em um tipo genérico em que a variável de tipo é restrita. O requisito é que a restrição da declaração de extensão corresponda à restrição do tipo declarado.

No entanto, mesmo quando as restrições são correspondidas entre um tipo declarado e uma extensão de tipo, é possível que uma restrição seja inferida pelo corpo de um membro estendido que impõe um requisito diferente no parâmetro de tipo do que o tipo declarado. Por exemplo:

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

Não há como obter esse código para trabalhar com uma extensão de tipo opcional:

- Como está, o membro `Sum` tem uma restrição diferente em `'T` (`static member get_Zero` e `static member (+)`) do que a extensão de tipo define.
- A modificação da extensão de tipo para ter a mesma restrição que `Sum` não corresponderá mais à restrição definida em `IEnumerable<'T>`.
- Alterar `member this.Sum` para `member inline this.Sum` dará um erro informando que as restrições de tipo são incompatíveis.

O que é desejado são métodos estáticos que "flutuam no espaço" e podem ser apresentados como se estivessem estendendo um tipo. É aí que os métodos de extensão se tornam necessários.

## <a name="extension-methods"></a>Métodos de extensão

Por fim, os métodos de extensão (C# às vezes chamados de "membros de extensão de F# estilo") podem ser declarados em como um método de membro estático em uma classe.

Os métodos de extensão são úteis para quando você deseja definir extensões em um tipo genérico que restringirá a variável de tipo. Por exemplo:

```fsharp
namespace Extensions

open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions() =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

Quando usado, esse código fará com que ele apareça como se `Sum` estiver definido em <xref:System.Collections.Generic.IEnumerable%601>, desde que `Extensions` tenha sido aberto ou esteja no escopo.

## <a name="other-remarks"></a>Outros comentários

As extensões de tipo também têm os seguintes atributos:

- Qualquer tipo que possa ser acessado pode ser estendido.
- Extensões intrínsecas e opcionais de tipo podem definir _qualquer_ tipo de membro, não apenas métodos. Portanto, as propriedades de extensão também são possíveis, por exemplo.
- O token `self-identifier` na [sintaxe](type-extensions.md#syntax) representa a instância do tipo que está sendo invocado, assim como os membros comuns.
- Os membros estendidos podem ser membros estáticos ou de instância.
- Variáveis de tipo em uma extensão de tipo devem corresponder às restrições do tipo declarado.

As seguintes limitações também existem para extensões de tipo:

- As extensões de tipo não dão suporte a métodos virtuais ou abstratos.
- As extensões de tipo não oferecem suporte a métodos de substituição como aumentos.
- As extensões de tipo não dão suporte a [parâmetros de tipo resolvidos estaticamente](./generics/statically-resolved-type-parameters.md).
- Extensões de tipo opcional não dão suporte a construtores como aumentos.
- Extensões de tipo não podem ser definidas em [abreviações de tipo](type-abbreviations.md).
- Extensões de tipo não são válidas para `byref<'T>` (embora possam ser declaradas).
- Extensões de tipo não são válidas para atributos (embora possam ser declaradas).
- Você pode definir extensões que sobrecarregam outros métodos de mesmo nome, mas F# o compilador dá preferência a métodos que não são de extensão se houver uma chamada ambígua.

Por fim, se existirem várias extensões de tipo intrínsecos para um tipo, todos os membros deverão ser exclusivos. Para extensões de tipo opcionais, os membros em extensões de tipo diferentes para o mesmo tipo podem ter os mesmos nomes. Os erros de ambiguidade ocorrem somente se o código do cliente abrir dois escopos diferentes que definem os mesmos nomes de membro.

## <a name="see-also"></a>Veja também

- [Referência da Linguagem F#](index.md)
- [Membros](./members/index.md)
