---
title: 'Implementando o padrão de controle SelectionItem de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 00a2dae818091c20649deae79c093a61b6e93732
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183749"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementando o padrão de controle SelectionItem de interface de usuário 
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listadas no final da visão geral.  
  
 O <xref:System.Windows.Automation.SelectionItemPattern> padrão de controle é usado para oferecer suporte aos controles que atuam como itens filhos selecionáveis e individuais de caixas de controles que implementam <xref:System.Windows.Automation.Provider.ISelectionProvider>. Para obter exemplos de controles que implementam o padrão de controle SelectionItem, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de Item de seleção, observe as seguintes diretrizes e convenções:  
  
-   Controles de seleção única que gerenciam os controles filho que implementam <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, como o **resolução de tela** controle deslizante no **as propriedades de exibição** caixa de diálogo deve implementar <xref:System.Windows.Automation.Provider.ISelectionProvider>e seus filhos devem implementar ambos <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> e <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Membros necessários para ISelectionItemProvider  
 As seguintes propriedades, métodos e eventos são necessários para implementar <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|evento|Gerado quando uma seleção em um contêiner mudou significativamente e requer o envio mais <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> e <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> eventos do que o <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> permite constante.|  
  
-   Se o resultado de uma <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, uma <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, ou uma <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> é um único item selecionado, uma <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> deve ser gerado; caso contrário, envie <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> conforme apropriado.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Quando qualquer um dos seguintes são tentadas:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> é chamado em um contêiner de seleção única em que <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` e um elemento já está selecionado.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> é chamado em um contêiner de seleção múltipla em que <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` e apenas um elemento é selecionado.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> é chamado em um contêiner de seleção única em que <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` e outro elemento já está selecionado.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle Selection de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Exemplo de provedor de fragmento](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
