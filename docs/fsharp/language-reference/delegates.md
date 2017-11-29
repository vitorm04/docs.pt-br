---
title: Delegados (F#)
description: 'Aprenda a trabalhar com delegados em F #.'
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 719948a3-83ba-4618-82d6-a22945c3f4b0
ms.openlocfilehash: c929a342ab4c5098062417691a99cee3b007d2d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a>Delegados

Um delegado representa uma chamada de função como um objeto. Em F #, você normalmente deve usar valores de função para representar a funções como valores de primeira classe; No entanto, os delegados são usados no .NET Framework e então são necessários para interagir com as APIs que espera que eles. Eles também podem ser usados quando criação bibliotecas projetadas para usam em outras linguagens do .NET Framework.


## <a name="syntax"></a>Sintaxe

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Comentários
Na sintaxe anterior, `type1` representa o tipo de argumento ou tipos e `type2` representa o tipo de retorno. Os tipos de argumento são representados por `type1` na forma curried automaticamente. Isso sugere que para esse tipo de você usar um formulário de tupla se os argumentos da função de destino estão na forma curried e uma tupla entre parênteses para argumentos que já estão na forma de tupla. O currying automático remove um conjunto de parênteses, deixando um argumento de tupla que coincide com o método de destino. Consulte o exemplo de código para a sintaxe que deve ser usada em cada caso.

Delegados podem ser anexados a F # valores de função e estáticos ou métodos de instância. Valores de função do F # podem ser passados diretamente como argumentos para delegar a construtores. Para um método estático, você pode construir o delegado usando o nome da classe e o método. Para um método de instância, você pode fornecer a instância do objeto e o método em um argumento. Em ambos os casos, o membro acessar operador (`.`) é usado.

O `Invoke` método no tipo de delegado chama a função encapsulada. Além disso, os delegados podem ser passados como valores de função referenciando o nome do método Invoke sem os parênteses.

O código a seguir mostra a sintaxe para criar delegados que representam vários métodos em uma classe. Dependendo se o método é um método estático ou um método de instância, e se ele tem argumentos de tupla ou no formulário na forma curried, a sintaxe para declarar e atribuir o delegado é um pouco diferente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

O código a seguir mostra algumas das diferentes maneiras de que trabalhar com delegados.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

A saída de exemplo de código anterior é da seguinte maneira.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Parâmetros e Argumentos](parameters-and-arguments.md)

[Eventos](members/events.md)
