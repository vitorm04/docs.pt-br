---
title: remover palavra-chave contextual (Referência em C#)
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 70b324b8bca09701ead398eb6586ad181826e5f4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527225"
---
# <a name="remove-c-reference"></a>remove (Referência de C#)

A palavra-chave contextual `remove` é usada para definir um acessador de eventos personalizado invocado quando o código cliente cancela a assinatura do seu [evento](event.md). Se você fornecer um acessador `remove` personalizado, também será necessário fornecer um acessador [add](add.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um evento com os acessadores [add](add.md) e `remove` personalizados. Para obter o exemplo completo, consulte [Como implementar eventos de interface](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.

## <a name="see-also"></a>Consulte também

- [Eventos](../../programming-guide/events/index.md)