---
title: Visão geral das técnicas de animação da propriedade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
ms.openlocfilehash: 0b4bf6d4963f32ad83f762fce73c805197ff9c9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181837"
---
# <a name="property-animation-techniques-overview"></a>Visão geral das técnicas de animação da propriedade
Este tópico descreve as diferentes abordagens para animar propriedades: storyboards, animações locais, relógios e animações por quadro.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Para entender este tópico, você deve estar familiarizado com os recursos básicos de animação descritos na [Visão geral da animação](animation-overview.md).  
  
<a name="summary"></a>
## <a name="different-ways-to-animate"></a>Diferentes maneiras de animar  
 Como há muitos cenários diferentes para animar propriedades, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece várias abordagens para animá-las.  
  
 Para cada abordagem, a tabela a seguir indica se ela pode ser usada por instância, em estilos, em modelos de controle ou em modelos de dados; se pode ser usada em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e se a abordagem permite que você controle interativamente a animação.  "Por instância" se refere à técnica de aplicar uma animação ou storyboard diretamente às instâncias de um objeto, em vez de um estilo, modelo de controle ou modelo de dados.  
  
|Técnica de animação|Cenários|Dá suporte a XAML|Controlável interativamente|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animação de storyboard|Por exemplo, <xref:System.Windows.Style> <xref:System.Windows.Controls.ControlTemplate>,<xref:System.Windows.DataTemplate>|Sim|Sim|  
|Animação local|Por instância|Não|Não|  
|Animação de relógio|Por instância|Não|Sim|  
|Animação por quadro|Por instância|Não|N/D|  
  
