---
description: Palavra-chave contextual remove – Referência de C#
title: Palavra-chave contextual remove – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: a5514e72a04daa1232dbdf9a37813f09de791590
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136948"
---
# <a name="remove-c-reference"></a>remove (Referência de C#)

A palavra-chave contextual `remove` é usada para definir um acessador de eventos personalizado invocado quando o código cliente cancela a assinatura do seu [evento](event.md). Se você fornecer um acessador `remove` personalizado, também será necessário fornecer um acessador [add](add.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um evento com os acessadores [add](add.md) e `remove` personalizados. Para obter o exemplo completo, consulte [como implementar eventos de interface](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.

## <a name="see-also"></a>Confira também

- [Eventos](../../programming-guide/events/index.md)
