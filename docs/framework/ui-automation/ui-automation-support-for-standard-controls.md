---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: d83713a81e7675a68482890c2401f1a0a6803abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914228"
---
# <a name="ui-automation-support-for-standard-controls"></a>Suporte de automação de interface do usuário para Controles Padrão
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico contém informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o suporte para controles padrão em aplicativos desenvolvidos para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]as [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]estruturas do [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] , e.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Controles de Windows Presentation Foundation  
 Todos [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] os elementos de controle que fornecem informações ou suporte para interação do usuário têm suporte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nativo completo para o. Outros elementos, como painéis, não são visíveis para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Controles do Win32  
 A [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] maioria dos controles é [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] exposta a provedores do lado do cliente em UIAutomationClientsideProviders. dll. Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.  
  
 O suporte completo é fornecido somente para controles da versão 6 do ComCtrl32. dll (disponível [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] com e posterior).  
  
 Há suporte para os controles a seguir.  
  
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
|RichEdit|Document. Consulte a observação.|  
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
  
 **Observação** O controle RichEdit tem suporte apenas para as versões fornecidas [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] com (em Riched20. dll versão 3,1 e posterior e MsftEdit. dll versão 4,1 e posterior).  
  
 Não há suporte para os seguintes controles.  
  
|Nome da classe|Tipo de controle|  
|----------------|------------------|  
|SysAnimate32|Image|  
|SysPager|Controle giratório|  
|SysDateTimePick32|Personalizado|  
|SysMonthCal32|Calendário|  
|MS_WINNOTE|Dessa|  
|VBBubble|Dessa|  
|ScrollBar (quando usado como um controle autônomo)|Controle deslizante|  
|Subgrade|Personalizado|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Controles de Windows Forms  
 Os controles de Windows Forms são [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] expostos a por meio de provedores do lado do cliente em UIAutomationClientsideProviders. dll. Esse assembly é registrado automaticamente para uso com aplicativos cliente de automação da interface do usuário.  
  
 Normalmente, Windows Forms controles que são wrappers gerenciados [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] para controles comuns são suportados [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]pelo. Há suporte para os controles a seguir.  
  
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
|Controlo|  
  
 Os controles a seguir são expostos [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] apenas por meio de seu suporte para o Microsoft acessibilidade ativa. Algumas funcionalidades podem não estar disponíveis.  
  
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
