---
title: Construtores (F#)
description: Saiba como definir e usar construtores em F# para criar e inicializar objetos de classe e estrutura.
ms.date: 05/16/2016
ms.openlocfilehash: ff2463f890034cce0bbaa85d9a5c93e50427cd03
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45743897"
---
# <a name="constructors"></a>Construtores

Este tópico descreve como definir e usar construtores para criar e inicializar objetos de classe e estrutura.

## <a name="construction-of-class-objects"></a>Construção de objetos de classe

Os objetos dos tipos de classe tiverem construtores. Há dois tipos de construtores. Um é o construtor primário, cujos parâmetros são exibidos entre parênteses, logo após o nome do tipo. Especificar construtores adicionais opcionais, outros, usando o `new` palavra-chave. Todos esses construtores adicionais devem chamar o construtor primário.

O construtor primário contém `let` e `do` associações que aparecem no início da definição de classe. Um `let` associação declara campos particulares e métodos da classe; um `do` associação executa o código. Para obter mais informações sobre `let` associações em construtores de classe, consulte [ `let` associações em Classes](let-bindings-in-classes.md). Para obter mais informações sobre `do` associações em construtores, consulte [ `do` associações em Classes](do-bindings-in-classes.md).

Independentemente se o construtor que você deseja chamar é um construtor primário ou um construtor adicional, você pode criar objetos usando um `new` expressão, com ou sem opcional `new` palavra-chave. Inicializar seus objetos junto com os argumentos de construtor, qualquer um, listando os argumentos na ordem e separados por vírgulas e colocados entre parênteses, ou usando argumentos nomeados e os valores entre parênteses. Você também pode definir propriedades em um objeto durante a construção do objeto usando os nomes de propriedade e atribuir valores, assim como você usa chamado argumentos de construtor.

O código a seguir ilustra uma classe que tem um construtor e várias maneiras de criar objetos.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

A saída é a seguinte.

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Construção de estruturas

As estruturas seguem todas as regras de classes. Portanto, você pode ter um construtor primário, e você pode fornecer construtores adicionais usando `new`. No entanto, há uma diferença importante entre classes e estruturas: estruturas podem ter um construtor padrão (ou seja, um sem argumentos), mesmo se nenhum construtor primário é definido. O construtor padrão inicializa todos os campos para o valor padrão para esse tipo, geralmente zero ou seu equivalente. Os construtores que você define para estruturas devem ter pelo menos um argumento para que eles não entrem em conflito com o construtor padrão.

Além disso, a estruturas geralmente têm campos que são criados usando o `val` palavra-chave; as classes também podem ter esses campos. Estruturas e classes que têm campos definidos usando o `val` palavra-chave também pode ser inicializado em construtores adicionais usando expressões de registro, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Para obter mais informações, consulte [campos explícitos: A `val` palavra-chave](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Execução de efeitos colaterais em construtores

Um construtor primário em uma classe pode executar código em um `do` associação. No entanto, e se você tiver que executar código em um construtor adicional, sem um `do` associação? Para fazer isso, você deve usar o `then` palavra-chave.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Os efeitos colaterais do construtor primário ainda executar. Portanto, a saída é da seguinte maneira.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Autoidentificadores em construtores

Em outros membros, você deve fornecer um nome para o objeto atual na definição de cada membro. Você também pode colocar o identificador de auto na primeira linha da definição da classe usando o `as` imediatamente após os parâmetros do construtor de palavra-chave. O exemplo a seguir ilustra essa sintaxe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Em construtores adicionais, você também pode definir um identificador de self, colocando o `as` cláusula logo após os parâmetros do construtor. O exemplo a seguir ilustra essa sintaxe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Problemas podem ocorrer quando você tentar usar um objeto antes que ele está totalmente definido. Portanto, os usos do identificador de self podem causar o compilador emite um aviso e insira verificações adicionais para garantir que os membros de um objeto não são acessados antes que o objeto é inicializado. Você deve usar apenas o identificador de autoatendimento na `do` associações do construtor primário, ou após o `then` palavra-chave em construtores adicionais.

O nome do identificador self não precisa ser `this`. Ele pode ser qualquer identificador válido.

## <a name="assigning-values-to-properties-at-initialization"></a>Atribuir valores às propriedades de inicialização

Você pode atribuir valores às propriedades de um objeto de classe no código de inicialização, acrescentando uma lista de atribuições do formulário `property = value` à lista de argumentos para um construtor. Isso será mostrado no exemplo de código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

A versão seguinte do código anterior ilustra a combinação de argumentos comuns, argumentos opcionais e as configurações de propriedade na chamada de um construtor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Construtores de classe herdada

Ao herdar de uma classe base que tem um construtor, você deve especificar seus argumentos na cláusula herdar. Para obter mais informações, consulte [construtores e herança](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Construtores estáticos ou construtores de tipo

Além de especificar o código para a criação de objetos, estáticos `let` e `do` associações podem ser criadas de tipos de classe que é executado antes que o tipo é usado pela primeira vez para executar a inicialização no nível do tipo. Para obter mais informações, consulte [ `let` associações em Classes](let-bindings-in-classes.md) e [ `do` associações em Classes](do-bindings-in-classes.md).

## <a name="see-also"></a>Consulte também

- [Membros](index.md)
