---
title: 'Como: Implementar notificação de alteração da propriedade'
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
ms.openlocfilehash: d37d468acc94470be8c2afdc495b40168932ec83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204348"
---
# <a name="how-to-implement-property-change-notification"></a>Como: Implementar notificação de alteração da propriedade
Para dar suporte à <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> para habilitar as propriedades de destino de associação refletir automaticamente as alterações dinâmicas da origem da associação (por exemplo, para que o painel de visualização atualizado automaticamente quando o usuário edita um formulário), sua classe Você precisa fornecer as notificações de alteração de propriedade adequadas. Este exemplo mostra como criar uma classe que implementa <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Exemplo  
 Para implementar <xref:System.ComponentModel.INotifyPropertyChanged> você precisa declarar o <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos e crie o `OnPropertyChanged` método. Em seguida, para cada propriedade você deseja que as notificações de alterações, chame `OnPropertyChanged` sempre que a propriedade é atualizada.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Para ver um exemplo de como o `Person` classe pode ser usada para dar suporte à <xref:System.Windows.Data.BindingMode.TwoWay> associação, consulte [controlar quando o texto de TextBox atualiza a origem](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral das fontes de associação](binding-sources-overview.md)
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos explicativos ](data-binding-how-to-topics.md)