<a name="storyboard_animations"></a>
## <a name="storyboard-animations"></a>Animações de storyboard  
 Use <xref:System.Windows.Media.Animation.Storyboard> um quando quiser definir e aplicar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]suas animações em, controlar interativamente suas animações após o início, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.DataTemplate>criar uma árvore complexa de animações ou animar em um <xref:System.Windows.Style>, ou . Para que um objeto <xref:System.Windows.Media.Animation.Storyboard>seja animado por <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>um , deve ser um <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>ou , ou deve ser usado para definir um ou . Para obter mais detalhes, consulte a [Visão geral de storyboards](storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> é um tipo <xref:System.Windows.Media.Animation.Timeline> especial de recipiente que fornece informações de segmentação para as animações que contém. Para animar com <xref:System.Windows.Media.Animation.Storyboard>um , você completa os três passos seguintes.  
  
1. Declare <xref:System.Windows.Media.Animation.Storyboard> a e uma ou mais animações.  
  
2. Use <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> as <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> propriedades anexadas para especificar o objeto de destino e a propriedade de cada animação.  
  
3. (Somente código) Defina <xref:System.Windows.NameScope> um <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>para um ou . Registre os nomes dos objetos <xref:System.Windows.FrameworkElement> para <xref:System.Windows.FrameworkContentElement>animar com isso ou .  
  
4. Comece <xref:System.Windows.Media.Animation.Storyboard>o .  
  
 Iniciar <xref:System.Windows.Media.Animation.Storyboard> um aplica animações às propriedades que eles animam e as inicia. Existem duas maneiras <xref:System.Windows.Media.Animation.Storyboard>de começar <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> um: você <xref:System.Windows.Media.Animation.Storyboard> pode usar o método <xref:System.Windows.Media.Animation.BeginStoryboard> fornecido pela classe, ou você pode usar uma ação. A única maneira de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se animar <xref:System.Windows.Media.Animation.BeginStoryboard> é usando uma ação. Uma <xref:System.Windows.Media.Animation.BeginStoryboard> ação pode ser <xref:System.Windows.EventTrigger>usada <xref:System.Windows.Trigger>em <xref:System.Windows.DataTrigger>uma propriedade ou a .  
  
 A tabela a seguir mostra <xref:System.Windows.Media.Animation.Storyboard> os diferentes locais onde cada técnica de início é suportada: por instância, estilo, modelo de controle e modelo de dados.  
  
|O storyboard é iniciado usando…|Por instância|Estilo|Modelo de controle|Modelo de dados|Exemplo|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e um<xref:System.Windows.EventTrigger>|Sim|Sim|Sim|Sim|[Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e uma propriedade<xref:System.Windows.Trigger>|Não|Sim|Sim|Sim|[Disparar uma animação quando o valor de uma propriedade é alterado](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>e um<xref:System.Windows.DataTrigger>|Não|Sim|Sim|Sim|[Como disparar uma animação quando dados são alterados](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|Método <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Sim|Não|Não|Não|[Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Para obter <xref:System.Windows.Media.Animation.Storyboard> mais informações sobre objetos, consulte a visão geral do [Storyboards](storyboards-overview.md).  
  
## <a name="local-animations"></a>Animações locais  
 As animações locais fornecem uma maneira conveniente de <xref:System.Windows.Media.Animation.Animatable> animar uma propriedade de dependência de qualquer objeto. Use animações locais quando você quiser aplicar uma única animação a uma propriedade e não precisar controlar interativamente a animação após seu início. Ao <xref:System.Windows.Media.Animation.Storyboard> contrário de uma animação, uma animação local pode <xref:System.Windows.FrameworkElement> animar <xref:System.Windows.FrameworkContentElement>um objeto que não está associado a um ou um . Você também não precisa definir <xref:System.Windows.NameScope> um para este tipo de animação.  
  
 Animações locais só podem ser usadas no código e não podem ser definidas em estilos, modelos de controle ou modelos de dados. Uma animação local não pode ser controlada interativamente após ter sido iniciada.  
  
 Para animar usando um animação local, conclua as etapas a seguir.  
  
1. Crie <xref:System.Windows.Media.Animation.AnimationTimeline> um objeto.  
  
2. Use <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> o método do objeto que você deseja <xref:System.Windows.Media.Animation.AnimationTimeline> animar para aplicar o na propriedade que você especificar.  
  
 O exemplo a seguir mostra como animar a <xref:System.Windows.Controls.Button>largura e a cor de fundo de a .  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Animações de relógio  
 Use <xref:System.Windows.Media.MediaPlayer.Clock%2A> objetos quando quiser animar <xref:System.Windows.Media.Animation.Storyboard> sem usar um e deseja criar árvores de cronometragem complexas ou controlar animações interativas depois que elas começarem. Você pode usar objetos relógio para animar <xref:System.Windows.Media.Animation.Animatable> uma propriedade de dependência de qualquer objeto.  
  
 Você não <xref:System.Windows.Media.Animation.Clock> pode usar objetos diretamente para animar em estilos, modelos de controle ou modelos de dados. (O sistema de animação <xref:System.Windows.Media.Animation.Clock> e cronometragem realmente usa objetos para animar em estilos, <xref:System.Windows.Media.Animation.Clock> modelos de <xref:System.Windows.Media.Animation.Storyboard>controle e modelos de dados, mas ele deve criar esses objetos para você a partir de um . Para obter mais informações <xref:System.Windows.Media.Animation.Storyboard> sobre <xref:System.Windows.Media.Animation.Clock> a relação entre objetos e objetos, consulte a visão geral do [sistema de animação e tempo](animation-and-timing-system-overview.md).)  
  
 Para aplicar <xref:System.Windows.Media.Animation.Clock> um único em uma propriedade, você completa as seguintes etapas.  
  
1. Crie <xref:System.Windows.Media.Animation.AnimationTimeline> um objeto.  
  
2. Use <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> o método <xref:System.Windows.Media.Animation.AnimationTimeline> do <xref:System.Windows.Media.Animation.AnimationClock>para criar um .  
  
3. Use <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> o método do objeto que você deseja <xref:System.Windows.Media.Animation.AnimationClock> animar para aplicar o na propriedade especificada.  
  
 O exemplo a seguir <xref:System.Windows.Media.Animation.AnimationClock> mostra como criar um e aplicá-lo a duas propriedades semelhantes.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Para criar uma árvore de tempo e usá-la para animar propriedades, conclua as etapas a seguir.  
  
1. Use <xref:System.Windows.Media.Animation.ParallelTimeline> <xref:System.Windows.Media.Animation.AnimationTimeline> e objetos para criar a árvore de cronometragem.  
  
2. Use <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> a raiz <xref:System.Windows.Media.Animation.ParallelTimeline> para <xref:System.Windows.Media.Animation.ClockGroup>criar um .  
  
3. Iterar através <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> do <xref:System.Windows.Media.Animation.ClockGroup> e aplicar <xref:System.Windows.Media.Animation.Clock> seus objetos infantis. Para <xref:System.Windows.Media.Animation.AnimationClock> cada criança, <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> use o método do objeto que <xref:System.Windows.Media.Animation.AnimationClock> você deseja animar para aplicar o na propriedade especificada  
  
 Para obter mais informações sobre objetos de Relógio, consulte o [Visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Animação por quadro: ignorar o sistema de animação e tempo  
 Use esta abordagem quando você precisar ignorar completamente o sistema de animação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Um cenário para essa abordagem são as animações de física, em que cada etapa da animação requer que os objetos sejam recalculados com base no último conjunto de interações de objetos.  
  
 Animações por quadro não podem ser definidas dentro de estilos, modelos de controle ou modelos de dados.  
  
 Para animar quadro a quadro, você <xref:System.Windows.Media.CompositionTarget.Rendering> se inscreve para o evento do objeto que contém os objetos que deseja animar. Esse método do manipulador de eventos é chamado uma vez por quadro. Toda vez que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] realizar marshaling dos dados persistentes de renderização na árvore visual para o gráfico de cena de composição, o método de manipulador de eventos será chamado.  
  
 Em seu manipulador de eventos, realize os cálculos necessários para o efeito da animação e defina as propriedades dos objetos que você deseja animar com esses valores.  
  
 Para obter o tempo de apresentação <xref:System.EventArgs> para o quadro atual, o associado a este evento pode ser lançado como <xref:System.Windows.Media.RenderingEventArgs>, que fornece uma <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> propriedade que você pode usar para obter o tempo de renderização do quadro atual.  
  
 Para saber mais, veja a página <xref:System.Windows.Media.CompositionTarget.Rendering>.  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
- [Visão geral da animação e do sistema de tempo](animation-and-timing-system-overview.md)
- [Visão geral das propriedades de dependência](../advanced/dependency-properties-overview.md)
