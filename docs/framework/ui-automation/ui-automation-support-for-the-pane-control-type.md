---
title: "Suporte de automação de interface de usuário para o Tipo de Controle Pane"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Pane control type
- Pane control type
- control types, Pane
ms.assetid: 79761191-4449-4630-899c-9cbdb8867d3f
caps.latest.revision: "25"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d8b5d1dac39e36144ee3d7acdc0fbdf854e4235b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-pane-control-type"></a>Suporte de automação de interface de usuário para o Tipo de Controle Pane
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de painel. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle precisa atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 O tipo de controle do painel é usado para representar um objeto dentro de um quadro ou janela do documento. Os usuários podem navegar entre os controles de painel e dentro do conteúdo do painel atual, mas não é possível navegar entre os itens nos painéis diferentes. Assim, controles de painel representam um nível de agrupamento abaixo das janelas ou documentos, mas acima dos controles individuais. O usuário navega entre os painéis pressionando TAB, F6 ou CTRL + TAB, dependendo do contexto. Nenhuma navegação de teclado específicos é necessário para o tipo de controle de painel.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura, propriedades, padrões de controle e eventos para o tipo de controle do painel de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de lista, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessário  
 A tabela a seguir descreve o modo de exibição de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore que se refere ao painel controla e descreve o que pode ser contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Painel|Painel|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição são especialmente relevantes para controles de painel. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, deve suportar essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|O valor para essa propriedade sempre deve ser um título claro, conciso e significativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|Essa propriedade expõe um ponto clicável do controle de painel que faz com que o painel em foco quando ele for clicado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte as observações.|Controles de painel geralmente não têm um rótulo estático. Se houver um rótulo de texto estático, devem ser exposto através desta propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Painel|Esse valor é o mesmo para todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] estruturas.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"painel"|Cadeia de caracteres localizada correspondente ao tipo de controle de painel.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|Controles de painel sempre são incluídos na exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|Controles de painel sempre são incluídos na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|O texto de ajuda para controles de painel deve explicar a finalidade do quadro e como ela está relacionada a outras molduras. Uma descrição será necessária se a finalidade e relacionamento de quadros não for clara do valor da `NameProperty`. "|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|Consulte as observações.|Se uma determinada combinação de teclas coloca o foco para o painel e em seguida, essas informações devem ser expostas através desta propriedade.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] padrões devem ser suportados por todos os controles de painel de controle. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Depende|Implemente esse padrão de controle se o controle de painel pode ser movido, redimensionado ou girado na tela.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Nunca|Se você precisar implementar esse padrão de controle, o controle deve ser baseado no <xref:System.Windows.Automation.ControlType.Window> tipo de controle.|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|Depende|Implemente esse padrão de controle se o controle de painel pode ser encaixado.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depende|Implemente esse padrão de controle se o controle de painel pode ser rolado.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos que devem ser suportados por todos os controles de painel. Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Valor do suporte|Observações|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Nunca|Nenhum|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Nunca|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>evento de propriedade alterada.|Nunca|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
<a name="Pane_Control_Type_Example"></a>   
## <a name="pane-control-type-example"></a>Exemplo de tipo de controle de painel  
 A imagem a seguir ilustra um controle que implementa o tipo de controle de painel.  
  
 ![Captura de tela de janela de miniaplicativo com dois painéis](../../../docs/framework/ui-automation/media/uiauto-pane.GIF "uiauto_pane")  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Árvore - exibição de controle|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Árvore - exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>Painel</li><li>Tree (padrão Scroll)<br /><br /> <ul><li>TreeItem</li><li>Painel</li><li>Editar (padrão de rolagem</li></ul></li></ul>|-Painel<br />-Tree (padrão Scroll)<br />-TreeItem<br />-... Painel<br />-Editar<br />-(Role a tela padrão)|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.ControlType.Pane>  
 [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Visão geral de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
