---
title: Indexadores em interfaces – Guia de Programação em C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627832"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexadores em interfaces (Guia de Programação em C#)

Os indexadores podem ser declarados em uma [interface](../../language-reference/keywords/interface.md). Acessadores de indexadores de interface diferem dos acessadores de indexadores de [classe](../../language-reference/keywords/class.md) das seguintes maneiras:

- Os acessadores de interface não usam modificadores.
- Um acessório de interface normalmente não tem um corpo.

O objetivo do acessório é indicar se o indexador é leitura-gravação, somente leitura ou somente gravação. Você pode fornecer uma implementação para um indexador definido em uma interface, mas isso é raro. Os indexadores normalmente definem uma API para acessar campos de dados, e os campos de dados não podem ser definidos em uma interface.

Este é um exemplo de um acessador de indexador de interface:

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

A assinatura de um indexador deve ser diferente das assinaturas de todos os outros indexadores declarados na mesma interface.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como implementar indexadores de interface.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

No exemplo anterior, é possível usar a implementação de membro de interface explícita usando o nome totalmente qualificado do membro de interface. Por exemplo

```csharp
string IIndexInterface.this[int index]
{
}
```

No entanto, o nome totalmente qualificado só será necessário para evitar ambiguidade quando a classe estiver implementando mais de uma interface com a mesma assinatura do indexador. Por exemplo, se uma classe `Employee` estiver implementando dois interfaces, `ICitizen` e `IEmployee`, e as duas interfaces tiverem a mesma assinatura de indexador, a implementação de membro de interface explícita é necessária. Ou seja, a seguinte declaração de indexador:

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

implementa o indexador na interface `ICitizen`.

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Indexadores](./index.md)
- [Propriedades](../classes-and-structs/properties.md)
- [Interfaces](../interfaces/index.md)
