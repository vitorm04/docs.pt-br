---
title: Associações let em classes (F#)
description: "Saiba como definir campos particulares e funções privadas para classes de F # usando associações 'let' na definição de classe."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c4511a541403dde517acaf902e86de8d48f13781
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="let-bindings-in-classes"></a>Associações let em classes

Você pode definir funções privadas para classes de F # e campos particulares usando `let` associações na definição de classe.


## <a name="syntax"></a>Sintaxe

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Comentários
A sintaxe anterior é exibido após as declarações de título e herança de classe, mas antes de quaisquer definições de membro. A sintaxe é semelhante de `let` associações fora de classes, mas os nomes definidos em uma classe têm um escopo limitado à classe. Um `let` associação cria um campo particular ou uma função; para expor dados ou funções publicamente, declarar uma propriedade ou um método de membro.

Um `let` que a associação não é estático é chamado de uma instância `let` associação. Instância `let` associações executar quando objetos são criados. Estático `let` associações fazem parte do inicializador estático da classe, que é garantido para executar antes que o tipo é usado pela primeira vez.

O código na instância `let` associações podem usar os parâmetros do construtor primário.

Atributos e modificadores de acessibilidade não são permitidos em `let` associações em classes.

Os exemplos de código a seguir ilustram a vários tipos de `let` associações em classes.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

A saída é a seguinte.

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Maneiras alternativas de criar campos
Você também pode usar o `val` palavra-chave para criar um campo particular. Ao usar o `val` palavra-chave, o campo não tem um valor quando o objeto é criado, mas em vez disso, é inicializado com um valor padrão. Para obter mais informações, consulte [campos explícitos: A val palavra-chave](explicit-fields-the-val-keyword.md).

Você também pode definir campos particulares em uma classe usando uma definição de membro e adicionando a palavra-chave `private` na definição. Isso pode ser útil se você pretende alterar a acessibilidade de um membro sem recriação de seu código. Para saber mais, veja [Controle de acesso](../access-control.md).

## <a name="see-also"></a>Consulte também
[Membros](index.md)

[`do`Associações em Classes](do-bindings-in-classes.md)

[`let` Associações](../functions/let-bindings.md)
