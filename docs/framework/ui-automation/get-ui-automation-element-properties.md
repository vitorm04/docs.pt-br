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
ms.openlocfilehash: 93e0fba4288ba3231bfed45252bdaa78892d008c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61610043"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="4eb0c-102">Obter propriedades de elemento da automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="4eb0c-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="4eb0c-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="4eb0c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4eb0c-104">Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="4eb0c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4eb0c-105">Este tópico mostra como recuperar propriedades de um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento.</span><span class="sxs-lookup"><span data-stu-id="4eb0c-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="4eb0c-106">Obter um valor da propriedade atual</span><span class="sxs-lookup"><span data-stu-id="4eb0c-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="4eb0c-107">Obter o <xref:System.Windows.Automation.AutomationElement> cuja propriedade você deseja obter.</span><span class="sxs-lookup"><span data-stu-id="4eb0c-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="4eb0c-108">Chame <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, ou recuperar o <xref:System.Windows.Automation.AutomationElement.Current%2A> estrutura de propriedade e obter o valor de um dos seus membros.</span><span class="sxs-lookup"><span data-stu-id="4eb0c-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="4eb0c-109">Obter um valor de propriedade em cache</span><span class="sxs-lookup"><span data-stu-id="4eb0c-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="4eb0c-110">Obter o <xref:System.Windows.Automation.AutomationElement> cuja propriedade você deseja obter.</span><span class="sxs-lookup"><span data-stu-id="4eb0c-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="4eb0c-111">A propriedade deve ter sido especificada no <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="4eb0c-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="4eb0c-112">Chame <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, ou recuperar o <xref:System.Windows.Automation.AutomationElement.Cached%2A> estrutura de propriedade e obter o valor de um dos seus membros.</span><span class="sxs-lookup"><span data-stu-id="4eb0c-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4eb0c-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4eb0c-113">Example</span></span>  
 <span data-ttu-id="4eb0c-114">O exemplo a seguir mostra várias maneiras de recuperar as propriedades atuais de um <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="4eb0c-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="4eb0c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4eb0c-115">See also</span></span>

- [<span data-ttu-id="4eb0c-116">Propriedades de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="4eb0c-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="4eb0c-117">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="4eb0c-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="4eb0c-118">Armazenamento em cache em clientes de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="4eb0c-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
