---
title: Registrar um Módulo Provedor do Lado do Cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: ed45b7e5d60e42f03bce8b9dc4abbf8226916304
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966352"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="b267d-102">Registrar um Módulo Provedor do Lado do Cliente</span><span class="sxs-lookup"><span data-stu-id="b267d-102">Register a Client-Side Provider Assembly</span></span>
> [!NOTE]
> <span data-ttu-id="b267d-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="b267d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b267d-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="b267d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b267d-105">Este tópico mostra como registrar uma DLL que contém provedores de automação da interface do usuário do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="b267d-105">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b267d-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b267d-106">Example</span></span>  
 <span data-ttu-id="b267d-107">O exemplo a seguir mostra como registrar um assembly que contém um provedor para uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="b267d-107">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="b267d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b267d-108">See also</span></span>

- [<span data-ttu-id="b267d-109">Criar um provedor de automação de interface do usuário do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="b267d-109">Create a Client-Side UI Automation Provider</span></span>](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
