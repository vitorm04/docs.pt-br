---
title: 'Como: Usar gatilhos de evento para controlar um storyboard depois de ter começado'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: e4cfaf2352c3cca2b67a8e6a5d4c933399583e5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663642"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Como: Usar gatilhos de evento para controlar um storyboard depois de ter começado
Este exemplo mostra como controlar um <xref:System.Windows.Media.Animation.Storyboard> após ele ser iniciado. Para iniciar um <xref:System.Windows.Media.Animation.Storyboard> por meio [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, que distribui as animações aos objetos e propriedades que elas animam e, em seguida, inicia o storyboard. Se você der <xref:System.Windows.Media.Animation.BeginStoryboard> um nome especificando sua <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> propriedade, você tornará um storyboard controlável. Você pode então controlar interativamente o storyboard depois que ele for iniciado.  
  
 Use as seguintes ações de storyboard junto com <xref:System.Windows.EventTrigger> objetos para controlar um storyboard.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard em pausa.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Altera a velocidade do storyboard.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avança um storyboard até o final do seu período de preenchimento, se ele tiver um.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Interrompe o storyboard.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Remove o storyboard, liberando recursos.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, usa ações de storyboard controlável para controlar interativamente um storyboard.  
  
 **Observação:** Para ver um exemplo de como controlar um storyboard usando o código, consulte [controlar um Storyboard depois dele é iniciado usando os método interativos](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Para obter exemplos adicionais, consulte a [Galeria de exemplos de animação](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Controlar um storyboard depois de ter começado usando os métodos interativos](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)
- [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
