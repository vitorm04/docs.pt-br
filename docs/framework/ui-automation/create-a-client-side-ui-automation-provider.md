---
title: Criar um Provedor de Automação de Interface de Usuário do Lado do Cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: f9f7258c272ada867b406c5615c5d2d52e1d98a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937907"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="67758-102">Criar um Provedor de Automação de Interface de Usuário do Lado do Cliente</span><span class="sxs-lookup"><span data-stu-id="67758-102">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="67758-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="67758-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="67758-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="67758-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="67758-105">Este tópico contém um código de exemplo que mostra como implementar um provedor de automação de interface do usuário do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="67758-105">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67758-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67758-106">Example</span></span>  
 <span data-ttu-id="67758-107">O código de exemplo a seguir pode ser incorporado em uma DLL (biblioteca de vínculo dinâmico) que implementa um provedor do lado do cliente muito simples para uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="67758-107">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="67758-108">O código não tem nenhuma funcionalidade útil, mas destina-se a demonstrar as etapas básicas na configuração de um assembly de provedor que pode ser registrado por um aplicativo cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="67758-108">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="67758-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67758-109">See also</span></span>

- [<span data-ttu-id="67758-110">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="67758-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="67758-111">Registrar um assembly do provedor do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="67758-111">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
