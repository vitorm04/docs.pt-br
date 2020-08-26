---
title: 'Campos explícitos: a palavra-chave val'
description: "Saiba mais sobre a palavra-chave ' Val ' de F #, que é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura sem inicializar o tipo."
ms.date: 08/15/2020
ms.openlocfilehash: 9f5599a241f27b234eeacf48327b4ccbc46ed38c
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811776"
---
# <a name="explicit-fields-the-val-keyword"></a>Campos explícitos: a palavra-chave val

A `val` palavra-chave é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura, sem inicializá-lo. Os locais de armazenamento declarados dessa maneira são chamados de *campos explícitos*. Outro uso da `val` palavra-chave é em conjunto com a `member` palavra-chave para declarar uma propriedade implementada automaticamente. Para obter mais informações sobre propriedades implementadas automaticamente, consulte [Propriedades](properties.md).

## <a name="syntax"></a>Sintaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Comentários

A maneira usual de definir campos em um tipo de classe ou estrutura é usar uma `let` associação. No entanto, as `let` associações devem ser inicializadas como parte do construtor da classe, o que nem sempre é possível, necessário ou desejável. Você pode usar a `val` palavra-chave quando desejar um campo que não foi inicializado.

Os campos explícitos podem ser estáticos ou não estáticos. O *modificador de acesso* pode ser `public` , `private` ou `internal` . Por padrão, os campos explícitos são públicos. Isso difere das `let` associações em classes, que são sempre particulares.

O atributo [DefaultValue](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-defaultvalueattribute.html) é necessário em campos explícitos em tipos de classe que têm um construtor principal. Esse atributo especifica que o campo é inicializado como zero. O tipo do campo deve dar suporte à inicialização zero. Um tipo oferece suporte à inicialização zero se for um dos seguintes:

- Um tipo primitivo que tem um valor zero.
- Um tipo que dá suporte a um valor nulo, seja como um valor normal, como um valor anormal, ou como uma representação de um valor. Isso inclui classes, tuplas, registros, funções, interfaces, tipos de referência do .NET, `unit` tipo e tipos de União discriminados.
- Um tipo de valor do .NET.
- Uma estrutura cujos campos oferecem suporte a um valor zero padrão.

Por exemplo, um campo imutável chamado `someField` tem um campo de apoio na representação compilada do .NET com o nome `someField@` e você acessa o valor armazenado usando uma propriedade chamada `someField` .

Para um campo mutável, a representação compilada do .NET é um campo .NET.

> [!WARNING]
> O namespace .NET Framework `System.ComponentModel` contém um atributo que tem o mesmo nome. Para obter informações sobre esse atributo, consulte <xref:System.ComponentModel.DefaultValueAttribute> .

O código a seguir mostra o uso de campos explícitos e, para comparação, uma `let` associação em uma classe que tem um construtor principal. Observe que o `let` campo-Bound `myInt1` é privado. Quando o `let` campo-Bound `myInt1` é referenciado de um método de membro, o autoidentifier `this` não é necessário. Mas quando você está fazendo referência a campos explícitos `myInt2` e `myString` , o autoidentifier é necessário.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

A saída é da seguinte maneira:

```console
11 12 abc
30 def
```

O código a seguir mostra o uso de campos explícitos em uma classe que não tem um construtor principal. Nesse caso, o `DefaultValue` atributo não é necessário, mas todos os campos devem ser inicializados nos construtores que são definidos para o tipo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

A saída é `35 22`.

O código a seguir mostra o uso de campos explícitos em uma estrutura. Como uma estrutura é um tipo de valor, ela automaticamente tem um construtor sem parâmetros que define os valores de seus campos como zero. Portanto, o `DefaultValue` atributo não é necessário.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

A saída é `11 xyz`.

**Cuidado**. se você for inicializar sua estrutura com `mutable` campos sem `mutable` palavra-chave, suas atribuições funcionarão em uma cópia da estrutura que será descartada logo após a atribuição. Portanto, sua estrutura não será alterada.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Os campos explícitos não são destinados ao uso de rotina. Em geral, quando possível, você deve usar uma `let` associação em uma classe em vez de um campo explícito. Os campos explícitos são úteis em determinados cenários de interoperabilidade, como quando você precisa definir uma estrutura que será usada em uma chamada de plataforma Invoke para uma API nativa ou em cenários de interoperabilidade COM. Para obter mais informações, consulte [external Functions](../functions/external-functions.md). Outra situação em que um campo explícito pode ser necessário é quando você está trabalhando com um gerador de código F # que emite classes sem um construtor principal. Os campos explícitos também são úteis para variáveis de thread estático ou construções semelhantes. Para obter mais informações, consulte `System.ThreadStaticAttribute`.

Quando as palavras-chave `member val` aparecem juntas em uma definição de tipo, é uma definição de uma propriedade implementada automaticamente. Para obter mais informações, consulte [Propriedades](properties.md).

## <a name="see-also"></a>Confira também

- [Propriedades](properties.md)
- [Membros](index.md)
- [`let` Associações em classes](let-bindings-in-classes.md)
