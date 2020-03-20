---
title: Suporte de automação de interface de usuário para o Tipo de Controle Tree
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Tree
- Tree control type
- UI Automation, Tree control type
ms.assetid: 312dd04d-a86b-4072-8b12-2beeabdff5e3
ms.openlocfilehash: 389506bed91d26288e9fe2ce84c00dfb27e821b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179434"
---
# <a name="ui-automation-support-for-the-tree-control-type"></a>Suporte de automação de interface de usuário para o Tipo de Controle Tree
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre suporte para o tipo de controle de árvore. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve cumprir para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> imóvel. As condições incluem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diretrizes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] específicas para a estrutura das árvores, valores de propriedade e padrões de controle.  
  
 O tipo de controle Tree é usado para recipientes cujo conteúdo tem relevância como uma hierarquia de nós, como com a forma como arquivos e pastas são exibidos no painel esquerdo do Microsoft Windows Explorer. Cada nó tem o potencial de conter outros nódulos, chamados de nódulos infantis. Os nódulos dos pais, ou nódulos que contêm nódulos infantis, podem ser exibidos como expandidos ou colapsados.  
  
 As seções a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir definem a estrutura da árvore necessária, propriedades, padrões de controle e eventos para o tipo de controle de árvore. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]todos os controles de árvores, se , Win32 ou Formulários windows.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra a visão [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle e a visão de conteúdo da árvore que diz respeito aos controles das árvores e descreve o que pode ser contido em cada exibição. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte [Visão geral da árvore de automação de ui](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Árvore<br /><br /> <ul><li>DataItem (0 ou mais)</li><li>TreeItem (0 ou mais)<br /><br /> <ul><li>TreeItem (0 ou mais)• ...</li></ul></li><li>Barra de rolagem (0, 1, 2)</li></ul>|Árvore<br /><br /> <ul><li>DataItem (0 ou mais)</li><li>TreeItem (0 ou mais)<br /><br /> <ul><li>TreeItem (0 ou mais)• ...</li></ul></li></ul>|  
  
 A visão de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controle da árvore consiste em:  
  
- Zero a muitos itens dentro do contêiner (os itens podem ser baseados no Item da Árvore, Item de Dados ou outro tipo de controle).  
  
- Zero, uma ou duas barras de rolagem.  
  
 A visualização [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de conteúdo da árvore consiste em zero ou muitos itens dentro do recipiente (os itens podem ser baseados no Item da Árvore, Item de Dados ou outro tipo de controle).  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista as propriedades cujo valor ou definição é especialmente relevante para controles de lista. Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Veja as notas.|O valor desta propriedade precisa ser único em todos os controles em uma aplicação.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Veja as notas.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Veja as notas.|Os controles das árvores têm um ponto clicável que fará com que a árvore ou um dos itens no recipiente da árvore tenham o foco definido sobre eles. Você recebe um ponto clicável para uma árvore somente se você puder clicar em algum lugar que não faça com que um dos itens seja selecionado/obter foco.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Árvore|Este valor é o mesmo para todas as estruturas de IA.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|O controle da árvore está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visualização de conteúdo da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|O controle da árvore está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visão de controle da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Veja as notas.|Se o controle puder receber foco no teclado, ele deve suportar esta propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Veja as notas.|Se o controle da árvore tiver um rótulo <xref:System.Windows.Automation.AutomationElement> associado a ele, esta propriedade devolverá um para esse rótulo. Caso contrário, a propriedade retornará`Nothing` uma referência nula (no Microsoft Visual Basic .NET).|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Árvore"|Seqüência localizada correspondente ao tipo de controle Lista.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Veja as notas.|O valor da propriedade de nome de um controle de árvore geralmente vem de um texto que rotula o controle. Se não houver um rótulo de texto, então o desenvolvedor do aplicativo deve fornecer um valor para esta propriedade.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de icarros necessários  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os padrões de controle necessários para serem suportados por controles de lista. Para obter mais informações sobre padrões de controle, consulte [Visão geral dos padrões de controle de automação de ui](ui-automation-control-patterns-overview.md).  
  
|Propriedade de padrão/padrão de controle|Suporte/Valor|Observações|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Depende|Os controles de árvore que contêm um conjunto de itens selecionáveis devem implementar este padrão de controle. Esse padrão de controle não precisa ser implementado se a seleção de um item não transmitir informações significativas ao usuário.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Veja as notas.|Implemente esta propriedade se o controle de árvore suportar uma seleção múltipla (a maioria dos controles de árvore não suporta mparas seleção múltipla).|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Veja as notas.|O valor desta propriedade é exposto se o controle exigir que um item seja selecionado.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depende|Implemente este padrão de controle se o conteúdo do recipiente da árvore puder ser rolado.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Eventos de automação de ui obrigatórios  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles de árvores. Para obter mais informações sobre eventos, consulte [Visão geral de eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.Tree>
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
