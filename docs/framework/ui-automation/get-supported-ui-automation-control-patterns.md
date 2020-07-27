---
title: Obter Padrões de Controle de Automação de IU Suportados
description: Leia um exemplo que mostra como recuperar objetos de padrão de controle com suporte de elementos de automação da interface do usuário.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: f2905b81a1af2f86c78b082f0241e2181c384d25
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164162"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="5e060-103">Obter Padrões de Controle de Automação de IU Suportados</span><span class="sxs-lookup"><span data-stu-id="5e060-103">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="5e060-104">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="5e060-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5e060-105">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="5e060-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5e060-106">Este tópico mostra como recuperar objetos de padrão de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos.</span><span class="sxs-lookup"><span data-stu-id="5e060-106">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="5e060-107">Obter todos os padrões de controle</span><span class="sxs-lookup"><span data-stu-id="5e060-107">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="5e060-108">Obtenha os <xref:System.Windows.Automation.AutomationElement> padrões de controle cujos quais você está interessado.</span><span class="sxs-lookup"><span data-stu-id="5e060-108">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="5e060-109">Chame <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> para obter todos os padrões de controle do elemento.</span><span class="sxs-lookup"><span data-stu-id="5e060-109">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5e060-110">É altamente recomendável que um cliente não use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> .</span><span class="sxs-lookup"><span data-stu-id="5e060-110">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="5e060-111">O desempenho pode ser seriamente afetado, pois esse método chama <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internamente para cada padrão de controle existente.</span><span class="sxs-lookup"><span data-stu-id="5e060-111">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="5e060-112">Se possível, um cliente deve chamar <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> para os principais padrões de interesse.</span><span class="sxs-lookup"><span data-stu-id="5e060-112">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="5e060-113">Obter um padrão de controle específico</span><span class="sxs-lookup"><span data-stu-id="5e060-113">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="5e060-114">Obtenha os <xref:System.Windows.Automation.AutomationElement> padrões de controle cujos quais você está interessado.</span><span class="sxs-lookup"><span data-stu-id="5e060-114">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="5e060-115">Chame <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> para consultar um padrão específico.</span><span class="sxs-lookup"><span data-stu-id="5e060-115">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="5e060-116">Esses métodos são semelhantes, mas se o padrão não for encontrado, o <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> gerará uma exceção e <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> retornará `false` .</span><span class="sxs-lookup"><span data-stu-id="5e060-116">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e060-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e060-117">Example</span></span>  
 <span data-ttu-id="5e060-118">O exemplo a seguir recupera um <xref:System.Windows.Automation.AutomationElement> para um item de lista e Obtém um <xref:System.Windows.Automation.SelectionItemPattern> desse elemento.</span><span class="sxs-lookup"><span data-stu-id="5e060-118">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="5e060-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="5e060-119">See also</span></span>

- [<span data-ttu-id="5e060-120">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="5e060-120">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
