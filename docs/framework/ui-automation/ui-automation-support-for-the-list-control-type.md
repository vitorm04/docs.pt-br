---
title: Suporte de automação de interface do usuário para o tipo de controle List
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: 2926e06cfbe065ad8a5bccdb7ebaf16596721def
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179714"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Suporte de automação de interface do usuário para o tipo de controle List
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre suporte para o tipo de controle de lista. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve cumprir para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> imóvel. As condições incluem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diretrizes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] específicas para a estrutura das árvores, valores de propriedade e padrões de controle.  
  
 O tipo de controle lista fornece uma maneira de organizar um grupo plano ou grupos de itens e permite que um usuário selecione um ou mais desses itens. O tipo de controle Lista tem uma restrição frouxa sobre quais tipos de elementos infantis ele pode conter. Isso permite que os provedores de automação de ui suportem um elemento bem conhecido para contêineres de seleção.  
  
 Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos nas seções a seguir se aplicam a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]todos os controles que implementam o tipo de controle de lista, seja , Win32 ou Formulários do Windows. Os controles de contêiner de lista são um exemplo de controles que implementam o tipo de controle Lista.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] as duas visões da árvore que pertencem aos controles de lista e descreve o que pode ser contido em cada exibição. A exibição de controle contém apenas elementos que são controles, e a exibição de conteúdo remove informações redundantes da árvore. Por exemplo, um controle de texto usado para rotular `ComboBox NameProperty`uma caixa de combinação será exposto como o . Como o controle de texto já está exposto dessa forma através da visão de controle, é desnecessário expô-lo duas vezes; portanto, ele é removido da exibição de conteúdo. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte [Visão geral da árvore de automação de ui](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Contém os elementos que correspondem aos controles.|Remove informações redundantes da árvore para que as tecnologias assistivas funcionem com o menor conjunto de informações significativas para o usuário final.|  
|Lista<br /><br /> - DataItem (0 ou mais)<br />- ListItem (0 ou mais)<br />- Grupo (0 ou mais)<br />- Barra de Rolagem (0, 1 ou 2)|Lista<br /><br /> - DataItem (0 ou mais)<br />- ListItem (0 ou mais)<br />- Grupo (0 ou mais)|  
  
 A exibição de controle de um controle que implementa o tipo de controle de lista (como um controle de lista) consiste em:  
  
- Zero ou mais itens dentro do controle de lista (os itens podem ser baseados nos tipos de controle de itens de lista ou de itens de dados).
  
- Zero ou mais controles de grupo dentro de um controle de lista.
  
- Zero, um ou dois controles de barra de rolagem.
  
A exibição de conteúdo de um controle que implementa o tipo de controle de lista (como um controle de lista) consiste em:  
  
- Zero ou mais itens dentro do controle de lista (os itens podem ser baseados nos tipos de controle de itens de lista ou de itens de dados).
  
- Zero ou mais grupos dentro do controle de lista.

Um controle de lista não deve ter itens que tenham uma relação hierárquica além de serem agrupados. Se os itens tiverem filhos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] na árvore, o recipiente da lista deve ser baseado no tipo de controle árvore.  
  
 Os itens selecionáveis no controle da lista estarão disponíveis [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dos descendentes na árvore do controle da lista. Todos os itens dentro do controle de lista devem pertencer ao mesmo grupo de seleção. Os itens selecionáveis da lista devem ser expostos como tipos de controle ListItem (em vez de DataItem).  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista as propriedades cujo valor ou definição é especialmente relevante para controles de lista. Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Veja as notas.|O valor desta propriedade precisa ser único em todos os controles em uma aplicação.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Veja as notas.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Veja as notas.|Se o controle de lista tiver um ponto clicável (um ponto que pode ser clicado para fazer com que a lista tenha foco), então esse ponto deve ser exposto através desta propriedade.<br /><br /> Se o valor `IsOffScreen` da propriedade for <xref:System.Windows.Automation.NoClickablePointException> verdadeiro, então o será aumentado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Veja as notas.|Se o controle puder receber foco no teclado, ele deve suportar esta propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Veja as notas.|O valor da propriedade Name de um controle de lista deve transmitir a categoria de opções que o usuário está sendo solicitado a selecionar. Esta propriedade normalmente obtém seu nome a partir de um rótulo de texto estático. Se não houver um rótulo de texto estático, o desenvolvedor do aplicativo deve expor um valor para a propriedade Nome.<br /><br /> A única vez que esta propriedade não é necessária para controles de lista é se o controle for usado dentro da subárvore de outro controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Veja as notas.|Se houver um rótulo de texto estático, então esta propriedade deve expor uma referência a esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Lista|Este valor é o mesmo para todas as estruturas de IA.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Lista"|Seqüência localizada correspondente ao tipo de controle Lista.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|O controle de lista está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visualização de conteúdo da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|O controle de lista está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visão de controle da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Se o contêiner pode aceitar a entrada do teclado, então esse valor de propriedade deve ser verdadeiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Veja as notas.|O texto ajuda para controles de lista deve explicar por que o usuário está sendo solicitado a fazer uma escolha a partir de uma lista de opções. Por exemplo, "Seleção de um item desta lista definirá a resolução do display para o monitor."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Padrões e propriedades de controle de automação de ida e clara necessários  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os padrões de controle necessários para serem suportados por controles de lista. Para obter mais informações sobre padrões de controle, consulte [Visão geral dos padrões de controle de automação de ui](ui-automation-control-patterns-overview.md).  
  
|Propriedade de padrão/padrão de controle|Suporte/Valor|Observações|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Obrigatório|Todos os controles que suportam `ISelectionProvider` o tipo de controle de lista devem ser implementados quando um estado de seleção é mantido entre os itens contidos no controle. Se os itens dentro do contêiner não forem selecionáveis, o tipo de controle Grupo deve ser usado.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Depende|Os controles de lista nem sempre exigem que um item seja selecionado.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Depende|Os controles de lista podem ser recipientes de seleção única ou múltipla.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depende|Implemente este padrão de controle se os itens do contêiner estiverem roláveis.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Depende|Implemente este padrão quando a navegação em rede precisar estar disponível em um item por item.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Depende|Implemente este padrão de controle se o controle puder suportar várias visualizações dos itens no recipiente.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Never|`ITableProvider`nunca é suportado para o tipo de controle lista. Se o controle deve suportar esse padrão de controle, então o controle deve ser baseado no tipo de controle Data Grid.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Eventos de automação de ui obrigatórios  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles de lista. Para obter mais informações sobre eventos, consulte [Visão geral de eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte/Valor|Observações|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.List>
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
