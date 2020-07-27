---
title: Assinar eventos de automação de interface do usuário
description: Consulte como assinar eventos gerados por provedores de automação da interface do usuário. O código de exemplo registra um manipulador de eventos para o evento gerado quando um controle é invocado.
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
ms.openlocfilehash: 8f456702657c70837c6137e3e60335110361bcd9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163536"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="cc7b5-104">Assinar eventos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="cc7b5-104">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="cc7b5-105">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cc7b5-106">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="cc7b5-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cc7b5-107">Este tópico mostra como assinar eventos gerados por provedores de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-107">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc7b5-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc7b5-108">Example</span></span>  
 <span data-ttu-id="cc7b5-109">O código de exemplo a seguir registra um manipulador de eventos para o evento que é gerado quando um controle como um botão é invocado e o Remove quando o formulário do aplicativo é fechado.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-109">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="cc7b5-110">O evento é identificado por um <xref:System.Windows.Automation.AutomationEvent> passado como parâmetro para <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> .</span><span class="sxs-lookup"><span data-stu-id="cc7b5-110">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="cc7b5-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc7b5-111">Example</span></span>  
 <span data-ttu-id="cc7b5-112">O exemplo a seguir mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o para assinar um evento que é gerado quando o foco é alterado.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-112">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="cc7b5-113">O manipulador de eventos tem o registro cancelado em um método que pode ser chamado no desligamento do aplicativo ou quando a notificação de eventos da interface do usuário não é mais necessária.</span><span class="sxs-lookup"><span data-stu-id="cc7b5-113">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="cc7b5-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="cc7b5-114">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="cc7b5-115">Visão geral sobre eventos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="cc7b5-115">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
