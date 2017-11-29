---
title: "Suporte de Automação de Interface de Usuário para o Tipo de Controle de Tabela"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TableControl type
- control types, Table
- UI Automation, Table control type
ms.assetid: 9050dde5-6469-4c83-abb7-f861c24ff985
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 821f46665e6c5c4011f7b611d798d2d3a2e4892d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-table-control-type"></a>Suporte de Automação de Interface de Usuário para o Tipo de Controle de Tabela
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de tabela. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle precisa atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 Controles de tabela contém linhas e colunas de texto e, opcionalmente, cabeçalhos de linha e cabeçalhos de coluna.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle de tabela, propriedades, padrões de controle e estrutura de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de tabela, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessário  
 A tabela a seguir descreve o modo de exibição de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore que pertence aos controles de tabela e descreve o que pode ser contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Tabela<br /><br /> -Cabeçalho (0 ou 1)<br />-Texto (0 ou 1)<br />-Vários controles (0 ou mais)|Tabela<br /><br /> -Texto (0 ou mais)<br />-Vários controles (0 ou mais)|  
  
 Se um controle de tabela tem cabeçalhos de linha ou coluna, eles devem ser expostos na exibição de controle da árvore de automação de interface do usuário. Exibição de conteúdo não precisa expor essas informações porque ele pode ser acessado usando o TablePattern.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição são especialmente relevantes para controles de tabela. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|Suporte se houver um retângulo delimitador. Se não for todo ponto dentro do retângulo delimitador é clicável, e você executa o teste de hit especializado, substituir e forneça um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, deve suportar essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|O controle de tabela normalmente obtém seu nome de um rótulo de texto estático. Se não houver nenhum rótulo de texto estático, você deve atribuir uma propriedade Name que deve estar sempre disponível para explicar a finalidade da tabela.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte as observações.|Se houver um rótulo de texto estático, essa propriedade deve expor uma referência para o elemento de automação do controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Tabela|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"tabela"|Cadeia de caracteres localizada correspondente ao tipo de controle de tabela.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Consulte as observações.|Para obter mais detalhes sobre a finalidade da tabela devem ser expostos através desta propriedade se ela não for suficientemente explicada acessando NameProperty.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de tabela sempre deve ser de conteúdo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de tabela sempre deve ser um controle.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devem ser suportados por controles de tabela de padrões de controle. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Sim|O controle de tabela sempre dá suporte a esse padrão de controle porque os itens que ele contém tem dados que são apresentados em uma grade.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Sim (obrigatório com objetos filho)|Os objetos internos de uma tabela devem dar suporte a padrões de controle GridItem tanto o item de tabela. A própria tabela não precisa de suporte os padrões de controle GridItem ou item de tabela, a menos que a tabela faz parte de outra tabela.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Sim|O controle de tabela sempre tem a capacidade de ter cabeçalhos associados ao conteúdo.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Sim (obrigatório com objetos filho)|Os objetos internos de uma tabela devem dar suporte a padrões de controle GridItem tanto o item de tabela. A própria tabela não precisa de suporte os padrões de controle GridItem ou item de tabela, a menos que a tabela faz parte de outra tabela.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos que devem ser suportados por todos os controles de tabela. Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.ControlType.Table>  
 [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Visão geral de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
