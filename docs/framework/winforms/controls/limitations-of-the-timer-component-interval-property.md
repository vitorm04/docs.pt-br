---
title: Limitações da propriedade Interval do componente de timer
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745237"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms
O componente Windows Forms <xref:System.Windows.Forms.Timer> tem uma propriedade <xref:System.Windows.Forms.Timer.Interval%2A> que especifica o número de milissegundos que passam entre um evento de temporizador e o próximo. A menos que o componente esteja desabilitado, um temporizador continua a receber o evento <xref:System.Windows.Forms.Timer.Tick> em intervalos de tempo aproximadamente iguais.  
  
 Esse componente foi criado para um ambiente dos Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="the-interval-property"></a>A propriedade Interval  
 A propriedade <xref:System.Windows.Forms.Timer.Interval%2A> tem algumas limitações a serem consideradas ao programar um componente de <xref:System.Windows.Forms.Timer>:  
  
- Se seu aplicativo ou outro aplicativo estiver tomando demandas pesadas no sistema — como loops longos, cálculos intensivos ou acesso a uma unidade, rede ou porta — seu aplicativo poderá não obter eventos de timer com tanta frequência como a propriedade <xref:System.Windows.Forms.Timer.Interval%2A> especifica.  
  
- Não há garantia de que o intervalo decorra exatamente na hora. Para garantir a precisão, o temporizador deve verificar o relógio do sistema conforme necessário, em vez de tentar manter o controle de tempo acumulado internamente.  
  
- A precisão da propriedade <xref:System.Windows.Forms.Timer.Interval%2A> é em milissegundos. Alguns computadores fornecem um contador de alta resolução que tem uma resolução maior do que milissegundos. A disponibilidade desse contador depende do hardware do processador do computador.
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Timer>
- [Componente Timer](timer-component-windows-forms.md)
- [Visão geral do componente de temporizador](timer-component-overview-windows-forms.md)
