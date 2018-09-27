---
title: Disparar Eventos de um Provedor de Automação UI
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: d8c65be9135049be81694c3aa375df0b27641bf2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47398963"
---
# <a name="raise-events-from-a-ui-automation-provider"></a><span data-ttu-id="d6d7b-102">Disparar Eventos de um Provedor de Automação UI</span><span class="sxs-lookup"><span data-stu-id="d6d7b-102">Raise Events from a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="d6d7b-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="d6d7b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d6d7b-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="d6d7b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d6d7b-105">Este tópico contém código de exemplo que mostra como disparar um evento de um provedor de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d6d7b-105">This topic contains example code that shows how to raise an event from a UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6d7b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6d7b-106">Example</span></span>  
 <span data-ttu-id="d6d7b-107">No exemplo a seguir, um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] é gerado na implementação de um controle de botão personalizado.</span><span class="sxs-lookup"><span data-stu-id="d6d7b-107">In the following example, a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] event is raised in the implementation of a custom button control.</span></span> <span data-ttu-id="d6d7b-108">A implementação permite que um aplicativo de cliente de automação de interface do usuário simular um clique de botão.</span><span class="sxs-lookup"><span data-stu-id="d6d7b-108">The implementation enables a UI Automation client application to simulate a button click.</span></span>  
  
 <span data-ttu-id="d6d7b-109">Para evitar o processamento desnecessário, o exemplo verifica <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> para ver se os eventos devem ser disparados.</span><span class="sxs-lookup"><span data-stu-id="d6d7b-109">To avoid unnecessary processing, the example checks <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> to see whether events should be raised.</span></span>  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a><span data-ttu-id="d6d7b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6d7b-110">See Also</span></span>  
 [<span data-ttu-id="d6d7b-111">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="d6d7b-111">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
