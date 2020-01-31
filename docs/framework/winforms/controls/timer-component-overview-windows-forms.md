---
title: Visão geral do componente de temporizador
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 83b52d395cdc3e3357bcf83517eab258a5c8ae08
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742772"
---
# <a name="timer-component-overview-windows-forms"></a>Visão geral do componente de temporizador (Windows Forms)
O <xref:System.Windows.Forms.Timer> de Windows Forms é um componente que gera um evento em intervalos regulares. Esse componente foi criado para um ambiente dos Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="key-properties-methods-and-events"></a>Propriedades, métodos e eventos de chave  
 O comprimento dos intervalos é definido pela propriedade <xref:System.Windows.Forms.Timer.Interval%2A>, cujo valor é em milissegundos. Quando o componente é habilitado, o evento <xref:System.Windows.Forms.Timer.Tick> é gerado a cada intervalo. É aí que você adicionaria o código a ser executado. Para obter mais informações, consulte [como: executar procedimentos em intervalos definidos com o componente de Timer Windows Forms](run-procedures-at-set-intervals-with-wf-timer-component.md). Os principais métodos do componente <xref:System.Windows.Forms.Timer> são <xref:System.Windows.Forms.Timer.Start%2A> e <xref:System.Windows.Forms.Timer.Stop%2A>, o que ativa e desativa o temporizador. Quando o temporizador é desligado, ele é redefinido; Não é possível pausar um componente <xref:System.Windows.Forms.Timer>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Timer>
- [Componente Timer](timer-component-windows-forms.md)
- [Limitações da propriedade de intervalo do componente temporizador dos Windows Forms](limitations-of-the-timer-component-interval-property.md)
