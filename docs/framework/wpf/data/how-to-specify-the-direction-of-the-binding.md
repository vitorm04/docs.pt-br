---
title: Como especificar a direção da associação
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459096"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Como especificar a direção da Associação

Este exemplo mostra como especificar se a associação atualiza apenas a propriedade de destino da associação (destino), a propriedade de origem da associação (origem) ou a propriedade de destino e a propriedade de origem.  
  
## <a name="example"></a>Exemplo  
 Use a propriedade <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> para especificar a direção da associação. A seguir estão as opções disponíveis para atualizações de associação:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> atualiza a propriedade de destino ou a propriedade sempre que a propriedade de destino ou a propriedade de origem for alterada.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> atualiza a propriedade de destino somente quando a propriedade de origem é alterada.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> atualiza a propriedade de destino somente quando o aplicativo é iniciado ou quando o <xref:System.Windows.FrameworkElement.DataContext%2A> passa por uma alteração.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> atualiza a propriedade Source quando a propriedade de destino é alterada.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> faz com que o valor de <xref:System.Windows.Data.Binding.Mode%2A> padrão da propriedade de destino seja usado.  
  
 Para obter mais informações, consulte a enumeração <xref:System.Windows.Data.BindingMode>.  
  
 O exemplo a seguir mostra como definir a propriedade <xref:System.Windows.Data.Binding.Mode%2A>.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Para detectar alterações de origem (aplicável a associações de <xref:System.Windows.Data.BindingMode.OneWay> e <xref:System.Windows.Data.BindingMode.TwoWay>), a origem deve implementar um mecanismo de notificação de alteração de propriedade adequado, como <xref:System.ComponentModel.INotifyPropertyChanged>. Consulte [implementar notificação de alteração de propriedade](how-to-implement-property-change-notification.md) para obter um exemplo de uma implementação de <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Para associações <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource>, você pode controlar o tempo das atualizações de origem definindo a propriedade <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>. Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para obter mais informações.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.Binding>
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Tópicos explicativos](data-binding-how-to-topics.md)
