---
title: add (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: c1fa8c130475a67ac175205fe3491a32654ea475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216000"
---
# <a name="add-c-reference"></a>add (Referência de C#)
A palavra-chave contextual `add` é usada para definir um acessador de evento personalizado que é invocado quando o código cliente assina seu [evento](../../../csharp/language-reference/keywords/event.md). Se você fornecer um acessador `add` personalizado, também será fornecer um acessador [remove](../../../csharp/language-reference/keywords/remove.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um evento que tem acessadores `add` e [remove](../../../csharp/language-reference/keywords/remove.md) personalizados. Para obter o exemplo completo, consulte [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)
