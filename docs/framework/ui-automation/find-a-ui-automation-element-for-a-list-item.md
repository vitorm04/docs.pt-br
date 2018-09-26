---
title: Encontrar um Elemento de Automação de Interface de Usuário para um Item de Lista
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4e8822ce8d33d285475be5ec85d36c5085d46f4b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47172999"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Encontrar um Elemento de Automação de Interface de Usuário para um Item de Lista
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico mostra como recuperar um <xref:System.Windows.Automation.AutomationElement> para um item dentro de uma lista quando o índice do item é conhecido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra duas maneiras de recuperar um item especificado de uma lista, uma usando <xref:System.Windows.Automation.TreeWalker> e outra usando <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.  
  
 A primeira técnica tende a ser mais rápido para [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles, mas a segunda é mais rápida para controles do Windows Presentation Foundation (WPF).  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Consulte também  
 [Obtendo elementos de automação de interface do usuário](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
