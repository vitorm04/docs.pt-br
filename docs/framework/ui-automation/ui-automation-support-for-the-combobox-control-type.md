---
title: Suporte de automação de interface de usuário para o tipo de controle ComboBox
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
ms.openlocfilehash: 2b1629adcc9e23294daa0512070089cc72ab5810
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179788"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle ComboBox
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre suporte para o tipo de controle ComboBox. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve cumprir para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> imóvel. As condições incluem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diretrizes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] específicas para a estrutura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] das árvores, valores de propriedade, padrões de controle e eventos.  
  
 Uma caixa de combinação é uma caixa de lista combinada com um controle estático ou um controle de edição que exibe o item selecionado no momento na parte da caixa de lista da caixa de combinação. A parte da caixa de lista do controle é exibida o tempo todo ou só aparece quando o usuário seleciona a seta suspensa (que é um botão de pressão) ao lado do controle. Se o campo de seleção for um controle de edição, o usuário poderá inserir informações que não estão na lista; caso contrário, o usuário só pode selecionar itens da lista.  
  
 As seções a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir definem a estrutura da árvore necessária, propriedades, padrões de controle e eventos para o tipo de controle ComboBox. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]os controles de caixa combo, seja , Win32 ou Formulários windows.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra a exibição [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle e a visão de conteúdo da árvore que diz respeito aos controles da caixa de combinação e descreve o que pode ser contido em cada exibição. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte Visão geral da [árvore de automação de ui](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|ComboBox<br /><br /> - Editar (0 ou 1)<br />- Lista (1)<br />- Item da Lista (filho da Lista; 0 a muitos)<br />- Botão (1)|ComboBox<br /><br /> - Item de lista (0 a muitos)|  
  
 O controle de edição na exibição de controle da caixa de combinação só é necessário se a caixa de combinação puder ser editada para obter qualquer entrada, como é o caso da caixa de combinação na caixa de diálogo Executar.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista as propriedades cujo valor ou definição é especialmente relevante para os controles de caixa de combinação. Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Veja as notas.|O valor desta propriedade precisa ser único em todos os controles em uma aplicação.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Veja as notas.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Veja as notas.|Suportado se houver um retângulo delimitador. Se nem todos os pontos dentro do retângulo delimitador forem clicáveis, e você realizar testes especializados de acerto, então anular e fornecer um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Este valor é o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mesmo para todos os quadros.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Veja as notas.|O texto de ajuda para controles de caixa de combinação deve explicar por que o usuário está sendo solicitado a escolher uma opção na caixa de combinação. O texto é semelhante às informações apresentadas através de uma dica de ferramenta. Por exemplo, "Selecione um item para definir a resolução do display do monitor."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Os controles da caixa combo estão sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluídos na visualização de conteúdo da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Os controles da caixa combo estão sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluídos na visão de controle da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Os controles da caixa combo expõem um conjunto de itens de um recipiente de seleção. O controle da caixa de combinação pode receber foco no teclado, embora quando um cliente de automação de ui define o foco em uma caixa de combinação, qualquer item na subárvore da caixa de combinação pode receber o foco.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Veja as notas.|Os controles de caixa de combo normalmente têm um rótulo de texto estático que esta propriedade faz referência.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"caixa de combinação"|String localizada correspondente ao tipo de controle ComboBox.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Veja as notas.|O controle da caixa de combinação normalmente obtém seu nome a partir de um controle de texto estático.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de icarros necessários  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os padrões de controle necessários para serem suportados por todos os controles de caixa combo. Para obter mais informações sobre padrões de controle, consulte [Visão geral dos padrões de controle de automação de ui](ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Sim|O controle da caixa combo deve conter sempre o botão de parada para ser uma caixa combo.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Sim|Exibe a seleção atual na caixa de combinação. Esse suporte é delegado à caixa de lista abaixo da caixa de combinação.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Depende|Se a caixa de combinação tiver a capacidade de pegar valores de texto arbitrários, o padrão Valor deve ser suportado. Este padrão fornece a capacidade de definir programáticamente o conteúdo da seqüência da caixa de combinação. Se o padrão Valor não for suportado, isso indica que o usuário deve fazer uma seleção a partir dos itens da lista dentro da subárvore da caixa de combinação.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Never|O padrão Scroll nunca é suportado diretamente em uma caixa de combinação. Ele é suportado se uma caixa de lista contida dentro de uma caixa de combinação pode rolar. Ele só pode ser suportado quando a caixa de lista estiver visível na tela.|  
  
<a name="Required_Events"></a>
## <a name="required-events"></a>Eventos obrigatórios  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles de caixa combo. Para obter mais informações sobre eventos, consulte [Visão geral de eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>evento alterado de propriedade.|Depende|Se o controle suportar o padrão Valor, ele deve suportar este evento.|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.ComboBox>
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
