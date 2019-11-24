---
title: Visão Geral dos Tipos de Controle de Automação de Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: ec2dd3635f09144985df278be1d53ead675d3080
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442633"
---
# <a name="ui-automation-control-types-overview"></a>Visão Geral dos Tipos de Controle de Automação de Interface do Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.  
  
 Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>UI Automation Control Type Requisites  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types provide a set of conditions that providers must meet. When these conditions are met, the control can use the specific control type name. Each control type has conditions for the following:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] property values—which property values are supported.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.  
  
 When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Current UI Automation Control Types  
 The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:  
  
- [Suporte de automação de interface do usuário para o tipo de controle de botão](ui-automation-support-for-the-button-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de Calendar](ui-automation-support-for-the-calendar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de CheckBox](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ComboBox](ui-automation-support-for-the-combobox-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle DataGrid](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle DataItem](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Document](ui-automation-support-for-the-document-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de edição](ui-automation-support-for-the-edit-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Group](ui-automation-support-for-the-group-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Header](ui-automation-support-for-the-header-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle HeaderItem](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Hyperlink](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de imagem](ui-automation-support-for-the-image-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de lista](ui-automation-support-for-the-list-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ListItem](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Menu](ui-automation-support-for-the-menu-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle MenuBar](ui-automation-support-for-the-menubar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle MenuItem](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de painel](ui-automation-support-for-the-pane-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ProgressBar](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle RadioButton](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ScrollBar](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Separator](ui-automation-support-for-the-separator-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle deslizante](ui-automation-support-for-the-slider-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Spinner](ui-automation-support-for-the-spinner-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle SplitButton](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle StatusBar](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle guia](ui-automation-support-for-the-tab-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle TabItem](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Table](ui-automation-support-for-the-table-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Text](ui-automation-support-for-the-text-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de posição](ui-automation-support-for-the-thumb-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle TitleBar](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de barra de ferramentas](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ToolTip](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Tree](ui-automation-support-for-the-tree-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle TreeItem](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Window](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.ControlType>
