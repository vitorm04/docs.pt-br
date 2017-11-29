---
title: "Campos explícitos: a palavra-chave val (F#)"
description: "Saiba mais sobre F # 'val' palavra-chave, que é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura sem inicializar o tipo."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3bdbc745-436b-407f-bf54-5d11ca829cd0
ms.openlocfilehash: cee53a48f08aec89b0bdd40189ed331cadee877d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="explicit-fields-the-val-keyword"></a>Campos explícitos: a palavra-chave val

O `val` palavra-chave é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura, sem inicializá-la. Locais de armazenamento declarados dessa maneira são chamadas *campos explícitos*. Outro uso do `val` palavra-chave é em conjunto com o `member` palavra-chave para declarar uma propriedade implementada automaticamente. Para obter mais informações sobre propriedades implementadas automaticamente, consulte [propriedades](properties.md).


## <a name="syntax"></a>Sintaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Comentários
A maneira usual para definir campos em um tipo de classe ou estrutura é usar um `let` associação. No entanto, `let` associações devem ser inicializadas como parte do construtor de classe, que não é sempre possível, necessária ou desejada. Você pode usar o `val` palavra-chave quando desejar que um campo que não foi inicializado.

Campos explícitos podem ser estático ou não-estático. O *modificador de acesso* pode ser `public`, `private`, ou `internal`. Por padrão, os campos explícitos são públicos. Isso é diferente do `let` associações em classes, que são sempre privadas.

O [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atributo é necessário em campos explícitos em tipos de classe que tem um construtor primário. Esse atributo especifica que o campo é inicializado a zero. O tipo do campo deve oferecer suporte a inicialização de zero. Um tipo oferece suporte à inicialização zero se ele for um dos seguintes:

- Um tipo primitivo que tem um valor igual a zero.

- Um tipo que oferece suporte a um valor nulo, como um valor normal, como um valor anormal ou como uma representação de um valor. Isso inclui classes, tuplas, registros, funções, interfaces, tipos de referência do .NET, o `unit` tipo e tipos de união discriminados.

- Um tipo de valor de .NET.

- Uma estrutura cujos todos campos suportam a um padrão de valor zero.


Por exemplo, um campo imutável chamado `someField` tem um campo existente no .NET compilados representação com o nome `someField@`, e você acessar o valor armazenado usando uma propriedade chamada `someField`.

Para um campo mutável, a representação do .NET compilado é um campo de .NET.


>[!WARNING] 
`Note`O namespace do .NET Framework `System.ComponentModel` contém um atributo que tem o mesmo nome. Para obter informações sobre esse atributo, consulte `System.ComponentModel.DefaultValueAttribute`.


O código a seguir mostra o uso de campos explícitos e, para comparação, um `let` associação em uma classe que tem um construtor primário. Observe que o `let`-campo associado `myInt1` é privado. Quando o `let`-campo associado `myInt1` é referenciado por um método de membro, o identificador automático `this` não é necessária. Mas quando você está fazendo referência os campos explícitos `myInt2` e `myString`, o identificador de autoatendimento é necessário.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

A saída é a seguinte:

```
11 12 abc
30 def
```

O código a seguir mostra o uso de campos explícitos em uma classe que não tem um construtor primário. Nesse caso, o `DefaultValue` atributo não é necessário, mas todos os campos devem ser inicializados em construtores definidos para o tipo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

A saída é `35 22`.

O código a seguir mostra o uso de campos explícitos em uma estrutura. Como uma estrutura é um tipo de valor, ela automaticamente tem um construtor padrão que define os valores de seus campos como zero. Portanto, o `DefaultValue` atributo não é necessário.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

A saída é `11 xyz`.

Campos explícitos não se destinam ao uso de rotina. Em geral, quando for possível usar um `let` associação em uma classe em vez de um campo explícita. Campos explícitos são úteis em determinados cenários de interoperabilidade, como quando você precisa definir uma estrutura que será usada em uma plataforma de invocar a chamada para uma API nativa ou em cenários de interoperabilidade COM. Para obter mais informações, consulte [funções externas](../functions/external-functions.md). Outra situação em que um campo explícito pode ser necessário é quando você estiver trabalhando com um gerador de código F # que emite classes sem um construtor primário. Campos explícitos também são úteis para variáveis de thread estático ou construções semelhantes. Para obter mais informações, consulte `System.ThreadStaticAttribute`.

Quando as palavras-chave `member val` aparecem juntos em uma definição de tipo, que é uma definição de uma propriedade implementada automaticamente. Para obter mais informações, consulte [propriedades](properties.md).


## <a name="see-also"></a>Consulte também
[Propriedades](properties.md)

[Membros](index.md)

[`let`Associações em Classes](let-bindings-in-classes.md)
