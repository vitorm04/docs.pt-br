---
title: "remove (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- remove_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b34d653a40e1309e281235416c0399abc6dd9a0d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="remove-c-reference"></a>remove (Referência de C#)
A palavra-chave contextual `remove` é usada para definir um acessador de eventos personalizado invocado quando o código cliente cancela a assinatura do seu [evento](../../../csharp/language-reference/keywords/event.md). Se você fornecer um acessador `remove` personalizado, também será necessário fornecer um acessador [add](../../../csharp/language-reference/keywords/add.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um evento com os acessadores [add](../../../csharp/language-reference/keywords/add.md) e `remove` personalizados. Para obter o exemplo completo, consulte [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)

