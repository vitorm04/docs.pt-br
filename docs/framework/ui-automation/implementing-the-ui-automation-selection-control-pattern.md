---
title: Implementando o padrão de controle Selection de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 083a4bb56fe76c1d65015ffabf741d7e1953d2ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180128"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementando o padrão de controle Selection de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.ISelectionProvider>convenções para a implementação, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.SelectionPattern> padrão de controle é usado para apoiar controles que atuam como recipientes para uma coleção de itens infantis selecionáveis. Os filhos deste elemento <xref:System.Windows.Automation.Provider.ISelectionItemProvider>devem implementar. Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle de seleção, observe as seguintes diretrizes e convenções:  
  
- Os controles <xref:System.Windows.Automation.Provider.ISelectionProvider> que implementam permitem que itens filho único ou múltiplo sejam selecionados. Por exemplo, caixa de lista, exibição de lista e exibição de árvore suportam várias seleções, enquanto a caixa de combinação, o controle deslizante e o grupo de botão de rádio suportam uma única seleção.  
  
- Controles com alcance mínimo, máximo e contínuo, como o controle de <xref:System.Windows.Automation.Provider.IRangeValueProvider> controle <xref:System.Windows.Automation.Provider.ISelectionProvider>deslizante **de volume,** devem ser implementados em vez de .  
  
- Os controles de seleção único <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>que gerenciam controles de criança que implementam, como o controle deslizante **resolução** de tela <xref:System.Windows.Automation.Provider.ISelectionProvider>na caixa de diálogo Propriedades de **exibição** ou o controle de seleção do **Seletor** de cores do Microsoft Word (ilustrado abaixo), devem ser implementados; seus filhos devem <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider>implementar ambos e .  
  
 ![Seletor de cores com amarelo destacado.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Exemplo de Mapeamento de Cordas de Swatch de Cor  
  
- Os menus <xref:System.Windows.Automation.SelectionPattern>não suportam . Se você estiver trabalhando com itens de menu que incluem gráficos e texto (como os itens **do Preview Pane** <xref:System.Windows.Automation.Provider.IToggleProvider>no menu **Exibir** no Microsoft Outlook) e precisar transmitir estado, você deve implementar .  
  
<a name="Required_Members_for_ISelectionProvider"></a>
## <a name="required-members-for-iselectionprovider"></a>Membros obrigatórios para ISelectionProvider  
 As seguintes propriedades, métodos e <xref:System.Windows.Automation.Provider.ISelectionProvider> eventos são necessários para a interface.  
  
|Membros necessários|Type|Observações|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Propriedade|Deve apoiar eventos <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> alterados de propriedade usando e <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Propriedade|Deve apoiar eventos <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> alterados de propriedade usando e <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Evento|Levantada quando uma seleção em um contêiner mudou significativamente e <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> requer o envio de mais eventos de adição e remoção do que as permissões constantes.|  
  
 As <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> propriedades podem ser dinâmicas. Por exemplo, o estado inicial de um controle pode não ter <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> nenhum `false`item selecionado por padrão, indicando que é . No entanto, depois que um item é selecionado, o controle deve sempre ter pelo menos um item selecionado. Da mesma forma, em casos raros, um controle pode permitir que vários itens sejam selecionados na inicialização, mas posteriormente permitir que apenas seleções únicas sejam feitas.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Se o controle não está habilitado.|  
|<xref:System.InvalidOperationException>|Se o controle estiver escondido.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle SelectionItem de interface de usuário ](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
