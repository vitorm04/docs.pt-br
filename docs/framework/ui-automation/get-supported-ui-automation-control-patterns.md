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
ms.openlocfilehash: 7b194d9430f27fb85723a91f5786ed11a60bfa85
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040988"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Obter Padrões de Controle de Automação de IU Suportados
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico mostra como recuperar objetos de padrão de controle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de elementos.  
  
### <a name="obtain-all-control-patterns"></a>Obter todos os padrões de controle  
  
1. Obtenha os <xref:System.Windows.Automation.AutomationElement> padrões de controle cujos quais você está interessado.  
  
2. Chame <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> para obter todos os padrões de controle do elemento.  
  
> [!CAUTION]
> É altamente recomendável que um cliente não use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. O desempenho pode ser seriamente afetado, pois esse método <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> chama internamente para cada padrão de controle existente. Se possível, um cliente deve chamar <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> para os principais padrões de interesse.  
  
### <a name="obtain-a-specific-control-pattern"></a>Obter um padrão de controle específico  
  
1. Obtenha os <xref:System.Windows.Automation.AutomationElement> padrões de controle cujos quais você está interessado.  
  
2. Chame <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> para consultar um padrão específico. Esses métodos são semelhantes, mas se o padrão não for encontrado, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> o gerará uma exceção <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> e `false`retornará.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir recupera <xref:System.Windows.Automation.AutomationElement> um para um item de lista e obtém <xref:System.Windows.Automation.SelectionItemPattern> um desse elemento.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Consulte também

- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
