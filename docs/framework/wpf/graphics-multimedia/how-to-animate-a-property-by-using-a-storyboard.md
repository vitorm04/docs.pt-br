---
title: Como animar uma propriedade usando um storyboard
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: 6cfce9a5b070a23ed9ac03473888bf572b61393b
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559632"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Como animar uma propriedade usando um storyboard
Este exemplo mostra como usar um <xref:System.Windows.Media.Animation.Storyboard> para animar propriedades. Para animar uma propriedade usando uma <xref:System.Windows.Media.Animation.Storyboard>, crie uma animação para cada propriedade que você deseja animar e também crie uma <xref:System.Windows.Media.Animation.Storyboard> para conter as animações.  
  
 O tipo da propriedade determina o tipo de animação a ser usada. Por exemplo, para animar uma propriedade que usa <xref:System.Double> valores, use uma <xref:System.Windows.Media.Animation.DoubleAnimation>. As propriedades anexadas <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> especificam o objeto e a propriedade aos quais a animação é aplicada.  
  
 Para iniciar um storyboard em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], use uma ação de <xref:System.Windows.Media.Animation.BeginStoryboard> e uma <xref:System.Windows.EventTrigger>. O <xref:System.Windows.EventTrigger> começa a <xref:System.Windows.Media.Animation.BeginStoryboard> ação quando o evento especificado por sua propriedade <xref:System.Windows.EventTrigger.RoutedEvent%2A> ocorre. A ação <xref:System.Windows.Media.Animation.BeginStoryboard> inicia o <xref:System.Windows.Media.Animation.Storyboard>.  
  
 O exemplo a seguir usa <xref:System.Windows.Media.Animation.Storyboard> objetos para animar dois controles <xref:System.Windows.Controls.Button>. Para que o primeiro botão mude de tamanho, sua <xref:System.Windows.FrameworkElement.Width%2A> é animada. Para fazer com que o segundo botão mude de cor, a propriedade <xref:System.Windows.Media.SolidColorBrush.Color%2A> da <xref:System.Windows.Media.SolidColorBrush> é usada para definir a <xref:System.Windows.Controls.Control.Background%2A> do botão que é animado.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Embora as animações possam ter como destino um objeto <xref:System.Windows.FrameworkElement>, como um <xref:System.Windows.Controls.Control> ou <xref:System.Windows.Controls.Panel>, e um objeto <xref:System.Windows.Freezable>, como um <xref:System.Windows.Media.Brush> ou <xref:System.Windows.Media.Transform>, somente os elementos da estrutura têm uma propriedade <xref:System.Windows.FrameworkElement.Name%2A>. Para atribuir um nome a um congelável para que ele possa ser alvo de uma animação, use a [Diretiva x:Name](../../../desktop-wpf/xaml-services/xname-directive.md), como mostrado no exemplo anterior.  
  
 Se você usar o código, deverá criar um <xref:System.Windows.NameScope> para um <xref:System.Windows.FrameworkElement> e registrar os nomes dos objetos para animar com esse <xref:System.Windows.FrameworkElement>. Para iniciar as animações no código, use uma ação <xref:System.Windows.Media.Animation.BeginStoryboard> com uma <xref:System.Windows.EventTrigger>. Opcionalmente, você pode usar um manipulador de eventos e o método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> de <xref:System.Windows.Media.Animation.Storyboard>. O exemplo a seguir mostra como usar o método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Para obter mais informações sobre animações e storyboard, consulte [Visão geral de animação](animation-overview.md).  
  
 Se você usar o código, não estará limitado a usar <xref:System.Windows.Media.Animation.Storyboard> objetos para animar as propriedades. Para obter mais informações e exemplos, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md) e [Animar uma propriedade usando um AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
