---
title: Suporte de automação de interface de usuário para o tipo de controle ListItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: 245f9030897d54a2f1c95d5ce6369b67d23cb319
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179696"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle ListItem
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações <xref:System.Windows.Automation.ControlType.ListItem> sobre suporte para o tipo de controle. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve cumprir para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> imóvel. As condições incluem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diretrizes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] específicas para a estrutura das árvores, valores de propriedade e padrões de controle.  
  
 Os controles de itens de lista são um exemplo de controles que implementam o tipo de controle ListItem.  
  
 As seções a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir definem a estrutura da árvore necessária, propriedades, padrões de controle e eventos para o tipo de controle ListItem. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]todos os controles de lista, se , Win32 ou Formulários windows.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra a exibição [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle e a exibição de conteúdo da árvore que diz respeito aos controles de itens de lista e descreve o que pode ser contido em cada exibição. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte [Visão geral da árvore de automação de ui](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Listitem<br /><br /> - Imagem (0 ou mais)<br />- Texto (0 ou mais)<br />- Editar (0 ou mais)|Listitem|  
  
 Os filhos de um controle de item [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de lista dentro da visualização de conteúdo da árvore devem ser sempre "0". Se a estrutura do controle for tal que outros itens estejam contidos abaixo do item da lista, ele deve seguir os requisitos para o suporte de automação de ui para o tipo [de controle treeitem tipo](ui-automation-support-for-the-treeitem-control-type.md) de controle.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista as propriedades cujo valor ou definição é especialmente relevante para listar controles de itens. Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Veja as notas.|O valor desta propriedade precisa ser único em todos os controles em uma aplicação.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Veja as notas.|Este valor desta propriedade deve incluir a área do conteúdo de imagem e texto do item da lista.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Depende|Se o controle de lista tiver um ponto clicável (um ponto que pode ser clicado para fazer com que a lista se concentre) então esse ponto deve ser exposto através desta propriedade. Se o controle da lista estiver completamente coberto por <xref:System.Windows.Automation.NoClickablePointException> itens da lista de descendentes, ele levantará um para indicar que o cliente deve pedir a um item dentro do controle de lista um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Veja as notas.|O valor da propriedade de nome de um item de lista vem do conteúdo de texto do item.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Veja as notas.|Se houver um rótulo de texto estático, então esta propriedade deve expor uma referência a esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Listitem|Este valor é o mesmo para todas as estruturas de IA.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Item de lista"|String localizada correspondente ao tipo de controle ListItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|O controle de lista está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visualização de conteúdo da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|O controle de lista está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visão de controle da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Se o contêiner pode aceitar a entrada do teclado, então esse valor de propriedade deve ser verdadeiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|O texto ajuda para controles de lista deve explicar por que o usuário está sendo solicitado a fazer uma escolha a partir de uma lista de opções, que é tipicamente o mesmo tipo de informação apresentada através de uma dica de ferramenta. Por exemplo, "Selecione um item para definir a resolução do display para o monitor."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Depende|Esta propriedade deve ser exposta para controles de itens de lista que representam um objeto subjacente. Esses controles de itens de lista normalmente têm um ícone associado ao controle que os usuários associam com o objeto subjacente.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Depende|Essa propriedade deve retornar um valor para saber se o item da lista está atualmente em exibição no contêiner pai que implementa o padrão de controle Scroll.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de icarros necessários  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os padrões de controle necessários para serem suportados pelos controles de itens de lista. Para obter mais informações sobre padrões de controle, consulte [Visão geral dos padrões de controle de automação de ui](ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Sim|O controle de itens de lista deve implementar este padrão de controle. Isso permite que os controles de itens de lista sejam transmitidos quando forem selecionados.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Depende|Se o item da lista estiver contido em um contêiner que seja rolável, esse padrão de controle deve ser implementado.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Depende|Se o item da lista estiver verificado e a ação não realizar uma alteração de estado de seleção, esse padrão de controle deve ser implementado.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Depende|Se o item pode ser manipulado para mostrar ou ocultar informações, então esse padrão de controle deve ser implementado.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Depende|Se o item pode ser editado, esse padrão de controle deve ser implementado. Alterações no controle de itens da lista <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>causarão alterações nos valores de , e <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Depende|Se o item para item de navegação espacial for suportado dentro do contêiner da lista e o contêiner estiver disposto em linhas e colunas, o padrão de controle de Item de Grade deve ser implementado.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Depende|Se o item tiver um comando que possa ser executado nele, separado da seleção, esse padrão deve ser implementado. Esta é tipicamente uma ação associada ao duplo clique no controle do item da lista. Exemplos seriam o lançamento de um documento do Microsoft Windows Explorer ou a reprodução de um arquivo de música no Microsoft Windows Media Player.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Eventos de automação de ui obrigatórios  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles de itens da lista. Para obter mais informações sobre eventos, consulte [Visão geral de eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.ListItem>
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
