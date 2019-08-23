---
title: Disparar Eventos de um Provedor de Automação UI
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: c973d6ddba498f4bdab4be764a4be6bff1cacf9e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966370"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="165a5-102">Disparar Eventos de um Provedor de Automação UI</span><span class="sxs-lookup"><span data-stu-id="165a5-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="165a5-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="165a5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="165a5-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="165a5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="165a5-105">Este tópico contém um código de exemplo que mostra como gerar um evento de um provedor de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="165a5-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="165a5-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="165a5-106">Example</span></span>  
 <span data-ttu-id="165a5-107">No exemplo a seguir, um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento é gerado na implementação de um controle de botão personalizado.</span><span class="sxs-lookup"><span data-stu-id="165a5-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="165a5-108">A implementação permite que um aplicativo cliente de automação da interface do usuário simule um clique de botão.</span><span class="sxs-lookup"><span data-stu-id="165a5-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="165a5-109">Para evitar o processamento desnecessário, o <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> exemplo verifica se os eventos devem ser gerados.</span><span class="sxs-lookup"><span data-stu-id="165a5-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="165a5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="165a5-110">See also</span></span>

- [<span data-ttu-id="165a5-111">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="165a5-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
