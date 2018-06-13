---
title: Construtores (F#)
description: 'Saiba como definir e usar os construtores em F # para criar e inicializar objetos de classe e estrutura.'
ms.date: 05/16/2016
ms.openlocfilehash: 1773c111e0398aa83951afe14979d8a4ebc4907f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564427"
---
# <a name="constructors"></a>Construtores

Este tópico descreve como definir e usar construtores para criar e inicializar objetos de classe e estrutura.


## <a name="construction-of-class-objects"></a>Construção de objetos de classe
Objetos dos tipos de classe tem construtores. Há dois tipos de construtores. Um é construtor primário, cujos parâmetros aparecem entre parênteses logo após o nome do tipo. Especifique outros, opcionais construtores adicionais usando o `new` palavra-chave. Nenhum construtor tais adicionais deve chamar o construtor primário.

O construtor primário contém `let` e `do` associações que aparecem no início da definição de classe. Um `let` associação declara campos particulares e os métodos da classe; um `do` associação executa código. Para obter mais informações sobre `let` associações em construtores de classe, consulte [ `let` associações em Classes](let-bindings-in-classes.md). Para obter mais informações sobre `do` associações em construtores, consulte [ `do` associações em Classes](do-bindings-in-classes.md).

Seja o construtor que você deseja chamar um construtor primário ou um construtor adicional, você pode criar objetos usando um `new` expressão, com ou sem opcional `new` palavra-chave. Inicializar seus objetos junto com os argumentos de construtor, seja por meio da lista de argumentos na ordem e separados por vírgulas e colocados entre parênteses, ou usando argumentos nomeados e os valores entre parênteses. Você também pode definir propriedades em um objeto durante a construção do objeto, usando os nomes de propriedade e atribuir valores, assim como você usa denominado argumentos de construtor.

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
Estruturas Siga todas as regras de classes. Portanto, você pode ter um construtor primário, e você pode fornecer construtores adicionais usando `new`. No entanto, há uma diferença importante entre as estruturas e classes: estruturas podem ter um construtor padrão (ou seja, aquele sem argumentos), mesmo se nenhum construtor primário é definido. O construtor padrão inicializa todos os campos para o valor padrão para esse tipo, geralmente zero ou seu equivalente. Nenhum construtor definido para estruturas deve ter pelo menos um argumento para que eles não entrem em conflito com o construtor padrão.

Além disso, estruturas geralmente têm campos que são criados usando o `val` palavra-chave; classes também podem ter esses campos. Estruturas e classes que têm campos definidos usando o `val` palavra-chave também pode ser inicializado em construtores adicionais usando expressões de registro, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Para obter mais informações, consulte [campos explícitos: A `val` palavra-chave](explicit-fields-the-val-keyword.md).


## <a name="executing-side-effects-in-constructors"></a>Efeitos colaterais em execução em construtores
Um construtor primário em uma classe pode executar código em um `do` associação. No entanto, se você tem que executar código em um construtor adicional, sem um `do` associação? Para fazer isso, use o `then` palavra-chave.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Os efeitos colaterais do construtor primário ainda executar. Portanto, a saída é da seguinte maneira.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Autoidentificadores em construtores
Em outros membros, você deve fornecer um nome para o objeto atual na definição de cada membro. Você também pode colocar o identificador automático na primeira linha da definição de classe usando o `as` imediatamente após os parâmetros do construtor de palavra-chave. O exemplo a seguir ilustra essa sintaxe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

Em construtores adicionais, você também pode definir um identificador de autoatendimento, colocando o `as` cláusula logo após os parâmetros do construtor. O exemplo a seguir ilustra essa sintaxe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Podem ocorrer problemas quando você tentar usar um objeto antes que ele esteja totalmente definido. Portanto, usos do identificador de autoatendimento podem causar o compilador emite um aviso e inserir verificações adicionais para garantir que os membros de um objeto não são acessados antes do objeto é inicializado. Você deve usar apenas o identificador de autoatendimento no `do` associações do construtor primário, ou após o `then` palavra-chave em construtores adicionais.

O nome do identificador de autoatendimento não precisa ser `this`. Pode ser qualquer identificador válido.


## <a name="assigning-values-to-properties-at-initialization"></a>Atribuindo valores a propriedades de inicialização
Você pode atribuir valores às propriedades de um objeto de classe no código de inicialização adicionando uma lista de atribuições de forma `property = value` à lista de argumentos para um construtor. Isso será mostrado no exemplo de código a seguir.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

A versão seguinte do código anterior mostra a combinação de argumentos comuns, argumentos opcionais e as configurações de propriedade na chamada de um construtor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a>Construtores de classe herdada
Ao herdar de uma classe base que tenha um construtor, você deve especificar os argumentos na cláusula herdar. Para obter mais informações, consulte [construtores e herança](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Construtores estáticos ou construtores de tipo
Além de especificar o código para a criação de objetos, estáticos `let` e `do` associações podem ser criadas em tipos de classe que é executada antes do primeiro, o tipo é usado para executar a inicialização em nível de tipo. Para obter mais informações, consulte [ `let` associações em Classes](let-bindings-in-classes.md) e [ `do` associações em Classes](do-bindings-in-classes.md).

## <a name="see-also"></a>Consulte também
[Membros](index.md)
