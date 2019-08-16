---
title: Implementando o padrão de controle Selection de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 2297ea0a181fe0fd16aa32b85909acdad5f129ab
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545193"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementando o padrão de controle Selection de automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.ISelectionProvider>, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.SelectionPattern> padrão de controle é usado para dar suporte a controles que atuam como contêineres para uma coleção de itens filho selecionáveis. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de seleção, observe as seguintes diretrizes e convenções:  
  
- Os controles que <xref:System.Windows.Automation.Provider.ISelectionProvider> implementam permitem que um único ou vários itens filho sejam selecionados. Por exemplo, caixa de listagem, exibição de lista e exibição de árvore dão suporte a várias seleções, enquanto que a caixa de combinação, o controle deslizante e o grupo de botões de opção dão suporte à seleção única.  
  
- Controles que têm um intervalo mínimo, máximo e contínuo, como o controle deslizante de **volume** , devem implementar <xref:System.Windows.Automation.Provider.IRangeValueProvider> em vez <xref:System.Windows.Automation.Provider.ISelectionProvider>de.  
  
- Controles de seleção única que gerenciam controles filho que <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>implementam, como o controle deslizante de **resolução de tela** na caixa de diálogo **Propriedades de exibição** ou o controle seleção de seletor de **cores** de [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] ( ilustrado abaixo), deve <xref:System.Windows.Automation.Provider.ISelectionProvider>implementar; seus filhos devem <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> implementar e <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Seletor de cores com amarelo realçado.](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemplo de mapeamento de cadeia de caracteres de amostra de cor  
  
- Os menus não dão <xref:System.Windows.Automation.SelectionPattern>suporte ao. Se você estiver trabalhando com itens de menu que incluem elementos gráficos e texto (como os itens do **painel de visualização** no menu **Exibir** no Microsoft Outlook) e precisar transmitir o estado, você deverá <xref:System.Windows.Automation.Provider.IToggleProvider>implementar o.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Membros necessários para ISelectionProvider  
 As propriedades, os métodos e os eventos a seguir são necessários <xref:System.Windows.Automation.Provider.ISelectionProvider> para a interface.  
  
|Membros necessários|Tipo|Observações|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Propriedade|Deve oferecer suporte a eventos de <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> alteração <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>de propriedade usando e.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Propriedade|Deve oferecer suporte a eventos de <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> alteração <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>de propriedade usando e.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|evento|Gerado quando uma seleção em um contêiner é alterada significativamente e requer o envio de mais eventos de adição e <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> remoção do que a constante permite.|  
  
 As <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> propriedades <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> e podem ser dinâmicas. Por exemplo, o estado inicial de um controle pode não ter nenhum item selecionado por padrão, indicando que <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> é `false`. No entanto, depois que um item é selecionado, o controle sempre deve ter pelo menos um item selecionado. Da mesma forma, em casos raros, um controle pode permitir que vários itens sejam selecionados na inicialização, mas posteriormente permitir que apenas seleções únicas sejam feitas.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Se o controle não está habilitado.|  
|<xref:System.InvalidOperationException>|Se o controle estiver oculto.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle SelectionItem de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
