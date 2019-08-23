---
title: Mover um elemento de automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- moving elements
- elements, moving
- UI Automation, moving elements
ms.assetid: 4042cb44-e27e-4a03-ac36-9be1eed65b47
ms.openlocfilehash: 43b1e005cdb499fae920a0999feaa56c5409f653
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964690"
---
# <a name="move-a-ui-automation-element"></a><span data-ttu-id="7132a-102">Mover um elemento de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7132a-102">Move a UI Automation Element</span></span>
> [!NOTE]
> <span data-ttu-id="7132a-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="7132a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7132a-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7132a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7132a-105">Este exemplo demonstra como mover um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento para um local de tela especificado.</span><span class="sxs-lookup"><span data-stu-id="7132a-105">This example demonstrates how to move a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element to a specified screen location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7132a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7132a-106">Example</span></span>  
 <span data-ttu-id="7132a-107">O exemplo a seguir usa <xref:System.Windows.Automation.WindowPattern> os <xref:System.Windows.Automation.TransformPattern> padrões de controle e para mover [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] programaticamente um aplicativo de destino para locais <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> de tela discretos e acompanhar o <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span><span class="sxs-lookup"><span data-stu-id="7132a-107">The following example uses the <xref:System.Windows.Automation.WindowPattern> and <xref:System.Windows.Automation.TransformPattern> control patterns to programmatically move a [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] target application to discrete screen locations and track the <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span></span>  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a><span data-ttu-id="7132a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7132a-108">See also</span></span>

- [<span data-ttu-id="7132a-109">Exemplo de WindowPattern</span><span class="sxs-lookup"><span data-stu-id="7132a-109">WindowPattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/WindowMove)
