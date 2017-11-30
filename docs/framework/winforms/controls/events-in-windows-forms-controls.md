---
title: Eventos em controles dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e568dd7fadea8af399a63aa95347f368b4e13a54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="events-in-windows-forms-controls"></a>Eventos em controles dos Windows Forms
Um controle Windows Forms herda mais de sessenta eventos de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Isso inclui o <xref:System.Windows.Forms.Control.Paint> evento, que faz com que um controle a ser desenhada, eventos relacionados ao exibir uma janela, como o <xref:System.Windows.Forms.Control.Resize> e <xref:System.Windows.Forms.Control.Layout> eventos e eventos de mouse e teclado de nível inferior. Alguns eventos de nível inferior são sintetizados por <xref:System.Windows.Forms.Control> em eventos semânticos como <xref:System.Windows.Forms.Control.Click> e <xref:System.Windows.Forms.Control.DoubleClick>. Para obter detalhes sobre eventos herdados, consulte <xref:System.Windows.Forms.Control>.  
  
 Se o controle personalizado deve substituir a funcionalidade de eventos herdados, substituir o herdadas `On` *EventName* método em vez de anexar um representante. Se você não estiver familiarizado com o modelo de evento no .NET Framework, consulte [disparar eventos de um componente](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
## <a name="see-also"></a>Consulte também  
 [Substituindo o método OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [Manipulando a entrada do usuário](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [Definindo um evento](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Eventos](../../../../docs/standard/events/index.md)
