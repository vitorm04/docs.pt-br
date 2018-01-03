---
title: "Navegar em elementos de automação de interface do usuário com TreeWalker"
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
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
caps.latest.revision: "8"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 00a5d3b33b45fd521f36f1e4775ad864ee525293
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="bbc15-102">Navegar em elementos de automação de interface do usuário com TreeWalker</span><span class="sxs-lookup"><span data-stu-id="bbc15-102">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
>  <span data-ttu-id="bbc15-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="bbc15-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bbc15-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="bbc15-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bbc15-105">Este tópico contém código de exemplo que mostra como navegar entre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementos usando o <xref:System.Windows.Automation.TreeWalker> classe.</span><span class="sxs-lookup"><span data-stu-id="bbc15-105">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbc15-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbc15-106">Example</span></span>  
 <span data-ttu-id="bbc15-107">O exemplo a seguir usa <xref:System.Windows.Automation.TreeWalker.GetParent%2A> para percorrer o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] árvore até encontrar o elemento raiz, ou área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bbc15-107">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="bbc15-108">O elemento logo abaixo que é a janela pai do elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="bbc15-108">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="bbc15-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bbc15-109">Example</span></span>  
 <span data-ttu-id="bbc15-110">O exemplo a seguir usa <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> e <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> para criar um <xref:System.Windows.Forms.TreeView> que mostra uma subárvore inteira de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementos que estão no modo de exibição de controle e que estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="bbc15-110">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="bbc15-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbc15-111">See Also</span></span>  
 [<span data-ttu-id="bbc15-112">Obtendo elementos de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="bbc15-112">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
