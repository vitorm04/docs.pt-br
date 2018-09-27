---
title: Eventos em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: d18938565c302be085b7ac51f878d83ae5ab533d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47235813"
---
# <a name="events-in-windows-forms-controls"></a>Eventos em controles dos Windows Forms
Um controle dos Windows Forms herda mais de sessenta eventos de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Isso inclui o <xref:System.Windows.Forms.Control.Paint> evento, que faz com que um controle a ser desenhado, eventos relacionados ao exibir uma janela, como o <xref:System.Windows.Forms.Control.Resize> e <xref:System.Windows.Forms.Control.Layout> eventos e eventos de mouse e teclado de nível baixo. Alguns eventos de nível inferior são sintetizados por <xref:System.Windows.Forms.Control> sobre eventos de semânticos, como <xref:System.Windows.Forms.Control.Click> e <xref:System.Windows.Forms.Control.DoubleClick>. Para obter detalhes sobre eventos herdados, consulte <xref:System.Windows.Forms.Control>.  
  
 Se precisar de seu controle personalizado substituir a funcionalidade de eventos herdados, substituir o herdadas `On` *EventName* método em vez de anexar um delegado. Se você não estiver familiarizado com o modelo de evento no .NET Framework, consulte [gerando eventos de um componente](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Consulte também  
 [Substituindo o método OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [Manipulando a entrada do usuário](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [Definindo um evento](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Eventos](../../../../docs/standard/events/index.md)
