---
title: 'Como: Usar gatilhos de evento para controlar um Storyboard depois de ter começado'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855855"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Como: Usar gatilhos de evento para controlar um Storyboard depois de ter começado

Este exemplo mostra como controlar um <xref:System.Windows.Media.Animation.Storyboard> depois que ele é iniciado. Para iniciar um <xref:System.Windows.Media.Animation.Storyboard> usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]o, use <xref:System.Windows.Media.Animation.BeginStoryboard>o, que distribui as animações para os objetos e as propriedades que eles animam e, em seguida, inicia o storyboard. Se você der <xref:System.Windows.Media.Animation.BeginStoryboard> um nome especificando sua <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> Propriedade, você o tornará um storyboard controlável. Você pode então controlar interativamente o storyboard depois que ele for iniciado.

Use as seguintes ações de storyboard junto <xref:System.Windows.EventTrigger> com objetos para controlar um Storyboard.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard pausado.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Altera a velocidade do storyboard.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avança um storyboard até o final de seu período de preenchimento, se ele tiver um.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Para o storyboard.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Remove o storyboard, liberando recursos.

## <a name="example"></a>Exemplo

No exemplo a seguir, usa ações de storyboard controlável para controlar interativamente um storyboard.

> [!NOTE]
> Para ver um exemplo de controle de um storyboard usando código, consulte [controlar um storyboard depois que ele começar a usar seus métodos interativos](how-to-control-a-storyboard-after-it-starts.md).

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Para obter exemplos adicionais, consulte a [Galeria de exemplos de animação](https://go.microsoft.com/fwlink/?LinkID=159969).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Controlar um storyboard depois de ter começado usando os métodos interativos](how-to-control-a-storyboard-after-it-starts.md)
- [Visão geral da animação](animation-overview.md)
- [Visão geral de storyboards](storyboards-overview.md)
