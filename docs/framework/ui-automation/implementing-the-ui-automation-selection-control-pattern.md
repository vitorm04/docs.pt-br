---
title: Implementando o padrão de controle Selection de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: fb37c55076f243c48604cbaafdb5fd32c94934f2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002925"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementando o padrão de controle Selection de automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ISelectionProvider>, incluindo informações sobre propriedades e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.SelectionPattern> padrão de controle é usado para dar suporte a controles que atuam como contêineres para uma coleção de itens filhos selecionáveis. Os filhos deste elemento devem implementar <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle de seleção, observe as seguintes diretrizes e convenções:  
  
-   Controles que implementam <xref:System.Windows.Automation.Provider.ISelectionProvider> permitir único ou filho de vários itens a serem selecionados. Por exemplo, caixa de listagem, exibição de lista e exibição de árvore dar suporte a várias seleções, enquanto a caixa de combinação, o controle deslizante e o grupo de botões de rádio dá suporte à seleção única.  
  
-   Controles que têm um intervalo mínimo, máximo e contínuo, assim como o **Volume** controle deslizante, deve implementar <xref:System.Windows.Automation.Provider.IRangeValueProvider> em vez de <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
-   Controles de seleção única que gerenciam os controles filho que implementam <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, como o **resolução de tela** controle deslizante no **as propriedades de exibição** caixa de diálogo ou o **cor Seletor** controle de seleção do [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (ilustrado abaixo), deve implementar <xref:System.Windows.Automation.Provider.ISelectionProvider>; seus filhos devem implementar ambos <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> e <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Seletor de cores com amarelo realçado. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemplo de mapeamento de cadeia de caracteres de amostra de cor  
  
-   Menus não suportam <xref:System.Windows.Automation.SelectionPattern>. Se você estiver trabalhando com itens de menu que incluem elementos gráficos e texto (como o **painel de visualização** os itens na **exibição** menu no [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) e precisar transmitir estado, você deve implementar <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Membros necessários para ISelectionProvider  
 As seguintes propriedades, métodos e eventos são necessários para o <xref:System.Windows.Automation.Provider.ISelectionProvider> interface.  
  
|Membros necessários|Tipo|Observações|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Propriedade|Deve dar suporte a eventos de alteração de propriedade usando <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> e <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Propriedade|Deve dar suporte a eventos de alteração de propriedade usando <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> e <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|evento|Gerado quando uma seleção em um contêiner mudou significativamente e requer o envio de mais eventos de adição e remoção de que o <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> permite constante.|  
  
 O <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> e <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> propriedades podem ser dinâmicas. Por exemplo, o estado inicial de um controle pode não ter todos os itens selecionados por padrão, que indica que <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> é `false`. No entanto, depois que um item é selecionado, o controle deve sempre ter pelo menos um item selecionado. Da mesma forma, em casos raros, um controle pode permitir que vários itens sejam selecionados na inicialização, mas, subsequentemente, permitir que apenas as seleções únicas a ser feita.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Se o controle não está habilitado.|  
|<xref:System.InvalidOperationException>|Se o controle está oculto.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementando o padrão de controle SelectionItem de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
