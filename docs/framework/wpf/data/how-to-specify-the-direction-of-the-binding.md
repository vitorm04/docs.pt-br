---
title: 'Como: Especificar a direção da associação'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 265271cee16d203d7652281c5416b93759e66d4b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378205"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>Como: Especificar a direção da associação
Este exemplo mostra como especificar se a associação atualiza apenas a propriedade de destino da associação (destino), a propriedade de origem da associação (origem) ou a propriedade de destino e a propriedade de origem.  
  
## <a name="example"></a>Exemplo  
 Você usa o <xref:System.Windows.Data.Binding.Mode%2A> propriedade para especificar a direção da associação. A lista de enumeração a seguir mostra as opções disponíveis para atualizações de associação:  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> Atualiza a propriedade de destino ou a propriedade sempre que a propriedade de destino ou a propriedade de origem é alterado.  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> Atualiza a propriedade de destino somente quando a propriedade de origem é alterada.  
  
-   <xref:System.Windows.Data.BindingMode.OneTime> Atualiza a propriedade de destino somente quando o aplicativo é iniciado ou quando o <xref:System.Windows.FrameworkElement.DataContext%2A> sofrer uma alteração.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> Atualiza a propriedade de origem quando a propriedade de destino é alterado.  
  
-   <xref:System.Windows.Data.BindingMode.Default> faz com que o padrão <xref:System.Windows.Data.Binding.Mode%2A> valor da propriedade de destino a ser usado.  
  
 Para obter mais informações, consulte a enumeração <xref:System.Windows.Data.BindingMode>.  
  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Data.Binding.Mode%2A> propriedade.  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 Para detectar alterações na origem (aplicáveis ao <xref:System.Windows.Data.BindingMode.OneWay> e <xref:System.Windows.Data.BindingMode.TwoWay> associações), a origem deve implementar um mecanismo de notificação de alteração de propriedade adequado, como <xref:System.ComponentModel.INotifyPropertyChanged>. Ver [implementar notificação de alteração de propriedade](how-to-implement-property-change-notification.md) para obter um exemplo de um <xref:System.ComponentModel.INotifyPropertyChanged> implementação.  
  
 Para <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> associações, você pode controlar o intervalo das atualizações na origem definindo o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade. Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para obter mais informações.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Data.Binding>
- [Visão geral da vinculação de dados](data-binding-overview.md)
- [Tópicos de instruções](data-binding-how-to-topics.md)
