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
ms.openlocfilehash: f17f3ad25f137bbf8d7cf88b43cc52dfdeeb3fd4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923731"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="3f40d-102">Invocando um Controle Utilizando Automação de IU</span><span class="sxs-lookup"><span data-stu-id="3f40d-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="3f40d-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3f40d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3f40d-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3f40d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3f40d-105">Este tópico demonstra como executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="3f40d-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="3f40d-106">Localize um controle que corresponda a condições de propriedade específicas percorrendo a exibição de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controle da árvore para o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="3f40d-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="3f40d-107">Crie um <xref:System.Windows.Automation.AutomationElement> para cada controle.</span><span class="sxs-lookup"><span data-stu-id="3f40d-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="3f40d-108">Obtenha um <xref:System.Windows.Automation.InvokePattern> objeto de qualquer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento encontrado que dê suporte <xref:System.Windows.Automation.InvokePattern> ao padrão de controle.</span><span class="sxs-lookup"><span data-stu-id="3f40d-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="3f40d-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> para invocar o controle de um manipulador de eventos de cliente.</span><span class="sxs-lookup"><span data-stu-id="3f40d-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f40d-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f40d-110">Example</span></span>  
 <span data-ttu-id="3f40d-111">Este exemplo usa o <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> método <xref:System.Windows.Automation.AutomationElement> da classe para gerar um <xref:System.Windows.Automation.InvokePattern> objeto e invocar um controle usando o <xref:System.Windows.Automation.InvokePattern.Invoke%2A> método.</span><span class="sxs-lookup"><span data-stu-id="3f40d-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="3f40d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f40d-112">See also</span></span>

- [<span data-ttu-id="3f40d-113">Exemplo de InvokePattern, ExpandCollapsePattern e TogglePattern</span><span class="sxs-lookup"><span data-stu-id="3f40d-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
