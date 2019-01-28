---
title: add – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: d0eb05b5f7cb2e9ad51fe8787299a51f77ea276e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736897"
---
# <a name="add-c-reference"></a>add (Referência de C#)
A palavra-chave contextual `add` é usada para definir um acessador de evento personalizado que é invocado quando o código cliente assina seu [evento](../../../csharp/language-reference/keywords/event.md). Se você fornecer um acessador `add` personalizado, também será fornecer um acessador [remove](../../../csharp/language-reference/keywords/remove.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um evento que tem acessadores `add` e [remove](../../../csharp/language-reference/keywords/remove.md) personalizados. Para ver o exemplo completo, confira [Como  implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.  
  
## <a name="see-also"></a>Consulte também
- [Eventos](../../../csharp/programming-guide/events/index.md)
