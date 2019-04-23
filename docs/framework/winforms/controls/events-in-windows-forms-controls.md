---
title: Eventos em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 41ad95de7a65dbd0cb3a0d1af8f5c8cb00c1ccdd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215879"
---
# <a name="events-in-windows-forms-controls"></a>Eventos em controles dos Windows Forms
Um controle dos Windows Forms herda mais de sessenta eventos de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Isso inclui o <xref:System.Windows.Forms.Control.Paint> evento, que faz com que um controle a ser desenhado, eventos relacionados ao exibir uma janela, como o <xref:System.Windows.Forms.Control.Resize> e <xref:System.Windows.Forms.Control.Layout> eventos e eventos de mouse e teclado de nível baixo. Alguns eventos de nível inferior são sintetizados por <xref:System.Windows.Forms.Control> sobre eventos de semânticos, como <xref:System.Windows.Forms.Control.Click> e <xref:System.Windows.Forms.Control.DoubleClick>. Para obter detalhes sobre eventos herdados, consulte <xref:System.Windows.Forms.Control>.  
  
 Se precisar de seu controle personalizado substituir a funcionalidade de eventos herdados, substituir o herdadas `On` *EventName* método em vez de anexar um delegado. Se você não estiver familiarizado com o modelo de evento no .NET Framework, consulte [gerando eventos de um componente](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Consulte também

- [Substituindo o método OnPaint](overriding-the-onpaint-method.md)
- [Manipulando a entrada do usuário](handling-user-input.md)
- [Definindo um evento](defining-an-event-in-windows-forms-controls.md)
- [Eventos](../../../standard/events/index.md)
