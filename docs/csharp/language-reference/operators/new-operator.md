---
title: operador new – Referência em C#
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403964"
---
# <a name="new-operator-c-reference"></a>operador new (Referência em C#)

O operador `new` cria uma nova instância de um tipo.

Você também pode usar a palavra-chave `new` como um [modificador de declaração de membro](../keywords/new-modifier.md) ou uma [restrição de tipo genérico](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Chamada de construtor

Para criar uma nova instância de um tipo, você normalmente invoca um dos [construtores](../../programming-guide/classes-and-structs/constructors.md) desse tipo usando o operador `new`:

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

Você pode usar um [inicializador de objeto ou coleção](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) com o operador `new` para instanciar e inicializar um objeto em uma instrução, como mostra o exemplo a seguir:

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Criação de matriz

Você também usar o operador `new` para criar uma instância de matriz, como mostra o exemplo a seguir:

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

Use a sintaxe de inicialização de matriz para criar uma instância de matriz e preenchê-la com os elementos em uma instrução. O exemplo a seguir mostra várias maneiras de como fazer isso:

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Instanciação de tipos anônimos

Para criar uma instância de um [tipo anônimo](../../programming-guide/classes-and-structs/anonymous-types.md), use o operador `new` e a sintaxe do inicializador de objeto:

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Destruição de instâncias do tipo

Você não precisa destruir as instâncias do tipo criadas anteriormente. As instâncias dos tipos de referência e de valor são destruídas automaticamente. As instâncias dos tipos de valor serão destruídas assim que o contexto que as contém for destruído. As instâncias dos tipos de referência serão destruídas pelo [coletor de lixo](../../../standard/garbage-collection/index.md) em um momento não especificado depois que a última referência a eles for removida.

Para tipos que contêm recursos não gerenciados, como um identificador de arquivo, é recomendável empregar limpeza determinística para garantir que os recursos sejam liberados assim que possível. Para obter mais informações, veja o artigo <xref:System.IDisposable?displayProperty=nameWithType> Referência da API e a [instrução de uso](../keywords/using-statement.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário não pode sobrecarregar o operador `new`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [O operador new](~/_csharplang/spec/expressions.md#the-new-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Inicializadores de objeto e de coleção](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
