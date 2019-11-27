---
title: Invocando um Controle Utilizando Automação de IU
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: e1b489e8daaaf9f5b8c0cb46374fa54bf165d49c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447007"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="e0c88-102">Invocando um Controle Utilizando Automação de IU</span><span class="sxs-lookup"><span data-stu-id="e0c88-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="e0c88-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="e0c88-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e0c88-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="e0c88-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e0c88-105">Este tópico demonstra como executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="e0c88-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="e0c88-106">Localize um controle que corresponda a condições de propriedade específicas percorrendo a exibição de controle da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="e0c88-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="e0c88-107">Crie um <xref:System.Windows.Automation.AutomationElement> para cada controle.</span><span class="sxs-lookup"><span data-stu-id="e0c88-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="e0c88-108">Obtenha um objeto <xref:System.Windows.Automation.InvokePattern> de qualquer elemento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] encontrado que dê suporte ao padrão de controle de <xref:System.Windows.Automation.InvokePattern>.</span><span class="sxs-lookup"><span data-stu-id="e0c88-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="e0c88-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> para invocar o controle de um manipulador de eventos de cliente.</span><span class="sxs-lookup"><span data-stu-id="e0c88-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0c88-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e0c88-110">Example</span></span>  
 <span data-ttu-id="e0c88-111">Este exemplo usa o método <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> da classe <xref:System.Windows.Automation.AutomationElement> para gerar um objeto <xref:System.Windows.Automation.InvokePattern> e invocar um controle usando o método <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0c88-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="e0c88-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0c88-112">See also</span></span>

- [<span data-ttu-id="e0c88-113">Exemplo de InvokePattern, ExpandCollapsePattern e TogglePattern</span><span class="sxs-lookup"><span data-stu-id="e0c88-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
