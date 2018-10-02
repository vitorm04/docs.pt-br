---
title: Retornando Propriedades de um Provedor de Automação de IU
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: ac5d539f99fe4f7a20d9030986120318840801bb
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036931"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="37064-102">Retornando Propriedades de um Provedor de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="37064-102">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="37064-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="37064-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="37064-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="37064-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="37064-105">Este tópico contém código de exemplo que mostra como um provedor de automação de interface do usuário pode retornar propriedades de um elemento para aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="37064-105">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="37064-106">Para qualquer propriedade que não oferece suporte explicitamente, o provedor deve retornar `null` (`Nothing` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="37064-106">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="37064-107">Isso garante que [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tenta obter a propriedade de outra fonte, como o provedor de janela de host.</span><span class="sxs-lookup"><span data-stu-id="37064-107">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37064-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37064-108">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="37064-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37064-109">See Also</span></span>  
 [<span data-ttu-id="37064-110">Visão geral dos provedores de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="37064-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="37064-111">Implementação de provedor de Automação da Interface do Usuário no lado do servidor</span><span class="sxs-lookup"><span data-stu-id="37064-111">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
