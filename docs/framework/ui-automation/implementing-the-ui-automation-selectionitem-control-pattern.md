---
title: 'Implementando o padrão de controle SelectionItem de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 02505224e4673592f1e169c40af1cfb098e5d9bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180095"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementando o padrão de controle SelectionItem de interface de usuário 
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.ISelectionItemProvider>convenções para a implementação, incluindo informações sobre propriedades, métodos e eventos. Os links para referências adicionais são listados no final da visão geral.  
  
 O <xref:System.Windows.Automation.SelectionItemPattern> padrão de controle é usado para apoiar controles que atuam como itens <xref:System.Windows.Automation.Provider.ISelectionProvider>infantis individuais e selecionáveis de controles de contêineres que implementam . Para exemplos de controles que implementam o padrão de controle SelectionItem, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle do item de seleção, observe as seguintes diretrizes e convenções:  
  
- Os controles de seleção único <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>que gerenciam controles de criança que implementam , <xref:System.Windows.Automation.Provider.ISelectionProvider> como o controle <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider>deslizante de resolução de **tela** na caixa de diálogo Propriedades de **exibição,** devem implementar e seus filhos devem implementar ambos e .  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-iselectionitemprovider"></a>Membros obrigatórios para ISelectionItemProvider  
 As seguintes propriedades, métodos e eventos <xref:System.Windows.Automation.Provider.ISelectionItemProvider>são necessários para a implementação.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Evento|Criado quando uma seleção em um contêiner <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> mudou <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> significativamente <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> e requer o envio de mais e eventos do que as permissões constantes.|  
  
- Se o resultado <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>de <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>um <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> , um ou um <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> é um único item selecionado, um deve ser levantado; caso contrário, enviar <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> conforme apropriado.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Quando alguma das seguintes tentativas é tentada:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>é chamado em um recipiente <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` de seleção única onde e um elemento já está selecionado.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>é chamado em um contêiner <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` de múltipla seleção onde e apenas um elemento é selecionado.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>é chamado em um contêiner <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` de seleção única onde e outro elemento já está selecionado.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle Selection de automação de interface do usuário](implementing-the-ui-automation-selection-control-pattern.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
- [Amostra do provedor de fragmentos](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
