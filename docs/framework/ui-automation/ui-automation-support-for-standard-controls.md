---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 3fde9779205ea7d0902ddd99ed192f097a159d2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221473"
---
# <a name="ui-automation-support-for-standard-controls"></a>Suporte de automação de interface do usuário para Controles Padrão
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para controles padrão em aplicativos desenvolvidos para o [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] estruturas.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Controles do Windows Presentation Foundation  
 Todos os [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos de controle que fornecem informações ou suporte à interação do usuário têm suporte nativo completo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Controles do Win32  
 A maioria dos [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] por meio de provedores do lado do cliente na UIAutomationClientsideProviders. Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.  
  
 Suporte completo é fornecido somente para controles de versão 6 do Comctrl32 (disponível com [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] e posterior).  
  
 Os seguintes controles têm suporte.  
  
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
|SysHeader32|Header/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Lista|  
|ListBox|Lista|  
|ListBox|ListItem|  
|#32768|Menu|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|Documento. Consulte a observação.|  
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
  
 **Observação** RichEdit o controle tem suporte somente para versões fornecidas com [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (em RichEd20.dll versão 3.1 e posterior e MsftEdit versão 4.1 e posteriores).  
  
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
 Controles dos Windows Forms são expostos ao [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] através de provedores do lado do cliente na UIAutomationClientsideProviders. Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação de interface do usuário.  
  
 Normalmente, controles de formulários do Windows que são gerenciados wrappers [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles comuns são suportados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Os seguintes controles têm suporte.  
  
|Nome da classe|  
|----------------|  
|Botão|  
|CheckBox|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
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
|TabControl/TabPage|  
|TextBox|  
|Temporizador|  
|Barra de ferramentas|  
|ToolTip|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|WebBrowser|  
  
 Os seguintes controles estão expostos a [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] somente através de seu suporte [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. Algumas funcionalidades podem não estar disponíveis.  
  
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
|PrintPreview-Control|  
|PrintPreview-Dialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Divisor|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Consulte também

- [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)
