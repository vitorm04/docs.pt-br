---
title: "Suporte de automação de interface de usuário para o tipo de controle ToolTip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, ToolTip control type
- ToolTip control type
- control types, ToolTip
ms.assetid: c3779d78-3164-43ae-8dae-bfaeafffdd65
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2040020ba32aed97c613260948f0772355c1287f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-tooltip-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle ToolTip
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de dica de ferramenta. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle precisa atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 Controles de dica de ferramenta são janelas pop-up que contêm texto.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle de dica de ferramenta, propriedades, padrões de controle e estrutura de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de dica de ferramenta se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessário  
 A tabela a seguir descreve o modo de exibição de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controles de árvore referente a dica de ferramenta e descreve o que pode ser contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|ToolTip<br /><br /> -Texto (0 ou mais)<br />-Imagem (0 ou mais)|ToolTip|  
  
 Controles de dica de ferramenta aparecem somente na exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore se eles podem receber o foco do teclado. Caso contrário, todas as informações da dica de ferramenta está disponível na `HelpTextProperty` no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a dica de ferramenta está fazendo referência ao elemento.  
  
 Dicas de ferramenta devem aparecer sob o controle que suas informações se refere a. Os clientes devem escutar a `ToolTipOpenedEvent` para garantir que eles consistentemente obtenham informações contidas na dica de ferramenta.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição é especialmente relevante para controles de dica de ferramenta. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|O ponto clicável deve ser parte da dica de ferramenta que irá ignorar o controle. Algumas dicas de ferramenta não têm essa capacidade e não terá um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, deve suportar essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|O nome do controle de dica de ferramenta é o texto que é exibido na dica de ferramenta.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Controles de dica de ferramenta sempre são rotulados automaticamente pelo seu conteúdo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ToolTip|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"dica de ferramenta"|Cadeia de caracteres localizada correspondente ao tipo de controle de dica de ferramenta.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Depende|Se o controle de dica de ferramenta pode receber o foco do teclado, ele deverá ser na exibição de conteúdo da árvore. Se ele é somente texto, está disponível como o HelpTextProperty do controle que o gerou.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de dica de ferramenta sempre deve ser um controle.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por controles de dica de ferramenta de padrões de controle. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Depende|Dicas de ferramenta que podem ser fechadas clicando em um item de interface do usuário devem oferecer suporte ao WindowPattern para que eles podem fechada automaticamente.|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Depende|Para melhor acessibilidade, um controle de dica de ferramenta pode dar suporte o padrão de controle de texto, embora não seja necessário. O padrão de controle de texto é útil quando o texto com estilo avançado e os atributos (por exemplo, cor, negrito e itálico).|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessário  
 Controles de dica de ferramenta devem gerar o `ToolTipOpenedEvent` quando eles aparecem na tela. O evento irá incluir uma referência para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento da dica de ferramenta em si.  
  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos que devem ser suportados por todos os controles de dica de ferramenta. Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.ControlType.ToolTip>  
 [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Visão geral de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
