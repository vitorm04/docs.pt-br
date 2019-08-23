---
title: Implementar provedores de automação de interface do usuário em um aplicativo cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: ef3d03bee412b97ed88ec76e81ad2fd19a9595eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968953"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="0f5b3-102">Implementar provedores de automação de interface do usuário em um aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="0f5b3-102">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
> <span data-ttu-id="0f5b3-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="0f5b3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0f5b3-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="0f5b3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0f5b3-105">Este tópico contém um código de exemplo que mostra como implementar um provedor de automação de interface do usuário no lado do cliente em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f5b3-105">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="0f5b3-106">Esse é um cenário incomum.</span><span class="sxs-lookup"><span data-stu-id="0f5b3-106">This is an uncommon scenario.</span></span> <span data-ttu-id="0f5b3-107">Geralmente, um aplicativo cliente de automação de interface do usuário usa provedores do lado do servidor ou provedores do lado do cliente que residem em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="0f5b3-107">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f5b3-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f5b3-108">Example</span></span>  
 <span data-ttu-id="0f5b3-109">O código de exemplo a seguir implementa um provedor simples para uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="0f5b3-109">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="0f5b3-110">O código não tem nenhuma funcionalidade útil, mas destina-se a demonstrar as etapas básicas na configuração de um provedor dentro do código do cliente e seu registro usando <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>o.</span><span class="sxs-lookup"><span data-stu-id="0f5b3-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="0f5b3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f5b3-111">See also</span></span>

- [<span data-ttu-id="0f5b3-112">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0f5b3-112">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="0f5b3-113">Registrar um assembly do provedor do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="0f5b3-113">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="0f5b3-114">Criar um provedor de automação de interface do usuário do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="0f5b3-114">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="0f5b3-115">Implementação de provedor de automação de interface do usuário do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="0f5b3-115">Client-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
