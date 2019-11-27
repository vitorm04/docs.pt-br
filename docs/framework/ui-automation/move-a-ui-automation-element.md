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
ms.openlocfilehash: a23280c38da55b8d5f0bd8011f9c172b0e173744
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438537"
---
# <a name="move-a-ui-automation-element"></a>Mover um elemento de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este exemplo demonstra como mover um elemento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para um local de tela especificado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa os padrões de controle <xref:System.Windows.Automation.WindowPattern> e <xref:System.Windows.Automation.TransformPattern> para mover programaticamente um aplicativo de destino [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] para locais discretos de tela e acompanhar o <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>de <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>.  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplo de WindowPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/WindowMove)
