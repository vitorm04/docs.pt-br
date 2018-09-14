---
title: Assinar eventos de automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c6845a85f9d3e07a4ecc9aad1ec11df8cdbc1f7a
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529487"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="50707-102">Assinar eventos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="50707-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
>  <span data-ttu-id="50707-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="50707-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="50707-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="50707-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="50707-105">Este tópico mostra como assinar eventos gerados por provedores de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="50707-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50707-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50707-106">Example</span></span>  
 <span data-ttu-id="50707-107">O exemplo de código a seguir registra um manipulador de eventos para o evento que é gerado quando um controle como um botão é invocado e o remove quando fecha o formulário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="50707-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="50707-108">O evento é identificado por um <xref:System.Windows.Automation.AutomationEvent> passado como um parâmetro para <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="50707-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="50707-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50707-109">Example</span></span>  
 <span data-ttu-id="50707-110">O exemplo a seguir mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para assinar um evento que é gerado quando o foco é alterado.</span><span class="sxs-lookup"><span data-stu-id="50707-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="50707-111">O manipulador de eventos é não registrado em um método que poderia ser chamado no encerramento do aplicativo, ou quando a notificação de eventos de interface do usuário não é mais necessária.</span><span class="sxs-lookup"><span data-stu-id="50707-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="50707-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50707-112">See Also</span></span>  
 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>  
 [<span data-ttu-id="50707-113">Visão geral sobre eventos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="50707-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
