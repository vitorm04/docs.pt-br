---
title: Visão geral do componente de temporizador (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 4b0b9a8d57eae774a62c7807bfa071508bb78c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660951"
---
# <a name="timer-component-overview-windows-forms"></a>Visão geral do componente de temporizador (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.Timer> é um componente que gera um evento em intervalos regulares. Esse componente foi projetado para um ambiente do Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="key-properties-methods-and-events"></a>Eventos, métodos e propriedades de chave  
 O tamanho dos intervalos de é definido pelo <xref:System.Windows.Forms.Timer.Interval%2A> propriedade, cujo valor é em milissegundos. Quando o componente está habilitado, o <xref:System.Windows.Forms.Timer.Tick> é acionado cada intervalo. Isso é onde você adicionaria o código a ser executado. Para obter mais informações, confira [Como: Executar procedimentos em intervalos definidos com o componente de temporizador do Windows Forms](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md). Os métodos da chave de <xref:System.Windows.Forms.Timer> componente estão <xref:System.Windows.Forms.Timer.Start%2A> e <xref:System.Windows.Forms.Timer.Stop%2A>, qual ativar o temporizador e desativar. Quando o temporizador é desligado, ele redefine; não é possível pausar um <xref:System.Windows.Forms.Timer> componente.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.Timer>
- [Componente Timer](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)
- [Limitações da propriedade de intervalo do componente temporizador dos Windows Forms](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
