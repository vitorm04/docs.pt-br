---
title: Como animar uma propriedade sem usar um storyboard
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
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a1292dae3a6fc7e86387ecbe3bf2b1da6912cc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Como animar uma propriedade sem usar um storyboard
Este exemplo mostra uma maneira de aplicar uma animação a uma propriedade sem usar um <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
>  Essa funcionalidade não está disponível no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Para obter informações sobre como animar uma propriedade em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], veja [Animar uma propriedade usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Para aplicar uma animação local para uma propriedade, use o <xref:System.Windows.UIElement.BeginAnimation%2A> método. Esse método usa dois parâmetros: um <xref:System.Windows.DependencyProperty> que especifica a propriedade para animar e a animação para aplicar a essa propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como animar a cor de plano de fundo e de largura de um <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Uma variedade de classes de animação de <xref:System.Windows.Media.Animation> namespace existe para diferentes tipos de propriedades de animação. Para obter mais informações sobre propriedades de animação, consulte [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Para obter mais informações sobre propriedades de dependência (o tipo de propriedades mostradas neste exemplo) e suas funcionalidades, veja [Visão geral das propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Existem outras maneiras para animar sem usar <xref:System.Windows.Media.Animation.Storyboard> objetos; para obter mais informações, consulte [visão geral de técnicas de animação de propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
