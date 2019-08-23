---
title: 'Como: Animar uma propriedade sem usar um Storyboard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963017"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Como: Animar uma propriedade sem usar um Storyboard
Este exemplo mostra uma maneira de aplicar uma animação a uma propriedade sem usar um <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
> Essa funcionalidade não está disponível no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Para obter informações sobre como animar uma propriedade em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], veja [Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Para aplicar uma animação local a uma propriedade, use o <xref:System.Windows.UIElement.BeginAnimation%2A> método. Esse método usa dois parâmetros: um <xref:System.Windows.DependencyProperty> que especifica a propriedade a ser animada e a animação a ser aplicada a essa propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como animar a cor da largura e do <xref:System.Windows.Controls.Button>plano de fundo de um.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Há uma variedade de classes de animação <xref:System.Windows.Media.Animation> no namespace para animar diferentes tipos de propriedades. Para obter mais informações sobre propriedades de animação, consulte [Visão geral da animação](animation-overview.md). Para obter mais informações sobre propriedades de dependência (o tipo de propriedades mostradas neste exemplo) e suas funcionalidades, veja [Visão geral das propriedades de dependência](../advanced/dependency-properties-overview.md).  
  
 Há outras maneiras de animar sem usar <xref:System.Windows.Media.Animation.Storyboard> objetos; para obter mais informações, consulte [visão geral das técnicas de animação de propriedades](property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Visão geral das técnicas de animação da propriedade](property-animation-techniques-overview.md)
- [Visão geral da animação](animation-overview.md)
