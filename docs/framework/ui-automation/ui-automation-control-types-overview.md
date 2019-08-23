---
title: Visão Geral dos Tipos de Controle de Automação de Interface do Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 5274a2a090669a9c51c5247b68d2b0460625a494
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911566"
---
# <a name="ui-automation-control-types-overview"></a>Visão Geral dos Tipos de Controle de Automação de Interface do Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]os tipos de controle são identificadores bem conhecidos que podem ser usados para indicar que tipo de controle um determinado elemento representa, como uma caixa de combinação ou um botão.  
  
 Ter um identificador conhecido torna mais fácil para os dispositivos de tecnologia assistencial determinar quais tipos de controles estão disponíveis no [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] e como interagir com os controles.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>Requisitos de tipo de controle de automação da interface do usuário  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]os tipos de controle fornecem um conjunto de condições que os provedores devem atender. Quando essas condições são atendidas, o controle pode usar o nome do tipo de controle específico. Cada tipo de controle tem condições para o seguinte:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]padrões de controle – quais padrões de controle devem ter suporte, quais padrões de controle são opcionais e quais padrões de controle não devem ser suportados pelo controle.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]valores de propriedade — quais valores de propriedade têm suporte.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]estrutura de árvore — a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore necessária para o controle.  
  
 Quando um controle atende às condições de um determinado tipo de controle, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> o valor da propriedade indicará esse tipo de controle.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Tipos de controle de automação da interface do usuário atuais  
 A lista a seguir contém o conjunto atual [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] de tipos de controle:  
  
- [Suporte de automação de interface do usuário para o tipo de controle de botão](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de Calendar](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de CheckBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ComboBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle DataGrid](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle DataItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Document](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de edição](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Group](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Header](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle HeaderItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Hyperlink](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de imagem](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de lista](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ListItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Menu](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle MenuBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle MenuItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de painel](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ProgressBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle RadioButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ScrollBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Separator](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle deslizante](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Spinner](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle SplitButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle StatusBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle guia](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle TabItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Table](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Text](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de posição](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle TitleBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle de barra de ferramentas](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle ToolTip](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Tree](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Suporte de automação de interface do usuário para o tipo de controle Window](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.ControlType>
