---
title: Como manipular vários eventos usando propriedades de evento
description: Saiba como lidar com muitos eventos usando as propriedades do evento. Defina coleções de delegados, chaves de evento & Propriedades de evento. Implemente adicionar & remover métodos de acessador.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET]
- multiple events [.NET]
- event handling [.NET], with multiple events
- events [.NET], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: fa0bdc26eba872a62cd5f7a773df0d7a53c83975
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064230"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Como manipular vários eventos usando propriedades de evento
Para usar as propriedades de evento, defina as propriedades de evento na classe que gera os eventos e, em seguida, defina os representantes das propriedades de evento nas classes que tratam dos eventos. Para implementar várias propriedades de evento em uma classe, a classe deve armazenar e manter internamente o representante definido para cada evento. Uma abordagem típica é implementar uma coleção de representantes indexada por uma chave de evento.  
  
 Para armazenar os representantes para cada evento, você pode usar a classe <xref:System.ComponentModel.EventHandlerList> ou implementar sua própria coleção. A classe da coleção deve fornecer métodos para configurar, acessar e recuperar o representante do manipulador de eventos com base na chave de evento. Por exemplo, você poderia usar uma classe <xref:System.Collections.Hashtable> ou derivar uma classe personalizada da classe <xref:System.Collections.DictionaryBase>. Os detalhes da implementação da coleção de representantes não precisam ser expostos fora de sua classe.  
  
 Cada propriedade de evento dentro da classe define um método adicionar acessador e um método remover acessador. O método adicionar acessador de uma propriedade de eventos adiciona a instância do representante de entrada à coleção de representantes. O acessador de remoção de uma propriedade de evento remove a instância do representante de entrada da coleção de representantes. Os acessadores de propriedades de evento usam a chave predefinida na propriedade de evento para adicionar e remover instâncias da coleção de representantes.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Para manipular vários eventos usando propriedades de evento  
  
1. Defina a coleção de representantes na classe que gera os eventos.  
  
2. Defina uma chave para cada evento.  
  
3. Defina as propriedades de evento na classe que gera os eventos.  
  
4. Use a coleção de representantes para implementar os métodos adicionar e remover acessador nas propriedades de evento.  
  
5. Use as propriedades de evento públicas para adicionar e remover representantes do manipulador de eventos nas classes que tratam dos eventos.  
  
## <a name="example"></a>Exemplo  
 O exemplo de C# a seguir implementa as propriedades de evento `MouseDown` e `MouseUp` usando uma <xref:System.ComponentModel.EventHandlerList> para armazenar o representante de cada evento. As palavras-chave dos constructos de propriedade de evento estão em negrito.  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [Eventos](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [Como declarar eventos personalizados para conservar memória](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
