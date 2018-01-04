---
title: "Como configurar notificação das atualizações de associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a07337e99e985bfbc0a5dbc5f2d231ee36cf1422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Como configurar notificação das atualizações de associação
Este exemplo mostra como configurar para ser notificado quando o destino de associação (destino) ou a origem da associação (origem) de uma associação foi atualizada.  
  
## <a name="example"></a>Exemplo  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] levanta um evento de atualização de dados cada vez que a fonte de associação ou destino foi atualizada. Internamente este evento é usado para informar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] que ele deve atualizar, porque os dados associados foram alterados. Observe que esses eventos trabalhar e também para a associação unidirecional ou bidirecional funcione corretamente, você precisa implementar sua classe de dados usando o <xref:System.ComponentModel.INotifyPropertyChanged> interface. Para obter mais informações, consulte [Implementar notificação de alteração da propriedade](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Definir o <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> ou <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> propriedade (ou ambos) para `true` na associação. O manipulador fornecido para ouvir este evento deve ser anexado diretamente ao elemento do qual se espera informações de mudanças ou ao contexto geral de dados, se é preciso estar ciente de qualquer mudança no contexto.  
  
 Aqui temos um exemplo que mostra como configurar a notificação quando uma propriedade de destino foi atualizada.  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Agora é possível atribuir um manipulador baseado no delegado EventHandler\<T>, *OnTargetUpdated* neste exemplo, para manipular o evento:  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Os parâmetros do evento podem ser usados para determinar detalhes sobre a propriedade que mudou (como o tipo ou o elemento específico se o mesmo manipulador estiver conectado a mais de um elemento), o que poderá ser útil se houver várias propriedades associadas em um único elemento.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
