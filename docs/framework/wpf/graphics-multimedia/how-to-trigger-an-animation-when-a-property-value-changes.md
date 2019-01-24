---
title: 'Como: Disparar uma animação quando o valor de uma propriedade é alterado'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 2be85a9ae93d504d98930468ad2e257385e835f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705291"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Como: Disparar uma animação quando o valor de uma propriedade é alterado
Este exemplo mostra como usar um <xref:System.Windows.Trigger> para iniciar um <xref:System.Windows.Media.Animation.Storyboard> quando um valor da propriedade muda. Você pode usar um <xref:System.Windows.Trigger> dentro de um <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ou <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Trigger> animar o <xref:System.Windows.UIElement.Opacity%2A> de uma <xref:System.Windows.Controls.Button> quando seu <xref:System.Windows.UIElement.IsMouseOver%2A> propriedade torna-se `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 As animações aplicadas pela propriedade <xref:System.Windows.Trigger> objetos se comportam de maneira mais complexa que <xref:System.Windows.EventTrigger> animações ou animações iniciadas usando <xref:System.Windows.Media.Animation.Storyboard> métodos.  Eles "entrega" com animações definida por outros <xref:System.Windows.Trigger> objetos, mas se compõem com <xref:System.Windows.EventTrigger> e animações disparadas por método.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Trigger>
- [Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
- [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
