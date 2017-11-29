---
title: "Suporte de automação de interface de usuário para o tipo de controle MenuItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 7b7fbd8f2f667c1a3276267700182fc7d113c73e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle MenuItem
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para o tipo de controle MenuItem. Descreve o controle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] estrutura de árvore e fornece as propriedades e padrões de controle que são necessários para o tipo de controle MenuItem.  
  
 Um controle de menu permite organização hierárquica de elementos associados com comandos e manipuladores de eventos. Em um típico [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] aplicativo, uma barra de menus contém vários itens de menu (como **arquivo**, **editar**, e **janela**), e cada item de menu exibe um menu. Um menu contém uma coleção de itens de menu (como **novo**, **abrir**, e **fechar**), que pode ser expandido para exibir itens de menu adicionais ou executar uma ação específica quando clicado. Um item de menu pode ser hospedado em um menu, barra de menu ou barra de ferramentas.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle MenuItem, propriedades, padrões de controle e estrutura de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de lista, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessário  
 A tabela a seguir descreve o modo de exibição de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controles de árvore referente ao item de menu e descreve o que pode ser contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|MenuItem "Ajuda"<br /><br /> <ul><li>Menu (submenu de item de menu de Ajuda)<br /><br /> <ul><li>MenuItem "Tópicos de Ajuda"</li><li>MenuItem "Sobre o bloco de notas"</li></ul></li></ul>|MenuItem "Ajuda"<br /><br /> -MenuItem "tópicos de Ajuda".<br />-MenuItem "Sobre o bloco de notas"|  
  
 A exibição de controle do controle de item de menu tem o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mostrada acima de estrutura de árvore. Observe que o **ajuda** item de menu é inlcluded para ilustrar melhor a estrutura em um menu típico para a hierarquia de submenu.  
  
 O modo de exibição de conteúdo, Menu está ausente do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore porque ela não transmite informações significativas para o usuário final.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição são especialmente relevantes para controles de item. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propriedade|Valor|Descrição|  
|--------------|-----------|-----------------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|Suporte se houver um retângulo delimitador. Se não for todo ponto dentro do retângulo delimitador é clicável, e você executa o teste de hit especializado, substituir e forneça um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, deve suportar essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|O controle de item de menu é incluído na exibição de conteúdo do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore e self rotulada com um nome.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Nenhum rótulo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|MenuItem|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"item de menu"|Cadeia de caracteres localizada correspondente ao tipo de controle MenuItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de item de menu nunca é incluído na exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de item de menu sempre deve ser incluído na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por controles de item de menu de padrões de controle. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Propriedade de padrão de controle|Suporte|Observações|  
|------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Depende|Se o controle pode ser expandido ou recolhido, implemente <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Depende|Se o controle executa uma ação única ou comando, implemente <xref:System.Windows.Automation.Provider.IInvokeProvider>.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Depende|Se o controle representa uma opção que pode ser ativada ou desativada, implemente <xref:System.Windows.Automation.Provider.IToggleProvider>.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Depende|Se o controle é usado para selecionar de uma lista de opções entre os itens de menu, implemente <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.|  
  
<a name="UI_Automation_Events_for_Menu_Item"></a>   
## <a name="ui-automation-events-for-menu-item"></a>Eventos de automação de interface do usuário para o Item de Menu  
 A seguinte tabela lista o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] eventos associados com o controle de item de menu.  
  
|Evento|Suporte|Explicação|  
|-----------|-------------|-----------------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|Deve ser gerado se o controle oferece suporte ao padrão de controle Invoke.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>evento de propriedade alterada.|Depende|Deve ser gerado se o controle oferece suporte ao padrão de controle Toggle.|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>evento de propriedade alterada.|Depende|Deve ser gerado se o controle oferece suporte ao padrão de controle de expandir recolher.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Depende|nenhuma.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos que devem ser suportados por todos os controles de item de menu. Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Valor do suporte|Observações|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
<a name="Legacy_Issues"></a>   
## <a name="legacy-issues"></a>Questões herdadas  
 Alternância padrão só serão suportados quando o [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] item de menu é verificado e pode ser programaticamente determinado necessário para dar suporte ao padrão de alternância. Porque o [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] item de menu não expõe se ele tem a capacidade de ser verificado, Invoke Pattern terá suporte quando o item de menu não estiver marcado. Uma exceção será feita para sempre oferecer suporte a Invoke Pattern mesmo para itens de menu que só devem dar suporte a alternância padrão. Isso é para que clientes não fiquem confusos que um elemento que tinha suporte Invoke Pattern (quando o item de menu foi desmarcado) não oferece suporte para o padrão depois que ele fica marcado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.ControlType.MenuItem>  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Visão geral de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
