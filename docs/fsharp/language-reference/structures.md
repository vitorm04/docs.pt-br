---
title: Estruturas
description: Aprenda sobre a estrutura F#, um tipo de objeto compacto muitas vezes mais eficiente do que uma classe para tipos com uma pequena quantidade de dados e comportamento simples.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400277"
---
# <a name="structures"></a>Estruturas

Uma *estrutura* é um tipo de objeto compacto que pode ser mais eficiente do que uma classe para tipos que têm uma pequena quantidade de dados e comportamento simples.

## <a name="syntax"></a>Sintaxe

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a>Comentários

Estruturas são *tipos de valor,* o que significa que são armazenadas diretamente na pilha ou, quando são usadas como campos ou elementos de matriz, inline no tipo pai. Ao contrário de classes e registros, as estruturas têm semântica de passar-por-valor. Isso significa que elas são úteis principalmente para pequenos agregados de dados que são acessados e copiados com frequência.

Na sintaxe anterior, duas formas são mostradas. A primeira não é a sintaxe leve, mas ela é usada com frequência, pois quando você usa as palavras-chave `struct` e `end`, é possível omitir o atributo `StructAttribute`, que aparece na segunda forma. É possível abreviar `StructAttribute` como apenas `Struct`.

A *definição de tipo-elementos-e-membros* na sintaxe anterior representa declarações e definições de membros. As estruturas podem ter construtores e campos mutáveis e imutáveis e podem declarar membros e implementações de interface. Para obter mais informações, consulte [Membros](./members/index.md).

As estruturas não podem participar da herança, não podem conter associações `let` ou `do` e não podem conter recursivamente campos de seu próprio tipo (embora possam conter células de referência que fazem referência ao seu próprio tipo).

Como as estruturas não permitem associações `let`, você deve declarar campos em estruturas usando a palavra-chave `val`. A palavra-chave `val` define um campo e seu tipo, mas não permite inicialização. Em vez disso, as declarações `val` são inicializadas como zero ou nulo. Por esse motivo, as estruturas que possuem um construtor implícito (ou seja, parâmetros que são fornecidos imediatamente após o nome da estrutura na declaração) requerem que declarações `val` sejam anotadas com o atributo `DefaultValue`. As estruturas que tenham um construtor definido ainda oferecem suporte à inicialização como zero. Portanto, o atributo `DefaultValue` é uma declaração de que um valor zero é válido para o campo. Construtores implícitos para estruturas não executam nenhuma ação, pois as associações `let` e `do` não são permitidas no tipo, mas os valores de parâmetro construtor implícito passados estão disponíveis como campos particulares.

Construtores explícitos podem envolver inicialização de valores do campo. Quando você tem uma estrutura que possui um construtor explícito, ela ainda suporta inicialização como zero; no entanto, você não usa o atributo `DefaultValue` nas declarações `val`, pois ela entra em conflito com o construtor explícito. Para obter `val` mais informações sobre declarações, consulte [Explicit Fields: `val` The Keyword](./members/explicit-fields-the-val-keyword.md).

Modificadores de atributos e de acessibilidade são permitidos em estruturas e seguem as mesmas regras dos outros tipos. Para obter mais informações, consulte [Atributos](attributes.md) e [Controle de Acesso](access-control.md).

Os exemplos de código a seguir ilustram definições de estrutura.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a>Structs ByRefLike

Você pode definir suas próprias estruturas `byref`que podem aderir à semântica semelhante: consulte [Byrefs](byrefs.md) para obter mais informações. Isso é feito <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> com o atributo:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`não implica `Struct`. Ambos devem estar presentes no tipo.

Uma`byref`estrutura " -like" em F# é um tipo de valor vinculado à pilha. Ele nunca é alocado no monte gerenciado. Uma `byref`estrutura semelhante é útil para programação de alto desempenho, pois é aplicada com um conjunto de verificações fortes sobre a vida útil e a não captura. As regras são:

- Eles podem ser usados como parâmetros de função, parâmetros de método, variáveis locais, retornos do método.
- Eles não podem ser membros estáticos ou de instância de uma classe ou estrutura normal.
- Eles não podem ser capturados`async` por qualquer construção de fechamento (métodos ou expressões lambda).
- Eles não podem ser usados como parâmetro genérico.

Embora essas regras restrinjam fortemente o uso, eles o fazem para cumprir a promessa de computação de alto desempenho de forma segura.

## <a name="readonly-structs"></a>ReadOnly structs

Você pode anotar estruturas com o <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atributo. Por exemplo: 

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsReadOnly`não implica `Struct`. Você deve adicionar ambos `IsReadOnly` para ter uma estrutura.

O uso deste atributo emite metadados permitindo que `inref<'T>` `in ref`F# e C# saibam tratá-lo como e, respectivamente.

Definir um valor mutável dentro de uma estrutura somente leitura produz um erro.

## <a name="struct-records-and-discriminated-unions"></a>Registros de estrutura e sindicatos discriminados

Você pode representar [registros](records.md) e [sindicatos discriminados](discriminated-unions.md) como estruturas com o atributo. `[<Struct>]`  Veja cada artigo para saber mais.

## <a name="see-also"></a>Confira também

- [Referência de idioma F#](index.md)
- [Classes](classes.md)
- [Registros](records.md)
- [Membros](./members/index.md)
