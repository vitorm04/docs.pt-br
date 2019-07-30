---
title: Delegados
description: Saiba como trabalhar com delegados no F#.
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630363"
---
# <a name="delegates"></a>Delegados

Um delegado representa uma chamada de função como um objeto. No F#, normalmente você deve usar valores de função para representar funções como valores de primeira classe; no entanto, os delegados são usados na .NET Framework e, portanto, são necessários quando você interopera com APIs que os esperam. Eles também podem ser usados durante a criação de bibliotecas criadas para uso de outras linguagens de .NET Framework.

## <a name="syntax"></a>Sintaxe

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Comentários

Na sintaxe anterior, `type1` representa o tipo de argumento ou os tipos e `type2` representa o tipo de retorno. Os tipos de argumento que são representados por `type1` são automaticamente na forma curried. Isso sugere que, para esse tipo, você use um formulário de tupla se os argumentos da função de destino forem na forma curried e uma tupla entre parênteses para argumentos que já estão no formulário de tupla. O currying automático remove um conjunto de parênteses, deixando um argumento de tupla que corresponda ao método de destino. Consulte o exemplo de código para a sintaxe que você deve usar em cada caso.

Delegados podem ser anexados F# a valores de função e métodos estáticos ou de instância. F#os valores de função podem ser passados diretamente como argumentos para delegar construtores. Para um método estático, você constrói o delegado usando o nome da classe e o método. Para um método de instância, você fornece a instância de objeto e o método em um argumento. Em ambos os casos, o operador de acesso`.`de membro () é usado.

O `Invoke` método no tipo delegado chama a função encapsulada. Além disso, os delegados podem ser passados como valores de função referenciando o nome do método Invoke sem os parênteses.

O código a seguir mostra a sintaxe para criar delegados que representam vários métodos em uma classe. Dependendo se o método é um método estático ou um método de instância e se ele tem argumentos no formulário de tupla ou no formulário na forma curried, a sintaxe para declarar e atribuir o delegado é um pouco diferente.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

O código a seguir mostra algumas das diferentes maneiras que você pode trabalhar com delegados.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

A saída do exemplo de código anterior é a seguinte.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Parâmetros e Argumentos](parameters-and-arguments.md)
- [Eventos](./members/events.md)
