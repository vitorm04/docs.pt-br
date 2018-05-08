---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3ccd6e1348125f5d901e0f093d2b5483b818719f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-standard-controls"></a>Suporte de automação de interface do usuário para Controles Padrão
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] oferece suporte para controles padrão em aplicativos desenvolvidos para o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] estruturas.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Controles do Windows Presentation Foundation  
 Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte de interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Controles de Win32  
 A maioria dos [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders. Esse assembly é registrado automaticamente para uso com aplicativos clientes de automação de interface do usuário.  
  
 Suporte completo é fornecido somente para controles da versão 6 da Comctrl32 (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).  
  
 Há suporte para os seguintes controles.  
  
|Nome da classe|Tipo de controle|  
|----------------|------------------|  
|Botão|Botão|  
|Botão|RadioButton|  
|Botão|Grupo|  
|Botão|CheckBox|  
|Botão|Hiperlink|  
|Botão|SplitButton|  
|Botão|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Editar|Documento|  
|Editar|Editar|  
|SysLink|Hiperlink|  
|Estático|Texto|  
|Estático|Image|  
|SysIPAddress32|Personalizado|  
|SysHeader32|Cabeçalho/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Lista|  
|ListBox|Lista|  
|ListBox|Item de lista|  
|#32768|Menu|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|documento. Consulte a observação.|  
|RichEdit20A|Documento|  
|RichEdit20W|Documento|  
|RichEdit50W|Documento|  
|ScrollBar|Controle deslizante|  
|msctls_trackbar32|Controle deslizante|  
|msctls_updown32|Controle giratório|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tabulação|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|Botão|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Separador|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|ReBarWindow32|Barra de ferramentas|  
|SysTreeView32|Árvore|  
|SysTreeView32|TreeItem|  
  
 **Observação** controle RichEdit o tem suporte apenas para versões fornecidas com [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (no RichEd20.dll versão 3.1 e posterior e MsftEdit versão 4.1 e posterior).  
  
 Não há suporte para os seguintes controles.  
  
|Nome da classe|Tipo de controle|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Controle giratório|  
|SysDateTimePick32|Personalizado|  
|SysMonthCal32|Calendário|  
|MS_WINNOTE|Dica de ferramenta|  
|VBBubble|Dica de ferramenta|  
|Barra de rolagem (quando usado como um controle autônomo)|Controle deslizante|  
|SuperGrid|Personalizado|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Controles de Windows Forms  
 Controles de formulários do Windows são expostos para [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders. Esse assembly é registrado automaticamente para uso com aplicativos clientes de automação de interface do usuário.  
  
 Normalmente, os controles de formulários do Windows que são gerenciados wrappers para [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Há suporte para os seguintes controles.  
  
|Nome da classe|  
|----------------|  
|Botão|  
|CheckBox|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FolderBrowserDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|Rotular|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabPage/TabControl|  
|TextBox|  
|Temporizador|  
|Barra de ferramentas|  
|ToolTip|  
|Barra de controle|  
|TreeView|  
|VscrollBar|  
|WebBrowser|  
  
 Os seguintes controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] apenas através de seu suporte para [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. Algumas funcionalidades podem não estar disponíveis.  
  
|Nome do controle|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|Formulário|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Painel|  
|PictureBox|  
|PrintDocument|  
|Controle PrintPreview|  
|Caixa de diálogo PrintPreview|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Separador|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Consulte também  
 [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)
