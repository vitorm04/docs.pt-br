---
title: "Visão geral do componente de temporizador (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a467cb266f284e2bfdedbb5061f26231736af2b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="timer-component-overview-windows-forms"></a>Visão geral do componente de temporizador (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Timer> é um componente que gera um evento em intervalos regulares. Esse componente foi projetado para um ambiente do Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="key-properties-methods-and-events"></a>Eventos, métodos e propriedades de chave  
 O comprimento dos intervalos é definido pelo <xref:System.Windows.Forms.Timer.Interval%2A> propriedade cujo valor é em milissegundos. Quando o componente está habilitado, o <xref:System.Windows.Forms.Timer.Tick> é gerado cada intervalo. Isso é onde você deve adicionar código a ser executado. Para obter mais informações, consulte [como: executar procedimentos em intervalos definido com o componente de temporizador do Windows Forms](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md). Os principais métodos do <xref:System.Windows.Forms.Timer> componente são <xref:System.Windows.Forms.Timer.Start%2A> e <xref:System.Windows.Forms.Timer.Stop%2A>, qual ativar o temporizador e desativar. Quando o timer está desligado, ele redefine; não é possível pausar um <xref:System.Windows.Forms.Timer> componente.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Timer>  
 [Componente Timer](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Limitações da propriedade de intervalo do componente temporizador dos Windows Forms](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
