---
title: Como acionar e consumir eventos
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
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d052c865a554977ce5c8b0a347337d9d9b92fc57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-raise-and-consume-events"></a>Como acionar e consumir eventos
Os exemplos neste tópico mostram como trabalhar com eventos. Elas incluem exemplos do <xref:System.EventHandler> delegado, o <xref:System.EventHandler%601> delegado e um representante personalizado, para ilustrar eventos com e sem dados.  
  
 Os exemplos usam conceitos descritos no [eventos](../../../docs/standard/events/index.md) artigo.  
  
## <a name="example"></a>Exemplo  
 O primeiro exemplo mostra como gerar e consumir um evento que não têm dados. Ele contém uma classe denominada `Counter` que tem um evento chamado `ThresholdReached`. Esse evento é gerado quando um valor de contador é igual a ou excede um valor de limite. O <xref:System.EventHandler> delegado é associado ao evento, porque nenhum dado de evento é fornecido.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como gerar e consumir um evento que fornece dados. O <xref:System.EventHandler%601> delegado é associado ao evento e uma instância de um objeto de dados de evento personalizado é fornecida.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como declarar um delegado para um evento. O representante chamado `ThresholdReachedEventHandler`. Isso é apenas uma ilustração. Normalmente, você não precisa declarar um delegado para um evento, porque você pode usar o <xref:System.EventHandler> ou <xref:System.EventHandler%601> delegate. Você deve declarar um delegado somente em cenários raros, como tornar sua classe disponível para o código herdado que não é possível usar genéricos.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../docs/standard/events/index.md)
