---
title: "Visão geral das técnicas de animação da propriedade"
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
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 132d41346e1c6dcec6ed39b3a9485f04fe8f845c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="property-animation-techniques-overview"></a>Visão geral das técnicas de animação da propriedade
Este tópico descreve as diferentes abordagens para animar propriedades: storyboards, animações locais, relógios e animações por quadro.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você deve estar familiarizado com os recursos básicos de animação descritos na [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>Diferentes maneiras de animar  
 Como há muitos cenários diferentes para animar propriedades, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece várias abordagens para animá-las.  
  
 Para cada abordagem, a tabela a seguir indica se ela pode ser usada por instância, em estilos, em modelos de controle ou em modelos de dados; se pode ser usada em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e se a abordagem permite que você controle interativamente a animação.  "Por instância" se refere à técnica de aplicar uma animação ou storyboard diretamente às instâncias de um objeto, em vez de um estilo, modelo de controle ou modelo de dados.  
  
|Técnica de animação|Cenários|Dá suporte a XAML|Controlável interativamente|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animação de storyboard|Por instância, <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>,<xref:System.Windows.DataTemplate>|Sim|Sim|  
|Animação local|Por instância|Não|Não|  
|Animação de relógio|Por instância|Não|Sim|  
|Animação por quadro|Por instância|Não|N/D|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>Animações de storyboard  
 Use um <xref:System.Windows.Media.Animation.Storyboard> quando você deseja definir e aplicar suas animações em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], interativamente controlar as animações depois de iniciar, criar uma árvore complexa de animações ou animar em um <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> ou <xref:System.Windows.DataTemplate>. Para um objeto seja animado por um <xref:System.Windows.Media.Animation.Storyboard>, ele deve ser um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, ou deve ser usado para definir um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Para obter mais detalhes, consulte a [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Um <xref:System.Windows.Media.Animation.Storyboard> é um tipo especial de recipiente <xref:System.Windows.Media.Animation.Timeline> que fornece informações de direcionamento para as animações que ele contém. Para animar com um <xref:System.Windows.Media.Animation.Storyboard>, conclua as três etapas a seguir.  
  
1.  Declarar um <xref:System.Windows.Media.Animation.Storyboard> e uma ou mais animações.  
  
2.  Use o <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> e <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> nas propriedades para especificar o objeto de destino e a propriedade de cada animação.  
  
3.  (Somente código) Definir um <xref:System.Windows.NameScope> para um <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Registrar os nomes dos objetos para animar com aquele <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  
  
4.  Iniciar o <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Iniciando um <xref:System.Windows.Media.Animation.Storyboard> aplica animações às propriedades que eles animam e inicia. Há duas maneiras de iniciar um <xref:System.Windows.Media.Animation.Storyboard>: você pode usar o <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método fornecido pelo <xref:System.Windows.Media.Animation.Storyboard> classe, ou você pode usar um <xref:System.Windows.Media.Animation.BeginStoryboard> ação. A única maneira de animar em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é usar um <xref:System.Windows.Media.Animation.BeginStoryboard> ação. Um <xref:System.Windows.Media.Animation.BeginStoryboard> ação pode ser usada em uma <xref:System.Windows.EventTrigger>, propriedade <xref:System.Windows.Trigger>, ou um <xref:System.Windows.DataTrigger>.  
  
 A tabela a seguir mostra os locais diferentes onde cada <xref:System.Windows.Media.Animation.Storyboard> começar técnica é suportada: por instância, estilo, modelo de controle e modelo de dados.  
  
|O storyboard é iniciado usando…|Por instância|Estilo|Modelo de controle|Modelo de dados|Exemplo|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e um<xref:System.Windows.EventTrigger>|Sim|Sim|Sim|Sim|[Animar uma propriedade usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e uma propriedade<xref:System.Windows.Trigger>|Não|Sim|Sim|Sim|[Disparar uma animação quando o valor de uma propriedade é alterado](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e um<xref:System.Windows.DataTrigger>|Não|Sim|Sim|Sim|[Como disparar uma animação quando dados são alterados](http://msdn.microsoft.com/en-us/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|Método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Sim|Não|Não|Não|[Animar uma propriedade usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Para obter mais informações sobre <xref:System.Windows.Media.Animation.Storyboard> objetos, consulte o [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
## <a name="local-animations"></a>Animações locais  
 Animações locais fornecem uma maneira conveniente para animar uma propriedade de dependência de qualquer <xref:System.Windows.Media.Animation.Animatable> objeto. Use animações locais quando você quiser aplicar uma única animação a uma propriedade e não precisar controlar interativamente a animação após seu início. Ao contrário de um <xref:System.Windows.Media.Animation.Storyboard> animação, uma animação local pode animar um objeto que não está associado com um <xref:System.Windows.FrameworkElement> ou um <xref:System.Windows.FrameworkContentElement>. Você também não precisa definir um <xref:System.Windows.NameScope> para esse tipo de animação.  
  
 Animações locais só podem ser usadas no código e não podem ser definidas em estilos, modelos de controle ou modelos de dados. Uma animação local não pode ser controlada interativamente após ter sido iniciada.  
  
 Para animar usando um animação local, conclua as etapas a seguir.  
  
1.  Criar um <xref:System.Windows.Media.Animation.AnimationTimeline> objeto.  
  
2.  Use o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método do objeto que você deseja animar para aplicar o <xref:System.Windows.Media.Animation.AnimationTimeline> à propriedade que você especificar.  
  
 O exemplo a seguir mostra como animar a cor de plano de fundo e de largura de um <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Animações de relógio  
 Use <xref:System.Windows.Media.MediaPlayer.Clock%2A> objetos quando você deseja animar sem usar um <xref:System.Windows.Media.Animation.Storyboard> e você deseja criar árvores complexas de tempo ou controlar interativamente animações após eles são iniciados. Você pode usar objetos Clock para animar uma propriedade de dependência de qualquer <xref:System.Windows.Media.Animation.Animatable> objeto.  
  
 Não é possível usar <xref:System.Windows.Media.Animation.Clock> objetos diretamente para animar em estilos, modelos de controle ou modelos de dados. (O sistema de animação e timing, na verdade, usar <xref:System.Windows.Media.Animation.Clock> objetos para animar em estilos, modelos de controle e modelos de dados, mas ele devem criar esses <xref:System.Windows.Media.Animation.Clock> objetos para você de um <xref:System.Windows.Media.Animation.Storyboard>. Para obter mais informações sobre a relação entre <xref:System.Windows.Media.Animation.Storyboard> objetos e <xref:System.Windows.Media.Animation.Clock> objetos, consulte o [visão geral do sistema de controle de tempo e animação](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).)  
  
 Para aplicar uma única <xref:System.Windows.Media.Animation.Clock> a uma propriedade, você concluir as etapas a seguir.  
  
1.  Criar um <xref:System.Windows.Media.Animation.AnimationTimeline> objeto.  
  
2.  Use o <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> método o <xref:System.Windows.Media.Animation.AnimationTimeline> para criar um <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3.  Use o <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> método do objeto que você deseja animar para aplicar o <xref:System.Windows.Media.Animation.AnimationClock> à propriedade que você especifica.  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-la a duas propriedades semelhantes.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Para criar uma árvore de tempo e usá-la para animar propriedades, conclua as etapas a seguir.  
  
1.  Use <xref:System.Windows.Media.Animation.ParallelTimeline> e <xref:System.Windows.Media.Animation.AnimationTimeline> objetos para criar a árvore de tempo.  
  
2.  Use o <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> da raiz <xref:System.Windows.Media.Animation.ParallelTimeline> para criar um <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3.  Iterar por meio de <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> do <xref:System.Windows.Media.Animation.ClockGroup> e aplicar seu filho <xref:System.Windows.Media.Animation.Clock> objetos. Para cada <xref:System.Windows.Media.Animation.AnimationClock> filho, use o <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> método do objeto que você deseja animar para aplicar o <xref:System.Windows.Media.Animation.AnimationClock> à propriedade que você especifica  
  
 Para obter mais informações sobre objetos de Relógio, consulte o [Visão geral da animação e do sistema de tempo](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Animação por quadro: ignorar o sistema de animação e tempo  
 Use esta abordagem quando você precisar ignorar completamente o sistema de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Um cenário para essa abordagem são as animações de física, em que cada etapa da animação requer que os objetos sejam recalculados com base no último conjunto de interações de objetos.  
  
 Animações por quadro não podem ser definidas dentro de estilos, modelos de controle ou modelos de dados.  
  
 Para animar por quadro, você registra o <xref:System.Windows.Media.CompositionTarget.Rendering> evento do objeto que contém os objetos que você deseja animar. Esse método de manipulador de eventos é chamado uma vez por quadro. Toda vez que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realizar marshaling dos dados persistentes de renderização na árvore visual ao longo da árvore de composição, o método do manipulador de eventos será chamado.  
  
 Em seu manipulador de eventos, realize os cálculos necessários para o efeito da animação e defina as propriedades dos objetos que você deseja animar com esses valores.  
  
 Para obter a hora de apresentação para o quadro atual, o <xref:System.EventArgs> associado com esse evento pode ser convertido como <xref:System.Windows.Media.RenderingEventArgs>, que fornecem um <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> tempo de processamento da propriedade que você pode usar para obter o quadro atual.  
  
 Para obter mais informações, consulte o <xref:System.Windows.Media.CompositionTarget.Rendering> página.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Visão geral da animação e do sistema de tempo](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
