---
title: "Como usar gatilhos de evento para controlar um storyboard depois de ter começado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80871d9daeec257351134e9f7a72a10b697e842a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Como usar gatilhos de evento para controlar um storyboard depois de ter começado
Este exemplo mostra como controlar um <xref:System.Windows.Media.Animation.Storyboard> após ele ser iniciado. Para iniciar um <xref:System.Windows.Media.Animation.Storyboard> usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, que distribui as animações aos objetos e propriedades que ele anima e, em seguida, inicia o storyboard. Se você fornecer <xref:System.Windows.Media.Animation.BeginStoryboard> especificando um nome de seu <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> propriedade, você torná-lo um storyboard controlável. Você pode então controlar interativamente o storyboard depois que ele for iniciado.  
  
 Use as seguintes ações de storyboard em conjunto com <xref:System.Windows.EventTrigger> objetos para controlar um storyboard.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard pausado.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Altera a velocidade do storyboard.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avança um storyboard até o final do período de preenchimento, se ele tiver um.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Para o storyboard.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>Remove o storyboard, liberando recursos.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, usa ações de storyboard controlável para controlar interativamente um storyboard.  
  
 **Observação:** para ver um exemplo de como controlar um storyboard usando um código, consulte [Controlar um Storyboard depois de ter começado usando os método interativos](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Para obter exemplos adicionais, consulte a [Galeria de exemplos de animação](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [Controlar um storyboard depois de ter começado usando os métodos interativos](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
