---
title: 'Como: Receber notificação quando o estado de um relógio mudar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: 116647b6b7df9c012ee7d5f08abd760b7f310f71
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277102"
---
# <a name="how-to-receive-notification-when-a-clocks-state-changes"></a>Como: Receber notificação quando o estado de um relógio mudar
Um relógio <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> evento ocorre quando seu <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> se torna inválido, por exemplo, quando o relógio inicia ou interrompe. Você pode se registrar para esse evento usando diretamente uma <xref:System.Windows.Media.Animation.Clock>, ou você pode registrar usando um <xref:System.Windows.Media.Animation.Timeline>.  
  
 No exemplo a seguir, uma <xref:System.Windows.Media.Animation.Storyboard> e duas <xref:System.Windows.Media.Animation.DoubleAnimation> objetos são usados para animar a largura de dois retângulos. O <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento é usado para ouvir alterações de estado do relógio.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 A ilustração a seguir mostra os diferentes estados em que as animações entram à medida que a linha do tempo pai (*Storyboard*) avança.  
  
 ![Estados do relógio para uma Storyboard com duas animações](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 A tabela a seguir mostra os horários em que *animação1*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento é acionado:  
  
||||||||  
|-|-|-|-|-|-|-|  
|Tempo (segundos)|1|10|19|21|30|39|  
|Estado|Ativo|Ativo|Parado|Ativo|Ativo|Parado|  
  
 A tabela a seguir mostra os horários em que *animação2*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento é acionado:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Tempo (segundos)|1|9|11|19|21|29|31|39|  
|Estado|Ativo|Preenchendo|Ativo|Parado|Ativo|Preenchendo|Ativo|Parado|  
  
 Observe que *animação1*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento é acionado em 10 segundos, embora seu estado permaneça <xref:System.Windows.Media.Animation.ClockState.Active>. Isso ocorre porque seu estado mudou em 10 segundos, mas ele alterado de <xref:System.Windows.Media.Animation.ClockState.Active> à <xref:System.Windows.Media.Animation.ClockState.Filling> e, em seguida, de volta para <xref:System.Windows.Media.Animation.ClockState.Active> na mesma escala.
