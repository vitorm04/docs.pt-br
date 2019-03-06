---
title: 'Como: Animar uma propriedade usando um storyboard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: f6064368b4f5e4fa8324b4039d734d4430cd9174
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364704"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Como: Animar uma propriedade usando um storyboard
Este exemplo mostra como usar um <xref:System.Windows.Media.Animation.Storyboard> para animar propriedades. Para animar uma propriedade usando um <xref:System.Windows.Media.Animation.Storyboard>, crie uma animação para cada propriedade que você deseja animar e também criar um <xref:System.Windows.Media.Animation.Storyboard> para conter as animações.  
  
 O tipo da propriedade determina o tipo de animação a ser usada. Por exemplo, para animar uma propriedade que utiliza <xref:System.Double> valores, use um <xref:System.Windows.Media.Animation.DoubleAnimation>. O <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> propriedades anexadas especificam o objeto e a propriedade à qual a animação é aplicada.  
  
 Para iniciar um storyboard [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], use uma <xref:System.Windows.Media.Animation.BeginStoryboard> ação e um <xref:System.Windows.EventTrigger>. O <xref:System.Windows.EventTrigger> começa a <xref:System.Windows.Media.Animation.BeginStoryboard> ação quando o evento que é especificado pelo seu <xref:System.Windows.EventTrigger.RoutedEvent%2A> propriedade ocorre. O <xref:System.Windows.Media.Animation.BeginStoryboard> início da ação de <xref:System.Windows.Media.Animation.Storyboard>.  
  
 O exemplo a seguir usa <xref:System.Windows.Media.Animation.Storyboard> objetos para animar dois <xref:System.Windows.Controls.Button> controles. Para fazer com que o primeiro botão mudar de tamanho, seu <xref:System.Windows.FrameworkElement.Width%2A> é animado. Para fazer com que o segundo botão Alterar cor, o <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriedade do <xref:System.Windows.Media.SolidColorBrush> é usado para definir o <xref:System.Windows.Controls.Control.Background%2A> do botão que é animado.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  Embora animações podem direcionar um <xref:System.Windows.FrameworkElement> objeto, como um <xref:System.Windows.Controls.Control> ou <xref:System.Windows.Controls.Panel>e uma <xref:System.Windows.Freezable> objeto, como um <xref:System.Windows.Media.Brush> ou <xref:System.Windows.Media.Transform>, apenas os elementos de estrutura têm uma <xref:System.Windows.FrameworkElement.Name%2A> propriedade. Para atribuir um nome a um congelável para que ele possa ser alvo de uma animação, use a [Diretiva x:Name](../../xaml-services/x-name-directive.md), como mostrado no exemplo anterior.  
  
 Se você usar o código, você deve criar uma <xref:System.Windows.NameScope> para um <xref:System.Windows.FrameworkElement> e registre os nomes dos objetos a serem animados com esse <xref:System.Windows.FrameworkElement>. Para iniciar as animações no código, use uma <xref:System.Windows.Media.Animation.BeginStoryboard> ação com um <xref:System.Windows.EventTrigger>. Opcionalmente, você pode usar um manipulador de eventos e o <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método de <xref:System.Windows.Media.Animation.Storyboard>. O exemplo a seguir mostra como usar o método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Para obter mais informações sobre animações e storyboard, consulte [Visão geral de animação](animation-overview.md).  
  
 Se você usar o código, você não está limitado a usar <xref:System.Windows.Media.Animation.Storyboard> objetos para animar propriedades. Para obter mais informações e exemplos, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md) e [Animar uma propriedade usando um AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
