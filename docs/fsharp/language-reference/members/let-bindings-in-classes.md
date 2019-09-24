---
title: Associações let em classes
description: Saiba como definir campos privados e funções particulares para F# classes usando associações ' Let ' na definição de classe.
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216524"
---
# <a name="let-bindings-in-classes"></a>Associações let em classes

Você pode definir campos privados e funções particulares para F# classes usando `let` associações na definição de classe.

## <a name="syntax"></a>Sintaxe

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Comentários

A sintaxe anterior aparece depois do cabeçalho da classe e das declarações de herança, mas antes de qualquer definição de membro. A sintaxe é como a de `let` associações fora de classes, mas os nomes definidos em uma classe têm um escopo limitado à classe. Uma `let` associação cria um campo ou função particular; para expor dados ou funções publicamente, declare uma propriedade ou um método de membro.

Uma `let` associação que não é estática é chamada de associação `let` de instância. As `let` associações de instância são executadas quando objetos são criados. As `let` associações estáticas fazem parte do inicializador estático para a classe, que tem a garantia de executar antes de o tipo ser usado pela primeira vez.

O código dentro das `let` associações de instância pode usar os parâmetros do construtor primário.

Os modificadores de atributos e de acessibilidade não `let` são permitidos em associações em classes.

Os exemplos de código a seguir ilustram `let` vários tipos de associações em classes.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

A saída é a seguinte.

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Maneiras alternativas de criar campos

Você também pode usar a `val` palavra-chave para criar um campo privado. Ao usar a `val` palavra-chave, o campo não recebe um valor quando o objeto é criado, mas, em vez disso, é inicializado com um valor padrão. Para obter mais informações, [consulte campos explícitos: A palavra-](explicit-fields-the-val-keyword.md)chave Val.

Você também pode definir campos privados em uma classe usando uma definição de membro e adicionando a palavra `private` -chave à definição. Isso pode ser útil se você espera alterar a acessibilidade de um membro sem reescrever seu código. Para saber mais, veja [Controle de acesso](../access-control.md).

## <a name="see-also"></a>Consulte também

- [Membros](index.md)
- [`do`Associações em Classes](do-bindings-in-classes.md)
- [`let`Associações](../functions/let-bindings.md)
