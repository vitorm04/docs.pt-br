---
title: Palavra-chave contextual remove – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: fc6f310e17841349d476f35214ac17100e81d76f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236720"
---
# <a name="remove-c-reference"></a>remove (Referência de C#)

A palavra-chave contextual `remove` é usada para definir um acessador de eventos personalizado invocado quando o código cliente cancela a assinatura do seu [evento](event.md). Se você fornecer um acessador `remove` personalizado, também será necessário fornecer um acessador [add](add.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um evento com os acessadores [add](add.md) e `remove` personalizados. Para ver o exemplo completo, confira [Como  implementar eventos de interface](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.

## <a name="see-also"></a>Consulte também

- [Eventos](../../programming-guide/events/index.md)