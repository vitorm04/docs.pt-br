---
title: Obter propriedades de elemento da automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 158ebf29bb504dd11f9e8416011226fc5846873e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043608"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="92c5a-102">Obter propriedades de elemento da automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="92c5a-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="92c5a-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="92c5a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="92c5a-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="92c5a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="92c5a-105">Este tópico mostra como recuperar propriedades de um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento.</span><span class="sxs-lookup"><span data-stu-id="92c5a-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="92c5a-106">Obter um valor da propriedade atual</span><span class="sxs-lookup"><span data-stu-id="92c5a-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="92c5a-107">Obtenha o <xref:System.Windows.Automation.AutomationElement> cuja propriedade você deseja obter.</span><span class="sxs-lookup"><span data-stu-id="92c5a-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="92c5a-108">Chame <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>ou recupere a <xref:System.Windows.Automation.AutomationElement.Current%2A> estrutura de propriedade e obtenha o valor de um de seus membros.</span><span class="sxs-lookup"><span data-stu-id="92c5a-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="92c5a-109">Obter um valor de propriedade em cache</span><span class="sxs-lookup"><span data-stu-id="92c5a-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="92c5a-110">Obtenha o <xref:System.Windows.Automation.AutomationElement> cuja propriedade você deseja obter.</span><span class="sxs-lookup"><span data-stu-id="92c5a-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="92c5a-111">A propriedade deve ter sido especificada no <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="92c5a-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="92c5a-112">Chame <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>ou recupere a <xref:System.Windows.Automation.AutomationElement.Cached%2A> estrutura de propriedade e obtenha o valor de um de seus membros.</span><span class="sxs-lookup"><span data-stu-id="92c5a-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92c5a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92c5a-113">Example</span></span>  
 <span data-ttu-id="92c5a-114">O exemplo a seguir mostra várias maneiras de recuperar as propriedades atuais <xref:System.Windows.Automation.AutomationElement>de um.</span><span class="sxs-lookup"><span data-stu-id="92c5a-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="92c5a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92c5a-115">See also</span></span>

- [<span data-ttu-id="92c5a-116">Propriedades de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="92c5a-116">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="92c5a-117">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="92c5a-117">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="92c5a-118">Armazenamento em cache em clientes de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="92c5a-118">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
