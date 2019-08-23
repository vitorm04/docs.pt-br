---
title: Ordem dos eventos em formulários do Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], order of
- focus event order
- application shutdown event order
- sequence [Windows Forms], of events
- validation events [Windows Forms], order of
- application startup event order
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
ms.openlocfilehash: 28eb451c7edd740664f80f8ec35c60192764043c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949871"
---
# <a name="order-of-events-in-windows-forms"></a>Ordem dos eventos em formulários do Windows Forms
A ordem na qual os eventos são gerados em aplicativos do Windows Forms é de interesse específico para os desenvolvedores preocupados com tratamento de cada um desses eventos sucessivamente. Quando uma situação exigir tratamento meticuloso de eventos, como quando você estiver redesenhando partes do formulário, será necessário um reconhecimento da ordem exata na qual os eventos são gerados em tempo de execução. Este tópico fornece alguns detalhes sobre a ordem dos eventos durante vários estágios importantes no tempo de vida de aplicativos e controles. Para obter detalhes específicos sobre a ordem de eventos de entrada do mouse, consulte [Eventos de mouse no Windows Forms](mouse-events-in-windows-forms.md). Para obter uma visão geral de eventos no Windows Forms, consulte [Visão geral de eventos](events-overview-windows-forms.md). Para obter detalhes sobre a composição de manipuladores de eventos, consulte [Visão geral de manipuladores de eventos](event-handlers-overview-windows-forms.md).  
  
## <a name="application-startup-and-shutdown-events"></a>Eventos de inicialização e desligamento de aplicativos  
 As <xref:System.Windows.Forms.Form> classes <xref:System.Windows.Forms.Control> e expõem um conjunto de eventos relacionados à inicialização e ao desligamento do aplicativo. Quando um Aplicativo do Windows Forms é iniciado, os eventos de inicialização do formulário principal são gerados na seguinte ordem:  
  
- <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Activated?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Shown?displayProperty=nameWithType>  
  
 Quando um aplicativo é fechado, os eventos de desligamento do formulário principal são gerados na seguinte ordem:  
  
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Closed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.FormClosed?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Form.Deactivate?displayProperty=nameWithType>  
  
 O <xref:System.Windows.Forms.Application.ApplicationExit> evento<xref:System.Windows.Forms.Application> da classe é gerado após os eventos de desligamento do formulário principal.  
  
> [!NOTE]
> Visual Basic 2005 inclui eventos de aplicativo adicionais, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=nameWithType> como e. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=nameWithType>  
  
## <a name="focus-and-validation-events"></a>Eventos de foco e validação  
 Quando você altera o foco usando o teclado (guia, Shift + Tab e assim por diante) <xref:System.Windows.Forms.Control.Select%2A> , chamando os métodos ou <xref:System.Windows.Forms.Control.SelectNextControl%2A> , ou definindo a <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> propriedade para <xref:System.Windows.Forms.Control> o formulário atual, os eventos de foco da classe ocorrem na seguinte ordem :  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
 Quando você altera o foco usando o mouse ou chamando o método, <xref:System.Windows.Forms.Control.Focus%2A> os eventos <xref:System.Windows.Forms.Control> de foco da classe ocorrem na seguinte ordem:  
  
- <xref:System.Windows.Forms.Control.Enter>  
  
- <xref:System.Windows.Forms.Control.GotFocus>  
  
- <xref:System.Windows.Forms.Control.LostFocus>  
  
- <xref:System.Windows.Forms.Control.Leave>  
  
- <xref:System.Windows.Forms.Control.Validating>  
  
- <xref:System.Windows.Forms.Control.Validated>  
  
## <a name="see-also"></a>Consulte também

- [Criando manipuladores de eventos no Windows Forms](creating-event-handlers-in-windows-forms.md)
