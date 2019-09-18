---
title: Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 536a71532f02782f9e84bb2bd086af212a77c0da
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043662"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="ef541-102">Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="ef541-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="ef541-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="ef541-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ef541-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="ef541-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ef541-105">Este tópico contém um código de exemplo que mostra como localizar um elemento dentro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore com base em uma propriedade ou propriedades específicas.</span><span class="sxs-lookup"><span data-stu-id="ef541-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef541-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef541-106">Example</span></span>  
 <span data-ttu-id="ef541-107">No exemplo a seguir, são especificados um conjunto de condições de propriedade que identificam um determinado elemento (ou elementos) de interesse <xref:System.Windows.Automation.AutomationElement> na árvore.</span><span class="sxs-lookup"><span data-stu-id="ef541-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="ef541-108">Uma pesquisa por todos os elementos correspondentes é então executada com <xref:System.Windows.Automation.AutomationElement.FindAll%2A> o método que incorpora uma série de <xref:System.Windows.Automation.AndCondition> operações booleanas para limitar o número de elementos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ef541-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef541-109">Ao pesquisar no <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, você deve tentar obter apenas os filhos diretos.</span><span class="sxs-lookup"><span data-stu-id="ef541-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="ef541-110">Uma pesquisa por descendentes pode iterar por centenas ou até milhares de elementos, possivelmente resultando em um estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="ef541-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="ef541-111">Se você estiver tentando obter um elemento específico em um nível inferior, deverá iniciar a pesquisa na janela do aplicativo ou em um contêiner em um nível inferior.</span><span class="sxs-lookup"><span data-stu-id="ef541-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="ef541-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef541-112">See also</span></span>

- <span data-ttu-id="ef541-113">[Exemplo de item de menu InvokePattern e ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ef541-113">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="ef541-114">Obtendo elementos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="ef541-114">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="ef541-115">Usar a propriedade AutomationID</span><span class="sxs-lookup"><span data-stu-id="ef541-115">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
