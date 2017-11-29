---
title: "Como implementar notificação de alteração da propriedade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6674628acd4ea6b18f98a0ab5e20935220595de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-property-change-notification"></a>Como implementar notificação de alteração da propriedade
Para dar suporte a <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> para habilitar suas propriedades de destino de associação refletir automaticamente alterações dinâmicas da fonte de associação (por exemplo, para o painel de visualização atualizadas automaticamente quando o usuário edita um formulário), sua classe Você precisa fornecer as notificações de alteração de propriedade adequadas. Este exemplo mostra como criar uma classe que implementa <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Exemplo  
 Para implementar <xref:System.ComponentModel.INotifyPropertyChanged> é necessário declarar a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos e crie o `OnPropertyChanged` método. Em seguida, para cada propriedade que você deseja notificações de alterações, chame `OnPropertyChanged` sempre que a propriedade é atualizada.  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Para ver um exemplo de como o `Person` classe pode ser usada para oferecer suporte a <xref:System.Windows.Data.BindingMode.TwoWay> de associação, consulte [controlar quando o texto da caixa de texto atualiza a fonte](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das origens da associação](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
