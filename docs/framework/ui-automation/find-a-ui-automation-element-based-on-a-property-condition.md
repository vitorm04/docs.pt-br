---
title: "Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d1d504ca056f35fe8716b299ec73f45648bb3d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="7eac0-102">Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="7eac0-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="7eac0-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="7eac0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7eac0-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="7eac0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7eac0-105">Este tópico contém código de exemplo que mostra como localizar um elemento dentro do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore com base em uma propriedade específica ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="7eac0-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7eac0-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7eac0-106">Example</span></span>  
 <span data-ttu-id="7eac0-107">No exemplo a seguir, um conjunto de condições de propriedade é especificado para identificar um determinado elemento (ou elementos) de interesse no <xref:System.Windows.Automation.AutomationElement> árvore.</span><span class="sxs-lookup"><span data-stu-id="7eac0-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="7eac0-108">Uma pesquisa por todos os elementos correspondentes é executada com o <xref:System.Windows.Automation.AutomationElement.FindAll%2A> método que incorpora uma série de <xref:System.Windows.Automation.AndCondition> operações booleanas para limitar o número de elementos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="7eac0-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7eac0-109">Ao pesquisar a partir de <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, você deve tentar obter apenas filhos diretos.</span><span class="sxs-lookup"><span data-stu-id="7eac0-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="7eac0-110">Uma pesquisa por descendentes pode percorrer centenas ou mesmo milhares de elementos, possivelmente resultando em um estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="7eac0-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="7eac0-111">Se você está tentando obter um elemento específico em um nível inferior, você deve iniciar sua pesquisa de janela do aplicativo ou de um contêiner em um nível inferior.</span><span class="sxs-lookup"><span data-stu-id="7eac0-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="7eac0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7eac0-112">See Also</span></span>  
 [<span data-ttu-id="7eac0-113">Exemplo de Item de Menu ExpandCollapsePattern e InvokePattern</span><span class="sxs-lookup"><span data-stu-id="7eac0-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [<span data-ttu-id="7eac0-114">Obtendo elementos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7eac0-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [<span data-ttu-id="7eac0-115">Usar a propriedade AutomationID</span><span class="sxs-lookup"><span data-stu-id="7eac0-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
