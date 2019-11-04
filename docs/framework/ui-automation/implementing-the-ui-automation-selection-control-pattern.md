---
title: Implementando o padrão de controle Selection de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 39baadbad4bf5aff1cc2cd7877489f43581e0fa0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458166"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementando o padrão de controle Selection de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ISelectionProvider>, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O padrão de controle <xref:System.Windows.Automation.SelectionPattern> é usado para dar suporte a controles que atuam como contêineres para uma coleção de itens filho selecionáveis. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de seleção, observe as seguintes diretrizes e convenções:  
  
- Controles que implementam <xref:System.Windows.Automation.Provider.ISelectionProvider> permitem que um ou vários itens filho sejam selecionados. Por exemplo, caixa de listagem, exibição de lista e exibição de árvore dão suporte a várias seleções, enquanto que a caixa de combinação, o controle deslizante e o grupo de botões de opção dão suporte à seleção única.  
  
- Controles que têm um intervalo mínimo, máximo e contínuo, como o controle deslizante de **volume** , devem implementar <xref:System.Windows.Automation.Provider.IRangeValueProvider> em vez de <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
- Controles de seleção única que gerenciam controles filho que implementam <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, como o controle deslizante de **resolução de tela** na caixa de diálogo **Propriedades de exibição** ou o controle seleção de **seletor de cores** do Microsoft Word (ilustrado abaixo ), deve implementar <xref:System.Windows.Automation.Provider.ISelectionProvider>; seus filhos devem implementar tanto <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> quanto <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Seletor de cores com amarelo realçado.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemplo de mapeamento de cadeia de caracteres de amostra de cor  
  
- Os menus não dão suporte a <xref:System.Windows.Automation.SelectionPattern>. Se você estiver trabalhando com itens de menu que incluem elementos gráficos e texto (como os itens do **painel de visualização** no menu **Exibir** no Microsoft Outlook) e precisar transmitir o estado, você deve implementar <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Membros necessários para ISelectionProvider  
 As propriedades, os métodos e os eventos a seguir são necessários para a interface <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
|Membros necessários|Digite|Anotações|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|propriedade|Deve oferecer suporte a eventos de alteração de propriedade usando <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> e <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|propriedade|Deve oferecer suporte a eventos de alteração de propriedade usando <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> e <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|evento|Gerado quando uma seleção em um contêiner é alterada de forma significativa e requer o envio de mais eventos de adição e remoção do que a constante de <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> permite.|  
  
 As propriedades <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> e <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> podem ser dinâmicas. Por exemplo, o estado inicial de um controle pode não ter nenhum item selecionado por padrão, indicando que <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> é `false`. No entanto, depois que um item é selecionado, o controle sempre deve ter pelo menos um item selecionado. Da mesma forma, em casos raros, um controle pode permitir que vários itens sejam selecionados na inicialização, mas posteriormente permitir que apenas seleções únicas sejam feitas.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Se o controle não está habilitado.|  
|<xref:System.InvalidOperationException>|Se o controle estiver oculto.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle SelectionItem de automação de interface do usuário](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
