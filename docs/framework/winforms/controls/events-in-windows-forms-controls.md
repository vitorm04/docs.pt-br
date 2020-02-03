---
title: Eventos em controles
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745760"
---
# <a name="events-in-windows-forms-controls"></a>Eventos em controles dos Windows Forms
Um controle de Windows Forms herda mais de 60 eventos de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Isso inclui o evento <xref:System.Windows.Forms.Control.Paint>, que faz com que um controle seja desenhado, eventos relacionados à exibição de uma janela, como os eventos <xref:System.Windows.Forms.Control.Resize> e <xref:System.Windows.Forms.Control.Layout>, e eventos de teclado e mouse de baixo nível. Alguns eventos de nível baixo são sintetizados por <xref:System.Windows.Forms.Control> em eventos semânticos, como <xref:System.Windows.Forms.Control.Click> e <xref:System.Windows.Forms.Control.DoubleClick>. Para obter detalhes sobre os eventos herdados, consulte <xref:System.Windows.Forms.Control>.  
  
 Se o seu controle personalizado precisar substituir a funcionalidade de evento herdado, substitua o método herdado `On`*eventoname* em vez de anexar um delegado. Se você não estiver familiarizado com o modelo de evento no .NET Framework, consulte [gerando eventos de um componente](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Consulte também

- [Substituindo o método OnPaint](overriding-the-onpaint-method.md)
- [Manipulando a entrada do usuário](handling-user-input.md)
- [Definindo um evento](defining-an-event-in-windows-forms-controls.md)
- [Eventos](../../../standard/events/index.md)
