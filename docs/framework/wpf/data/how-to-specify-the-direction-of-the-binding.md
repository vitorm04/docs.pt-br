---
title: 'Como: Especificar a direção da associação'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817915"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Como: Especificar a direção da Associação

Este exemplo mostra como especificar se a associação atualiza apenas a propriedade de destino da associação (destino), a propriedade de origem da associação (origem) ou a propriedade de destino e a propriedade de origem.  
  
## <a name="example"></a>Exemplo  
 Você usa a <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> propriedade para especificar a direção da associação. A seguir estão as opções disponíveis para atualizações de associação:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>atualiza a propriedade de destino ou a propriedade sempre que a propriedade de destino ou a propriedade de origem for alterada.  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>atualiza a propriedade de destino somente quando a propriedade de origem é alterada.  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>atualiza a propriedade de destino somente quando o aplicativo é iniciado ou <xref:System.Windows.FrameworkElement.DataContext%2A> quando o passa por uma alteração.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>atualiza a propriedade Source quando a propriedade de destino é alterada.  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>faz com que <xref:System.Windows.Data.Binding.Mode%2A> o valor padrão da propriedade de destino seja usado.  
  
 Para obter mais informações, consulte a enumeração <xref:System.Windows.Data.BindingMode>.  
  
 O exemplo a seguir mostra como definir a <xref:System.Windows.Data.Binding.Mode%2A> propriedade.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Para detectar alterações de origem (aplicáveis <xref:System.Windows.Data.BindingMode.OneWay> às <xref:System.Windows.Data.BindingMode.TwoWay> associações e), a origem deve implementar um mecanismo de notificação de alteração de propriedade <xref:System.ComponentModel.INotifyPropertyChanged>adequado, como. Consulte [implementar notificação de alteração de propriedade](how-to-implement-property-change-notification.md) para obter um <xref:System.ComponentModel.INotifyPropertyChanged> exemplo de uma implementação.  
  
 Para <xref:System.Windows.Data.BindingMode.TwoWay> associações <xref:System.Windows.Data.BindingMode.OneWayToSource> ou, você pode controlar o tempo das atualizações de origem definindo a <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade. Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para obter mais informações.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.Binding>
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
