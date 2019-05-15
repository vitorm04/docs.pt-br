---
title: Delegados
description: Saiba como trabalhar com delegados em F#.
ms.date: 05/16/2016
ms.openlocfilehash: 0596b67530b0399df41dffdf855a07bce2bf4761
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641979"
---
# <a name="delegates"></a>Delegados

Um delegado representa uma chamada de função como um objeto. No F#, você normalmente deve usar valores de função para representar funções como valores de primeira classe; No entanto, delegados são usados no .NET Framework e então, são necessárias ao interoperar com APIs que esperam-los. Eles também podem ser usados quando a criação de bibliotecas projetadas para usam de outros idiomas do .NET Framework.

## <a name="syntax"></a>Sintaxe

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, `type1` representa o tipo de argumento ou tipos e `type2` representa o tipo de retorno. Os tipos de argumento são representados por `type1` via currying automaticamente. Isso sugere que, para esse tipo de você usar um formulário de tupla se os argumentos da função de destino são via currying e uma tupla entre parênteses para argumentos que já estão no formulário de tupla. O currying automática remove um conjunto de parênteses, deixando um argumento de tupla que corresponde ao método de destino. Consulte o exemplo de código para a sintaxe que deve ser usada em cada caso.

Delegados podem ser anexados a F# função de valores e static ou métodos de instância. F#os valores de função podem ser passados diretamente como argumentos para delegar a construtores. Para um método estático, você pode construir o delegado usando o nome da classe e o método. Para um método de instância, você pode fornecer a instância do objeto e o método em um argumento. Em ambos os casos, o membro do operador de acesso (`.`) é usado.

O `Invoke` método no tipo de delegado chama a função encapsulada. Além disso, os delegados podem ser passados como valores de função referenciando o nome do método Invoke sem parênteses.

O código a seguir mostra a sintaxe para criar representantes que representam vários métodos em uma classe. Dependendo se o método é um método estático ou um método de instância, e se ele tem argumentos nos formulários na forma curried ou o formulário de tupla, a sintaxe para declarar e atribuir o delegado é um pouco diferente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

O código a seguir mostra algumas das diferentes maneiras que você pode trabalhar com delegados.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

A saída do exemplo de código anterior é da seguinte maneira.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Parâmetros e Argumentos](parameters-and-arguments.md)
- [Eventos](members/events.md)
