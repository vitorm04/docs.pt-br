---
title: "Como receber notificação quando o estado de um relógio mudar"
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
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f59fddb1add29d52ccba6fc8b8ce84938b53a1c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a>Como receber notificação quando o estado de um relógio mudar
Um relógio <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> evento ocorre quando seu <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> torna-se inválida, como quando o relógio inicia ou termina. Você pode registrar este evento com diretamente usando um <xref:System.Windows.Media.Animation.Clock>, ou você pode registrar usando um <xref:System.Windows.Media.Animation.Timeline>.  
  
 No exemplo a seguir, uma <xref:System.Windows.Media.Animation.Storyboard> e dois <xref:System.Windows.Media.Animation.DoubleAnimation> objetos são usados para animar a largura de dois retângulos. O <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> eventos é usado para as alterações de estado do relógio.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 A ilustração a seguir mostra os diferentes estados em que as animações entram à medida que a linha do tempo pai (*Storyboard*) avança.  
  
 ![Estados do relógio para uma Storyboard com duas animações](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 A tabela a seguir mostra os horários em que *Animation1*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento ser acionado:  
  
||||||||  
|-|-|-|-|-|-|-|  
|Tempo (segundos)|1|10|19|21|30|39|  
|Estado|Ativo|Ativo|Parado|Ativo|Ativo|Parado|  
  
 A tabela a seguir mostra os horários em que *Animation2*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento ser acionado:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Tempo (segundos)|1|9|11|19|21|29|31|39|  
|Estado|Ativo|Preenchendo|Ativo|Parado|Ativo|Preenchendo|Ativo|Parado|  
  
 Observe que *Animation1*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento é acionado em 10 segundos, mesmo que seu estado permanece <xref:System.Windows.Media.Animation.ClockState.Active>. Isso ocorre porque seu estado é alterado em 10 segundos, mas ela alterada de <xref:System.Windows.Media.Animation.ClockState.Active> para <xref:System.Windows.Media.Animation.ClockState.Filling> e, em seguida, de volta para <xref:System.Windows.Media.Animation.ClockState.Active> na mesma escala.
