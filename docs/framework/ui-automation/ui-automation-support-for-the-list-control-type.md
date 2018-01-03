---
title: "Suporte de automação de interface do usuário para o tipo de controle List"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
caps.latest.revision: "20"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6ff31bd7874af989332e83a05e644c816fc82108
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Suporte de automação de interface do usuário para o tipo de controle List
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de lista. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle precisa atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 O tipo de controle de lista fornece uma maneira de organizar um grupo ou grupos de itens e permite que um usuário selecione um ou mais desses itens. O tipo de controle de lista tem uma restrição flexível em quais tipos de elementos filho que ele pode conter. Isso permite que provedores de automação de interface do usuário dar suporte a elementos conhecidos para contêiners de seleção.  
  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos nas seções a seguir se aplicam a todos os controles que implementam o tipo de controle de lista, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Controles de contêiner de lista são um exemplo de controles que implementam o tipo de controle de lista.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessário  
 A tabela a seguir descreve os dois modos de exibição de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controles de árvore que pertencem à lista e descreve o que pode ser contido em cada modo de exibição. O modo de exibição de controle contém apenas os elementos que são controles e a exibição de conteúdo remove informações redundantes da árvore. Por exemplo, um controle de texto usado para rotular uma caixa de combinação será exposto como o `ComboBox NameProperty`. Como o controle de texto já está exposto dessa maneira por meio da exibição de controle é desnecessário expô-lo duas vezes; Portanto, ele será removido da exibição do conteúdo. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Contém os elementos que correspondem aos controles.|Remove informações redundantes da árvore para que tecnologias assistenciais trabalham com o menor conjunto de informações significativas para o usuário final.|  
|Lista<br /><br /> -DataItem (0 ou mais)<br />-ListItem (0 ou mais)<br />-Grupo (0 ou mais)<br />-Barra de rolagem (0, 1 ou 2)|Lista<br /><br /> -DataItem (0 ou mais)<br />-ListItem (0 ou mais)<br />-Grupo (0 ou mais)|  
  
 O modo de exibição de controle para um controle que implementa o tipo de controle List (como um controle de lista) consiste em:  
  
-   Zero ou mais itens dentro do controle de lista (itens podem ser baseados nos tipos de controle Item de lista ou Item de dados)  
  
-   Zero ou mais controles de grupo em um controle de lista  
  
-   Controles da barra de rolagem zero, um ou dois  
  
-  
  
 Exibição de conteúdo de um controle que implementa o tipo de controle List (como um controle de lista) consiste em:  
  
-   Zero ou mais itens dentro do controle de lista (itens podem ser baseados nos tipos de controle Item de lista ou Item de dados)  
  
-   Zero ou mais grupos dentro do controle de lista  
  
 Um controle de lista não deve ter itens que têm uma relação hierárquica diferente sendo agrupados juntos. Se os itens têm filhos no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, em seguida, o contêiner de lista deve ser baseado no tipo de controle de árvore.  
  
 Os itens selecionáveis dentro do controle de lista estarão disponíveis a partir dos descendentes no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore do controle de lista. Todos os itens dentro do controle de lista devem pertencer ao mesmo grupo de seleção. Os itens podem ser selecionados na lista devem ser expostos como tipos de controle ListItem (em vez de DataItem).  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição são especialmente relevantes para controles de lista. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|Se o controle de lista tem um ponto clicável (um ponto que pode ser clicado para fazer com que a lista definir o foco), esse ponto deve ser exposto através desta propriedade.<br /><br /> Se o valor da `IsOffScreen` propriedade é true, o <xref:System.Windows.Automation.NoClickablePointException> será gerado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, deve suportar essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|O valor da propriedade de nome de um controle de lista deve transmitir a categoria de opções que o usuário está sendo solicitado a selecionar de. Essa propriedade normalmente obtém seu nome de um rótulo de texto estático. Se não houver um rótulo de texto estático o desenvolvedor do aplicativo deve expor um valor para a propriedade nome.<br /><br /> A única vez em que essa propriedade não é necessária para controles de lista é se o controle é usado dentro da subárvore de outro controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte as observações.|Se houver um rótulo de texto estático, em seguida, essa propriedade deve expor uma referência para esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Lista|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"list"|Cadeia de caracteres localizada correspondente ao tipo de controle de lista.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de lista é sempre incluído na exibição de conteúdo do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de lista é sempre incluído na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|verdadeiro|Se o contêiner pode aceitar a entrada do teclado, em seguida, o valor da propriedade deve ser verdadeiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Consulte as observações.|O texto de ajuda para controles de lista deve explicar por que o usuário está sendo solicitado a fazer uma escolha de uma lista de opções. Por exemplo, "seleção de um item da lista definirá a resolução de vídeo do seu monitor."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Padrões de controle de automação de interface do usuário e propriedades necessários  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por controles de lista de padrões de controle. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Propriedade padrão/padrão de controle|Valor do suporte|Observações|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Necessária|Todos os controles que oferecem suporte ao tipo de controle de lista devem implementar `ISelectionProvider` quando um estado de seleção é mantido entre os itens contidos no controle. Se os itens dentro do contêiner não selecionáveis, o tipo de controle de grupo deve ser usado.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Depende|Controles de lista nem sempre exigem que um item seja selecionado.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Depende|Controles de lista podem ser o único ou a seleção de vários contêineres.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depende|Implemente esse padrão de controle se os itens no contêiner são roláveis.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Depende|Implemente esse padrão quando navegação de grade precisa estar disponível em uma base de item a item.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Depende|Implemente esse padrão de controle se o controle pode suportar vários modos de exibição dos itens no contêiner.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Nunca|`ITableProvider`Não há suporte para o tipo de controle de lista. Se o controle deve oferecer suporte a esse padrão de controle, o controle deve ser baseado no tipo de controle grade de dados.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por todos os controles de lista de eventos. Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Valor do suporte|Observações|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.ControlType.List>  
 [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
