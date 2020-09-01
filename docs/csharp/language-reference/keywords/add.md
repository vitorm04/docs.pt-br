---
description: 'Saiba como criar acessadores de evento personalizados usando Adicionar palavra-chave em C #'
title: add – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 520267574320af7f85f2ee07e2778f8bebd01e4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127003"
---
# <a name="add-c-reference"></a>add (Referência de C#)
A palavra-chave contextual `add` é usada para definir um acessador de evento personalizado que é invocado quando o código cliente assina seu [evento](./event.md). Se você fornecer um acessador `add` personalizado, também será fornecer um acessador [remove](./remove.md).  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir mostra um evento que tem acessadores `add` e [remove](./remove.md) personalizados. Para obter o exemplo completo, consulte [como implementar eventos de interface](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Normalmente, não é necessário fornecer seus próprios acessadores de eventos personalizados. Os acessadores que são gerados automaticamente pelo compilador quando você declara um evento são suficientes para a maioria dos cenários.  
  
## <a name="see-also"></a>Confira também

- [Eventos](../../programming-guide/events/index.md)
