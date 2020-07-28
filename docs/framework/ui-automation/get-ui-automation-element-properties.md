---
title: Obter propriedades de elemento da automação de interface do usuário
description: Consulte as instruções e um exemplo que mostra como recuperar as propriedades atuais ou armazenadas em cache de um elemento de automação da interface do usuário.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164100"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="1bf2b-103">Obter propriedades de elemento da automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1bf2b-103">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="1bf2b-104">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="1bf2b-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1bf2b-105">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="1bf2b-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="1bf2b-106">Este tópico mostra como recuperar propriedades de um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento.</span><span class="sxs-lookup"><span data-stu-id="1bf2b-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="1bf2b-107">Obter um valor da propriedade atual</span><span class="sxs-lookup"><span data-stu-id="1bf2b-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="1bf2b-108">Obtenha o <xref:System.Windows.Automation.AutomationElement> cuja propriedade você deseja obter.</span><span class="sxs-lookup"><span data-stu-id="1bf2b-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="1bf2b-109">Chame <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou recupere a <xref:System.Windows.Automation.AutomationElement.Current%2A> estrutura de propriedade e obtenha o valor de um de seus membros.</span><span class="sxs-lookup"><span data-stu-id="1bf2b-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="1bf2b-110">Obter um valor de propriedade em cache</span><span class="sxs-lookup"><span data-stu-id="1bf2b-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="1bf2b-111">Obtenha o <xref:System.Windows.Automation.AutomationElement> cuja propriedade você deseja obter.</span><span class="sxs-lookup"><span data-stu-id="1bf2b-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="1bf2b-112">A propriedade deve ter sido especificada no <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="1bf2b-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="1bf2b-113">Chame <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ou recupere a <xref:System.Windows.Automation.AutomationElement.Cached%2A> estrutura de propriedade e obtenha o valor de um de seus membros.</span><span class="sxs-lookup"><span data-stu-id="1bf2b-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf2b-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bf2b-114">Example</span></span>  
 <span data-ttu-id="1bf2b-115">O exemplo a seguir mostra várias maneiras de recuperar as propriedades atuais de um <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="1bf2b-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="1bf2b-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="1bf2b-116">See also</span></span>

- [<span data-ttu-id="1bf2b-117">Automação de Propriedades de Interface de Usuário para Clientes.</span><span class="sxs-lookup"><span data-stu-id="1bf2b-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="1bf2b-118">Usar armazenamento em cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1bf2b-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="1bf2b-119">Armazenando em cache em clientes de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1bf2b-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
