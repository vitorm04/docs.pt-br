---
title: "Como disparar uma animação quando o valor de uma propriedade é alterado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d722be0f0367f7e6e98ef1c8451ce58ee28fedd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Como disparar uma animação quando o valor de uma propriedade é alterado
Este exemplo mostra como usar um <xref:System.Windows.Trigger> para iniciar um <xref:System.Windows.Media.Animation.Storyboard> quando um valor de propriedade é alterado. Você pode usar um <xref:System.Windows.Trigger> dentro de um <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, ou <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Trigger> para animar a <xref:System.Windows.UIElement.Opacity%2A> de um <xref:System.Windows.Controls.Button> quando seu <xref:System.Windows.UIElement.IsMouseOver%2A> propriedade torna-se `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Animações aplicadas pela propriedade <xref:System.Windows.Trigger> objetos se comportam de maneira mais complexa que <xref:System.Windows.EventTrigger> animações ou animações iniciadas usando <xref:System.Windows.Media.Animation.Storyboard> métodos.  Elas "entregam" animações definida por outros <xref:System.Windows.Trigger> objetos, mas se compõem com <xref:System.Windows.EventTrigger> e animações acionadas por método.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Trigger>  
 [Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
