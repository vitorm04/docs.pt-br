---
title: Suporte de automação de interface do usuário para Controles Padrão
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179860"
---
# <a name="ui-automation-support-for-standard-controls"></a>Suporte de automação de interface do usuário para Controles Padrão
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico contém [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] informações sobre o suporte a [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]controles padrão em aplicativos desenvolvidos para as estruturas, Win32 e Windows Forms.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a>Controles da Fundação de Apresentação do Windows  
 Todos [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] os elementos de controle que fornecem informações [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ou suporte para interação do usuário têm suporte nativo completo para . Outros elementos, como painéis, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]não são visíveis para .  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a>Controles Win32  
 A maioria dos controles Win32 são expostos através [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] de provedores do lado do cliente em UIAutomationClientsideProviders.dll. Este conjunto é automaticamente registrado para uso com aplicativos clientes de automação de interface do usuário.  
  
 O suporte completo é fornecido apenas para controles da versão 6 do *ComCtrl32.dll*.  
  
 Os seguintes controles são suportados.  
  
|Nome da classe|Tipo de controle|  
|----------------|------------------|  
|Botão|Botão|  
|Botão|RadioButton|  
|Botão|Agrupar|  
|Botão|CheckBox|  
|Botão|Hyperlink|  
|Botão|SplitButton|  
|Botão|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Editar|Document|  
|Editar|Editar|  
|Syslink|Hyperlink|  
|Estático|Texto|  
|Estático|Imagem|  
|SysIPAddress32|Personalizado|  
|SysHeader32|Cabeçalho/cabeçalhoItem|  
|SysListView32|DataGrid|  
|SysListView32|Lista|  
|ListBox|Lista|  
|ListBox|Listitem|  
|#32768|Menu|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|Richedit|Documento. Veja a nota.|  
|RichEdit20A|Document|  
|RichEdit20W|Document|  
|RichEdit50W|Document|  
|ScrollBar|Controle deslizante|  
|msctls_trackbar32|Controle deslizante|  
|msctls_updown32|Controle giratório|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tab|  
|SysTabControl32|Tabitem|  
|Barra de ferramentasJanela32|ToolBar|  
|Barra de ferramentasJanela32|MenuItem|  
|Barra de ferramentasJanela32|Botão|  
|Barra de ferramentasJanela32|CheckBox|  
|Barra de ferramentasJanela32|RadioButton|  
|Barra de ferramentasJanela32|Separador|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|RebarWindow32|Barra de ferramentas|  
|SysTreeView32|Árvore|  
|SysTreeView32|Treeitem|  
  
 **Nota** O controle RichEdit é suportado apenas para versões enviadas com o Windows Vista (na versão RichEd20.dll 3.1 e posteriores, e na versão 4.1 do MsftEdit.dll e posteriores).  
  
 Os seguintes controles não são suportados.  
  
|Nome da classe|Tipo de controle|  
|----------------|------------------|  
|SysAnimate32|Imagem|  
|SysPager|Controle giratório|  
|SysDateTimePick32|Personalizado|  
|SysMonthCal32|Calendário|  
|MS_WINNOTE|Dica de Ferramenta|  
|VBBubble|Dica de Ferramenta|  
|ScrollBar (quando usado como controle autônomo)|Controle deslizante|  
|SuperGrid|Personalizado|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a>Controles de Windows Forms  
 Os controles do Windows [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Forms são expostos através de provedores do lado do cliente em UIAutomationClientsideProviders.dll. Este conjunto é automaticamente registrado para uso com aplicativos clientes de automação de interface do usuário.  
  
 Normalmente, os controles do Windows Forms que são invólucros gerenciados para controles comuns do Win32 são suportados por [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Os seguintes controles são suportados.  
  
|Nome da Classe|  
|----------------|  
|Botão|  
|CheckBox|  
|CheckedListBox|  
|Colordialog|  
|ComboBox|  
|Folderbrowser|  
|Fontdialog|  
|GroupBox|  
|Hscrollbar|  
|Imagelist|  
|Rótulo|  
|ListBox|  
|ListView|  
|Menu principal/menu de contexto|  
|MonthCalendar|  
|Notifyicon|  
|OpenFileDialog|  
|Pagesetupdialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|Scrollablecontrol|  
|Soundplayer|  
|StatusBar|  
|Guias/página de guias|  
|TextBox|  
|Timer|  
|Barra de ferramentas|  
|ToolTip|  
|Trackbar|  
|TreeView|  
|Vscrollbar|  
|WebBrowser|  
  
 Os controles a seguir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] são expostos apenas através de seu suporte para acessibilidade ativa da Microsoft. Algumas funcionalidades podem não estar disponíveis.  
  
|Nome do controle|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|Domainupdown|  
|ErrorProvider|  
|Flowlayoutpanel|  
|Formulário|  
|Linklabel|  
|HelpProvider|  
|Maskedtextbox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Painel|  
|PictureBox|  
|PrintDocument|  
|Controle de visualização de impressão|  
|Impressãovisualização-caixa de diálogo|  
|PropertyGrid|  
|Usercontrol|  
|ToolStrip|  
|Tablelayoutpanel|  
|Painel splitcontainer/splitter|  
|Splitter|  
|Container de rafting|  
|StatusStrip|  
  
## <a name="see-also"></a>Confira também

- [Tipos de controle de automação de interface do usuário](ui-automation-control-types.md)
