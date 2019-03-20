---
title: Como usar um dicionário para armazenar instâncias de eventos - Guia de Programação em C#
ms.custom: seodec18
ms.date: 03/11/2019
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f8522e499887398402f63c7788bbc6c6c4f57782
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57845262"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Como usar um dicionário para armazenar instâncias de eventos - Guia de Programação em C#

Um uso para os acessadores de eventos personalizados `add` e `remove` é expor muitos eventos sem alocar um campo para cada um deles; em vez disso, usando uma instância <xref:System.Collections.Generic.Dictionary%602> para armazenar as instâncias de eventos, como demonstra o exemplo a seguir. Isso só será útil se você tiver muitos eventos, mas presume que não haverá subscrição à maioria deles.

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

Essa implementação está de acordo com o comportamento de [adição e remoção de delegados](~/_csharplang/spec/delegates.md#delegate-invocation) na especificação da linguagem C#.

Observe que a instrução [lock](../../language-reference/keywords/lock-statement.md) é usada somente para *acessar* o dicionário com manipuladores de eventos. Não invoque um manipulador de eventos dentro do corpo da instrução `lock`, pois ela poderia levar a deadlocks ou contenção de bloqueio.

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Eventos](../../../csharp/programming-guide/events/index.md)
- [Delegados](../../../csharp/programming-guide/delegates/index.md)
