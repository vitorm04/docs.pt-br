---
title: Obter Padrões de Controle de Automação de IU Suportados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: b1da13cf5eb39a61f40848a5f199cfd39b16d7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435645"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Obter Padrões de Controle de Automação de IU Suportados
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.  
  
### <a name="obtain-all-control-patterns"></a>Obtain All Control Patterns  
  
1. Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.  
  
2. Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.  
  
> [!CAUTION]
> It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern. If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.  
  
### <a name="obtain-a-specific-control-pattern"></a>Obtain a Specific Control Pattern  
  
1. Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.  
  
2. Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern. These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.  
  
## <a name="example"></a>Exemplo  
 The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Consulte também

- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
