---
title: Associações let em classes (F#)
description: "Saiba como definir campos particulares e funções privadas para classes de F # por meio de associações 'let' na definição de classe."
ms.date: 05/16/2016
ms.openlocfilehash: 237eb98a57571a21c9187abf31f05160374cf4fc
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972866"
---
# <a name="let-bindings-in-classes"></a>Associações let em classes

Você pode definir campos particulares e funções privadas para classes de F # usando `let` associações na definição de classe.

## <a name="syntax"></a>Sintaxe

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Comentários

A sintaxe anterior é exibido após as declarações de título e a herança de classe, mas antes das definições de membro. A sintaxe é semelhante à de `let` associações fora de classes, mas os nomes definidos em uma classe têm um escopo limitado à classe. Um `let` associação cria um campo particular ou uma função; a exposição de dados ou funções publicamente, declarar uma propriedade ou um método de membro.

Um `let` que a associação não é estático é chamado de uma instância `let` associação. Instância `let` associações executar quando objetos são criados. Estático `let` associações fazem parte do inicializador estático para a classe, que é a garantia de serem executados antes que o tipo é usado pela primeira vez.

O código dentro de instância `let` associações podem usar os parâmetros do construtor primário.

Atributos e modificadores de acessibilidade não são permitidas em `let` associações em classes.

Os exemplos de código a seguir ilustram vários tipos de `let` associações em classes.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

A saída é a seguinte.

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Maneiras alternativas de criar campos

Você também pode usar o `val` palavra-chave para criar um campo particular. Ao usar o `val` palavra-chave, o campo não recebe um valor quando o objeto é criado, mas em vez disso, é inicializado com um valor padrão. Para obter mais informações, consulte [campos explícitos: A val palavra-chave](explicit-fields-the-val-keyword.md).

Você também pode definir campos privados em uma classe usando uma definição de membro e adicionando a palavra-chave `private` à definição. Isso pode ser útil se você pretende alterar a acessibilidade de um membro sem reescrever seu código. Para saber mais, veja [Controle de acesso](../access-control.md).

## <a name="see-also"></a>Consulte também

- [Membros](index.md)
- [`do`Associações em Classes](do-bindings-in-classes.md)
- [`let` Associações](../functions/let-bindings.md)
