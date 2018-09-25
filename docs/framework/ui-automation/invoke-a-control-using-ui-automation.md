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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7e531e7ecdcc6e5cbdbc770b008d2c07873aca16
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086418"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="258cc-102">Invocando um Controle Utilizando Automação de IU</span><span class="sxs-lookup"><span data-stu-id="258cc-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="258cc-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="258cc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="258cc-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="258cc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="258cc-105">Este tópico demonstra como executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="258cc-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="258cc-106">Encontrar um controle que corresponde às condições de propriedade específica percorrendo a exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore para o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="258cc-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
-   <span data-ttu-id="258cc-107">Criar um <xref:System.Windows.Automation.AutomationElement> para cada controle.</span><span class="sxs-lookup"><span data-stu-id="258cc-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
-   <span data-ttu-id="258cc-108">Obter um <xref:System.Windows.Automation.InvokePattern> objeto de qualquer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento encontrado que suporte o <xref:System.Windows.Automation.InvokePattern> padrão de controle.</span><span class="sxs-lookup"><span data-stu-id="258cc-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
-   <span data-ttu-id="258cc-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> para invocar o controle de um manipulador de eventos do cliente.</span><span class="sxs-lookup"><span data-stu-id="258cc-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="258cc-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="258cc-110">Example</span></span>  
 <span data-ttu-id="258cc-111">Este exemplo usa o <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> método da <xref:System.Windows.Automation.AutomationElement> classe para gerar um <xref:System.Windows.Automation.InvokePattern> do objeto e invocar um controle usando o <xref:System.Windows.Automation.InvokePattern.Invoke%2A> método.</span><span class="sxs-lookup"><span data-stu-id="258cc-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="258cc-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="258cc-112">See Also</span></span>  
 [<span data-ttu-id="258cc-113">Exemplo de Item de Menu ExpandCollapsePattern e InvokePattern</span><span class="sxs-lookup"><span data-stu-id="258cc-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
