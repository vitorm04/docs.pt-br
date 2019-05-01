---
title: Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 54782c4e0460ba1ba9b8a870b8f60f08a76340b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012835"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Limitações da propriedade de intervalo do componente de temporizador dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.Timer> componente tem um <xref:System.Windows.Forms.Timer.Interval%2A> propriedade que especifica o número de milissegundos que passam entre um evento de temporizador e o próximo. A menos que o componente está desativado, um temporizador continua recebendo o <xref:System.Windows.Forms.Timer.Tick> evento em intervalos aproximadamente iguais de tempo.  
  
 Esse componente foi projetado para um ambiente do Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="the-interval-property"></a>A propriedade Interval  
 O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade tem algumas limitações a serem consideradas quando você está programando um <xref:System.Windows.Forms.Timer> componente:  
  
- Se seu aplicativo ou outro aplicativo estiver criando grandes demandas no sistema — como loops longos, cálculos intensivos, unidade, rede ou acesso à porta — seu aplicativo poderá não receber eventos com a frequência do temporizador como o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade especifica.  
  
- Não há garantia de que o intervalo decorra exatamente na hora. Para garantir a precisão, o temporizador deve verificar o relógio do sistema conforme necessário, em vez de tentar manter o controle de tempo acumulado internamente.  
  
- A precisão do <xref:System.Windows.Forms.Timer.Interval%2A> propriedade é em milissegundos. Alguns computadores fornecem um contador de alta resolução que tem uma resolução maior do que milissegundos. A disponibilidade desse contador depende do hardware do processador do computador.
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Timer>
- [Componente Timer](timer-component-windows-forms.md)
- [Visão geral do componente de temporizador](timer-component-overview-windows-forms.md)
