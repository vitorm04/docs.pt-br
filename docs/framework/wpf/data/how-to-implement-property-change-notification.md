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
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459751"
---
# <a name="how-to-implement-property-change-notification"></a>Como implementar notificação de alteração da propriedade
Para dar suporte à associação de <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> para permitir que suas propriedades de destino de associação reflitam automaticamente as alterações dinâmicas da fonte de associação (por exemplo, para que o painel de visualização seja atualizado automaticamente quando o usuário editar um formulário), sua classe precisará forneça as notificações adequadas de propriedade alterada. Este exemplo mostra como criar uma classe que implementa <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Exemplo  
 Para implementar <xref:System.ComponentModel.INotifyPropertyChanged> você precisa declarar o evento <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> e criar o método `OnPropertyChanged`. Em seguida, para cada propriedade para a qual você deseja alterar notificações, você chama `OnPropertyChanged` sempre que a propriedade é atualizada.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Para ver um exemplo de como a classe de `Person` pode ser usada para dar suporte à associação de <xref:System.Windows.Data.BindingMode.TwoWay>, consulte [controlar quando o texto da TextBox atualiza a origem](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral das origens da associação](binding-sources-overview.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
