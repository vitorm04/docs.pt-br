---
title: Implementando o padrão de controle SelectionItem de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 53a5a739918e61d53b3102c2c85d4ef2b8425173
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447114"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementando o padrão de controle SelectionItem de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final da visão geral.  
  
 O padrão de controle de <xref:System.Windows.Automation.SelectionItemPattern> é usado para dar suporte a controles que atuam como itens filho individuais selecionáveis de controles de contêiner que implementam <xref:System.Windows.Automation.Provider.ISelectionProvider>. Para obter exemplos de controles que implementam o padrão de controle SelectionItem, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle item de seleção, observe as seguintes diretrizes e convenções:  
  
- Controles de seleção única que gerenciam controles filho que implementam <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, como o controle deslizante de **resolução de tela** na caixa de diálogo **Propriedades de exibição** , devem implementar <xref:System.Windows.Automation.Provider.ISelectionProvider> e seus filhos devem implementar ambos <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> e <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Membros necessários para ISelectionItemProvider  
 As propriedades, os métodos e os eventos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Membros necessários|Tipo de membro|{1&gt;Observações&lt;1}|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Evento|Gerado quando uma seleção em um contêiner é alterada significativamente e requer o envio de mais <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> e <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> eventos do que a constante <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> permite.|  
  
- Se o resultado de um <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, um <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>ou um <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> for um único item selecionado, um <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> deverá ser gerado; caso contrário, envie <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>/ <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> conforme apropriado.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Quando qualquer uma das seguintes opções for tentada:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> é chamado em um contêiner de seleção única em que <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` e um elemento já está selecionado.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> é chamado em um contêiner de várias seleções, em que <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty> = `true` e apenas um elemento é selecionado.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> é chamado em um contêiner de seleção única em que <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty> = `false` e outro elemento já está selecionado.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle Selection de automação de interface do usuário](implementing-the-ui-automation-selection-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
- [Exemplo de provedor de fragmento](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
