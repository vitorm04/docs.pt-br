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
ms.openlocfilehash: 9c5308192ca122e9c25fa8e845f2b8f89345dda8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61983002"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="5a160-102">Assinar eventos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5a160-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
>  <span data-ttu-id="5a160-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="5a160-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5a160-104">Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5a160-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5a160-105">Este tópico mostra como assinar eventos gerados por provedores de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="5a160-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a160-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a160-106">Example</span></span>  
 <span data-ttu-id="5a160-107">O exemplo de código a seguir registra um manipulador de eventos para o evento que é gerado quando um controle como um botão é invocado e o remove quando fecha o formulário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5a160-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="5a160-108">O evento é identificado por um <xref:System.Windows.Automation.AutomationEvent> passado como um parâmetro para <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a160-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="5a160-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a160-109">Example</span></span>  
 <span data-ttu-id="5a160-110">O exemplo a seguir mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para assinar um evento que é gerado quando o foco é alterado.</span><span class="sxs-lookup"><span data-stu-id="5a160-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="5a160-111">O manipulador de eventos é não registrado em um método que poderia ser chamado no encerramento do aplicativo, ou quando a notificação de eventos de interface do usuário não é mais necessária.</span><span class="sxs-lookup"><span data-stu-id="5a160-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="5a160-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a160-112">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="5a160-113">Visão geral sobre eventos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5a160-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
