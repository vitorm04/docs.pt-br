---
title: Como implementar notificação de alteração da propriedade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: a9c0fb433e2fa65e28db3b793e038b49f9d6353b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555984"
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
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
