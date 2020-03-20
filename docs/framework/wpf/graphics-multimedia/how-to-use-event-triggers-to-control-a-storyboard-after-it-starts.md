---
title: Como usar gatilhos de evento para controlar um storyboard depois de ter começado
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186711"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Como usar gatilhos de evento para controlar um storyboard depois de ter começado

Este exemplo mostra como <xref:System.Windows.Media.Animation.Storyboard> controlar um depois de iniciado. Para iniciar <xref:System.Windows.Media.Animation.Storyboard> um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]usando <xref:System.Windows.Media.Animation.BeginStoryboard>, use , que distribui as animações para os objetos e propriedades que eles animam e, em seguida, inicia o storyboard. Se você <xref:System.Windows.Media.Animation.BeginStoryboard> der um <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> nome especificando sua propriedade, você o torna um storyboard controlável. Você pode então controlar interativamente o storyboard depois que ele for iniciado.

Use as seguintes ações <xref:System.Windows.EventTrigger> de storyboard juntamente com objetos para controlar um storyboard.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard pausado.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Muda a velocidade do storyboard.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Adianta um storyboard até o final do seu período de preenchimento, se tiver um.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Pare o storyboard.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Remove o storyboard, liberando recursos.

## <a name="example"></a>Exemplo

No exemplo a seguir, usa ações de storyboard controlável para controlar interativamente um storyboard.

> [!NOTE]
> Para ver um exemplo de controle de um storyboard usando código, consulte [Controle um Storyboard depois que ele começar a usar seus métodos interativos](how-to-control-a-storyboard-after-it-starts.md).

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Para obter exemplos adicionais, consulte a [Galeria de exemplos de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Controlar um Storyboard depois de ter começado usando os métodos interativos](how-to-control-a-storyboard-after-it-starts.md)
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
