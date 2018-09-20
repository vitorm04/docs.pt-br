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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8763277052a15e7cde1a5b03e124551bc91328df
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529153"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="41d3b-102">Criar um Provedor de Automação de Interface de Usuário do Lado do Cliente</span><span class="sxs-lookup"><span data-stu-id="41d3b-102">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="41d3b-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="41d3b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="41d3b-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="41d3b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="41d3b-105">Este tópico contém código de exemplo que mostra como implementar um provedor de automação de interface do usuário do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="41d3b-105">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41d3b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41d3b-106">Example</span></span>  
 <span data-ttu-id="41d3b-107">O exemplo de código a seguir pode ser criado em um [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] que implementa um provedor muito simples do lado do cliente para uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="41d3b-107">The following example code can be built into a [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="41d3b-108">O código não tem nenhuma funcionalidade útil, mas serve para demonstrar as etapas básicas na configuração de um assembly do provedor que possa ser registrado por um aplicativo de cliente de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="41d3b-108">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="41d3b-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41d3b-109">See Also</span></span>  
 [<span data-ttu-id="41d3b-110">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="41d3b-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="41d3b-111">Registrar um assembly do provedor do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="41d3b-111">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
