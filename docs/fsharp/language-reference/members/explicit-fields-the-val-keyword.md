---
title: 'Campos explícitos: a palavra-chave val (F#)'
description: "Saiba mais sobre o F # 'val' palavra-chave, que é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura sem inicializar o tipo."
ms.date: 05/16/2016
ms.openlocfilehash: 9cd06f7e90192be79490dd0ff67f118cce4339c3
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569993"
---
# <a name="explicit-fields-the-val-keyword"></a>Campos explícitos: a palavra-chave val

O `val` palavra-chave é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura, sem inicializá-la. Locais de armazenamento declarados dessa maneira são chamadas *campos explícitos*. Outro uso do `val` palavra-chave é em conjunto com o `member` palavra-chave para declarar uma propriedade implementada automaticamente. Para obter mais informações sobre Propriedades autoimplementadas, consulte [propriedades](properties.md).

## <a name="syntax"></a>Sintaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Comentários

Da maneira usual para definir os campos em um tipo de classe ou estrutura é usar um `let` associação. No entanto, `let` associações devem ser inicializadas como parte do construtor de classe, nem sempre é possível, necessário ou desejável. Você pode usar o `val` palavra-chave quando você quiser que um campo que não foi inicializado.

Campos explícitos podem ser estático ou não estático. O *modificador de acesso* pode ser `public`, `private`, ou `internal`. Por padrão, os campos explícitos são públicos. Isso é diferente de `let` associações em classes, que são sempre privadas.

O [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atributo é necessário em campos explícitos em tipos de classe que tem um construtor primário. Esse atributo especifica que o campo é inicializado como zero. O tipo do campo deve oferecer suporte a inicialização como zero. Um tipo que suporta inicialização como zero se for um dos seguintes:

- Um tipo primitivo que tem um valor igual a zero.

- Um tipo que dá suporte a um valor nulo, como um valor normal, como um valor anormal ou como uma representação de um valor. Isso inclui classes, as tuplas, registros, funções, interfaces e tipos de referência do .NET, o `unit` tipo e tipos de união discriminados.

- Um tipo de valor do .NET.

- Uma estrutura cujos todos os campos dar suporte a um padrão valor igual a zero.

Por exemplo, um campo imutável chamado `someField` tem um campo de suporte no .NET compilado representação com o nome `someField@`, e você acessar o valor armazenado usando uma propriedade chamada `someField`.

Para um campo mutável, a representação de .NET compilado é um campo de .NET.

>[!WARNING]
`Note` O namespace do .NET Framework `System.ComponentModel` contém um atributo que tem o mesmo nome. Para obter informações sobre esse atributo, consulte `System.ComponentModel.DefaultValueAttribute`.

O código a seguir mostra o uso de campos explícitos e, para comparação, um `let` de associação em uma classe que tem um construtor primário. Observe que o `let`-campo associado `myInt1` é privado. Quando o `let`-campo associado `myInt1` referenciado a partir de um método de membro, o identificador de self `this` não é necessária. Mas quando você está fazendo referência os campos explícitos `myInt2` e `myString`, o identificador de self é necessário.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

A saída é a seguinte:

```
11 12 abc
30 def
```

O código a seguir mostra o uso de campos explícitos em uma classe que não tem um construtor primário. Nesse caso, o `DefaultValue` atributo não for necessário, mas todos os campos devem ser inicializados nos construtores que são definidos para o tipo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

A saída é `35 22`.

O código a seguir mostra o uso de campos explícitos em uma estrutura. Como uma estrutura é um tipo de valor, ele automaticamente tem um construtor padrão que define os valores de seus campos como zero. Portanto, o `DefaultValue` atributo não é necessário.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

A saída é `11 xyz`.

Campos explícitos não se destinam ao uso de rotina. Em geral, quando for possível usar um `let` de associação em uma classe em vez de um campo explícitas. Campos explícitos são úteis em determinados cenários de interoperabilidade, como quando for necessário definir uma estrutura que será usada em uma invocação de plataforma chamada a uma API nativa, ou em cenários de interoperabilidade COM. Para obter mais informações, consulte [funções externas](../functions/external-functions.md). Outra situação em que um campo explícito pode ser necessário é quando você estiver trabalhando com um gerador de código F # que emite classes sem um construtor primário. Campos explícitos também são úteis para variáveis de thread estático ou construções semelhantes. Para obter mais informações, consulte `System.ThreadStaticAttribute`.

Quando as palavras-chave `member val` aparecem juntos em uma definição de tipo, ele é uma definição de uma propriedade implementada automaticamente. Para obter mais informações, consulte [propriedades](properties.md).

## <a name="see-also"></a>Consulte também

- [Propriedades](properties.md)
- [Membros](index.md)
- [`let`Associações em Classes](let-bindings-in-classes.md)
