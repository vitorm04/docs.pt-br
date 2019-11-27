---
title: Suporte de automação de interface do usuário para o tipo de controle List
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: c5ea011651537aa5836eeebe217239234fec40ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446738"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Suporte de automação de interface do usuário para o tipo de controle List
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de lista. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve atender para usar a propriedade <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 O tipo de controle lista fornece uma maneira de organizar um grupo ou grupos de itens simples e permite que um usuário selecione um ou mais desses itens. O tipo de controle List tem uma restrição flexível sobre quais tipos de elementos filho ele pode conter. Isso permite que os provedores de automação da interface do usuário ofereçam suporte a um elemento bem conhecido para contêineres de seleção.  
  
 Os requisitos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nas seções a seguir se aplicam a todos os controles que implementam o tipo de controle de lista, seja [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Controles de contêiner de lista são um exemplo de controles que implementam o tipo de controle de lista.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessária  
 A tabela a seguir descreve as duas exibições da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertencem a controles de lista e descreve o que pode ser contido em cada exibição. O modo de exibição de controle contém apenas elementos que são controles, e a exibição de conteúdo remove informações redundantes da árvore. Por exemplo, um controle de texto usado para rotular uma caixa de combinação será exposto como o `ComboBox NameProperty`. Como o controle de texto já está exposto dessa maneira por meio da exibição de controle, é desnecessário tê-lo exposto duas vezes; Portanto, ele é removido da exibição de conteúdo. Para obter mais informações sobre a árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [visão geral da árvore de automação da interface do usuário](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Contém os elementos que correspondem aos controles.|Remove informações redundantes da árvore para que as tecnologias assistenciais funcionem com o menor conjunto de informações significativas para o usuário final.|  
|Lista<br /><br /> -DataItem (0 ou mais)<br />-ListItem (0 ou mais)<br />-Grupo (0 ou mais)<br />-ScrollBar (0, 1 ou 2)|Lista<br /><br /> -DataItem (0 ou mais)<br />-ListItem (0 ou mais)<br />-Grupo (0 ou mais)|  
  
 O modo de exibição de controle para um controle que implementa o tipo de controle de lista (como um controle de lista) consiste em:  
  
- Zero ou mais itens dentro do controle de lista (itens podem ser baseados no item de lista ou tipos de controle de item de dados).
  
- Zero ou mais controles de grupo dentro de um controle de lista.
  
- Zero, um ou dois controles de barra de rolagem.
  
A exibição de conteúdo de um controle que implementa o tipo de controle de lista (como um controle de lista) consiste em:  
  
- Zero ou mais itens dentro do controle de lista (itens podem ser baseados no item de lista ou tipos de controle de item de dados).
  
- Zero ou mais grupos dentro do controle de lista.

Um controle de lista não deve ter itens que tenham uma relação hierárquica diferente de serem agrupados juntos. Se os itens tiverem filhos na árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], o contêiner de lista deverá ser baseado no tipo de controle de árvore.  
  
 Os itens selecionáveis dentro do controle de lista estarão disponíveis nos descendentes na árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do controle de lista. Todos os itens dentro do controle de lista devem pertencer ao mesmo grupo de seleção. Os itens selecionáveis na lista devem ser expostos como tipos de controle ListItem (em vez de DataItem).  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação da interface do usuário necessárias  
 A tabela a seguir lista as propriedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] cujo valor ou definição é especialmente relevante para controles de lista. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedades, consulte [Propriedades de automação da interface do usuário para clientes](ui-automation-properties-for-clients.md).  
  
|Propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valor|{1&gt;Observações&lt;1}|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte observações.|O valor dessa propriedade precisa ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte observações.|Se o controle de lista tiver um ponto clicável (um ponto que pode ser clicado para fazer com que a lista tenha foco), esse ponto deverá ser exposto por meio dessa propriedade.<br /><br /> Se o valor da propriedade `IsOffScreen` for true, o <xref:System.Windows.Automation.NoClickablePointException> será gerado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte observações.|Se o controle puder receber o foco do teclado, ele deverá dar suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte observações.|O valor da propriedade nome de um controle de lista deve transmitir a categoria de opções da qual o usuário está sendo solicitado a selecionar. Essa propriedade normalmente obtém seu nome de um rótulo de texto estático. Se não houver um rótulo de texto estático, o desenvolvedor do aplicativo deverá expor um valor para a propriedade Name.<br /><br /> A única vez em que essa propriedade não é necessária para controles de lista é se o controle é usado dentro da subárvore de outro controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte observações.|Se houver um rótulo de texto estático, essa propriedade deverá expor uma referência a esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Lista|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|lista|Cadeia de caracteres localizada correspondente ao tipo de controle de lista.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de lista é sempre incluído na exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de lista é sempre incluído na exibição de controle da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|verdadeiro|Se o contêiner puder aceitar entrada de teclado, esse valor de propriedade deverá ser verdadeiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Consulte observações.|O texto de ajuda para controles de lista deve explicar por que o usuário está sendo solicitado a fazer uma escolha de uma lista de opções. Por exemplo, "a seleção de um item dessa lista definirá a resolução de vídeo para o monitor."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Propriedades e padrões de controle de automação da interface do usuário necessários  
 A tabela a seguir lista os padrões de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necessários para serem suportados pelos controles de lista. Para obter mais informações sobre padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).  
  
|Propriedade padrão de controle/padrão|Suporte/valor|{1&gt;Observações&lt;1}|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Obrigatório|Todos os controles que dão suporte ao tipo de controle List devem implementar `ISelectionProvider` quando um estado de seleção é mantido entre os itens contidos no controle. Se os itens dentro do contêiner não forem selecionáveis, o tipo de controle grupo deverá ser usado.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Dependem|Os controles de lista nem sempre exigem que um item seja selecionado.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Dependem|Os controles de lista podem ser contêineres de seleção única ou múltipla.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Dependem|Implemente esse padrão de controle se os itens no contêiner forem roláveis.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Dependem|Implemente esse padrão quando a navegação de grade precisar estar disponível em um item por item base.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Dependem|Implemente esse padrão de controle se o controle puder dar suporte a várias exibições dos itens no contêiner.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|{1&gt;Nunca&lt;1}|`ITableProvider` nunca tem suporte para o tipo de controle de lista. Se o controle deve dar suporte a esse padrão de controle, o controle deve ser baseado no tipo de controle da grade de dados.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação da interface do usuário necessários  
 A tabela a seguir lista os eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necessários para serem suportados por todos os controles de lista. Para obter mais informações sobre eventos, consulte [visão geral dos eventos de automação da interface do usuário](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento|Suporte/valor|{1&gt;Observações&lt;1}|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Dependem|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Dependem|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de alteração de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de alteração de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de alteração de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.ControlType.List>
- [Visão geral de tipos de controle de automação da interface do usuário](ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](ui-automation-overview.md)
