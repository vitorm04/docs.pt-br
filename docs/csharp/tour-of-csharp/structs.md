---
title: Structs em C# - um tour pela linguagem C#
description: "Aprenda os conceitos básicos dos tipos de valor C#, chamados de structs"
keywords: .NET, C#, struct, tipo de valor
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9d435fd87a6103d505c14219499eeea9aee045fb
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="structs"></a>Structs

Como classes, os ***structs*** são estruturas de dados que podem conter membros de dados e os membros da função, mas, ao contrário das classes, as estruturas são tipos de valor e não precisam de alocação de heap. Uma variável de um tipo struct armazena diretamente os dados do struct, enquanto que uma variável de um tipo de classe armazena uma referência a um objeto alocado dinamicamente. Os tipos de struct não dão suporte à herança especificada pelo usuário, e todos os tipos de structs são herdados implicitamente do tipo <xref:System.ValueType>, que, por sua vez, é herdado implicitamente de `object`.

Os structs são particularmente úteis para estruturas de dados pequenas que têm semântica de valor. Números complexos, pontos em um sistema de coordenadas ou pares chave-valor em um dicionário são exemplos de structs. O uso de structs, em vez de classes para estruturas de dados pequenas, pode fazer uma grande diferença no número de alocações de memória que um aplicativo executa. Por exemplo, o programa a seguir cria e inicializa uma matriz de 100 pontos. Com `Point` implementado como uma classe, 101 objetos separados são instanciados — um para a matriz e um para os elementos de 100.

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

Uma alternativa é tornar um struct um Ponto.

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

Agora, somente um objeto é instanciado — um para a matriz — e as instâncias `Point` são armazenadas em linha na matriz.

Construtores de struct são invocados com o novo operador, mas isso não significa que a memória está sendo alocada. Em vez de alocar dinamicamente um objeto e retornar uma referência a ele, um construtor de struct simplesmente retorna o valor do struct (normalmente em um local temporário na pilha), e esse valor é, então, copiado conforme necessário.

Com classes, é possível que duas variáveis referenciem o mesmo objeto e, portanto, é possível que operações em uma variável afetem o objeto referenciado por outra variável. Com structs, as variáveis têm sua própria cópia dos dados e não é possível que as operações em um afetem o outro. Por exemplo, a saída produzida pelo seguinte fragmento de código depende de o ponto ser uma classe ou um struct.

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

Se `Point` for uma classe, a saída será 20 porque a e b referenciam o mesmo objeto. Se o ponto for um struct, a saída será 10 porque a atribuição de `a` para `b` cria uma cópia do valor e essa cópia não é afetada pela atribuição subsequente para `a.x`.

O exemplo anterior destaca duas das limitações dos structs. Primeiro, copiar um struct inteiro é, geralmente, menos eficiente do que copiar uma referência de objeto, então a passagem de atribuição e de valor do parâmetro pode ser mais custosa com structs que com tipos de referência. Segundo, com exceção para parâmetros `ref` e `out`, não é possível criar referências para structs, o que rege o uso em diversas situações.

>[!div class="step-by-step"]
[Anterior](classes-and-objects.md)
[Próximo](arrays.md)

