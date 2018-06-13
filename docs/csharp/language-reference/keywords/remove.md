---
title: remove (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 16a169ce1a0ef5dbc29739b2d808acb19737669e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269113"
---
# <a name="remove-c-reference"></a>remove (Referência de C#)
A palavra-chave contextual `remove` é usada para definir um acessador de eventos personalizado invocado quando o código cliente cancela a assinatura do seu [evento](../../../csharp/language-reference/keywords/event.md). Se você fornecer um acessador `remove` personalizado, também será necessário fornecer um acessador [add](../../../csharp/language-reference/keywords/add.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um evento com os acessadores [add](../../../csharp/language-reference/keywords/add.md) e `remove` personalizados. Para obter o exemplo completo, consulte [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)
