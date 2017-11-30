---
title: "Como manipular vários eventos usando propriedades de evento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c16918e715a93de8fdf164e75ce7be81511b71b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Como manipular vários eventos usando propriedades de evento
Para usar as propriedades de evento, você define as propriedades de evento na classe que gera os eventos e, em seguida, definir os representantes para as propriedades de evento nas classes que tratam os eventos. Para implementar várias propriedades de evento em uma classe, a classe deve armazenar internamente e manter o representante definido para cada evento. Uma abordagem típica é implementar uma coleção representante que é indexada por uma chave de evento.  
  
 Para armazenar os representantes para cada evento, você pode usar o <xref:System.ComponentModel.EventHandlerList> de classe ou implementar sua própria coleção. A classe de coleção deve fornecer métodos de configuração, acessando e recuperar o delegado do manipulador de eventos com base na chave de evento. Por exemplo, você pode usar um <xref:System.Collections.Hashtable> classe ou derivar uma classe personalizada do <xref:System.Collections.DictionaryBase> classe. Os detalhes da implementação da coleção representante não precise ser exposto fora de sua classe.  
  
 Cada propriedade de evento dentro da classe define um método de acessador add e um método de acessador remove. O acessador de adicionar uma propriedade de evento adiciona a instância representante de entrada à coleção representante. O acessador de remover uma propriedade de evento remove a instância representante de entrada da coleção representante. Acessadores de propriedade de evento usam a chave predefinida para a propriedade de evento para adicionar e remover instâncias da coleção representante.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Como manipular vários eventos usando propriedades de evento  
  
1.  Defina uma coleção representante dentro da classe que gera os eventos.  
  
2.  Defina uma chave para cada evento.  
  
3.  Defina as propriedades de evento na classe que gera os eventos.  
  
4.  Use a coleção de representante para implementar a adicionar e remover os métodos acessadores para as propriedades do evento.  
  
5.  Use as propriedades de evento público para adicionar e remover delegados de manipulador de eventos em classes que tratam os eventos.  
  
## <a name="example"></a>Exemplo  
 O exemplo c# a seguir implementa as propriedades do evento `MouseDown` e `MouseUp`usando um <xref:System.ComponentModel.EventHandlerList> para armazenar representante cada evento. As palavras-chave das construções de propriedade de evento estão em negrito.  
  
> [!NOTE]
>  Não há suporte para propriedades de evento em [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>  
 [Eventos](../../../docs/standard/events/index.md)  
 <xref:System.Web.UI.Control.Events%2A>  
 [Como declarar eventos personalizados para conservar memória](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
