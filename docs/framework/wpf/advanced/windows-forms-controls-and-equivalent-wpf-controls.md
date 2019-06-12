---
title: Controles dos Windows Forms e controles WPF equivalentes
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: acb8095b32364f1e22330f22df60085016bdc664
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834038"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a>Controles dos Windows Forms e controles WPF equivalentes
Muitos controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] equivalentes, mas alguns controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não têm equivalentes em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Este tópico compara os tipos de controle fornecidos pelas duas tecnologias.  
  
 Sempre é possível usar interoperação para hospedar controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que não têm equivalentes nos aplicativos baseados em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 A tabela a seguir mostra quais controles e componentes [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm funcionalidade de controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] equivalente.  
  
|Controle de Windows Forms|Controle equivalente WPF|Comentários|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<xref:System.Windows.Controls.ListBox> com a composição.||  
|<xref:System.Windows.Forms.ColorDialog>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<xref:System.Windows.Controls.ComboBox> não oferece suporte a preenchimento automático.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<xref:System.Windows.Controls.TextBox> e dois <xref:System.Windows.Controls.Primitives.RepeatButton> controles.||  
|<xref:System.Windows.Forms.ErrorProvider>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<xref:System.Windows.Controls.WrapPanel> ou <xref:System.Windows.Controls.StackPanel>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.FontDialog>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<xref:System.Windows.Window> não oferece suporte a janelas filho.|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|Nenhum controle equivalente.|Sem ajuda F1. A ajuda “O que é Isso” é substituída por ToolTips.|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|A rolagem é incorporada em controles de recipiente.|  
|<xref:System.Windows.Forms.ImageList>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|Nenhum controle equivalente.|Você pode usar o <xref:System.Windows.Documents.Hyperlink> classe para hospedar hiperlinks dentro do conteúdo de fluxo.|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|O <xref:System.Windows.Controls.ListView> controle fornece uma exibição de detalhes de somente leitura.|  
|<xref:System.Windows.Forms.MaskedTextBox>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<xref:System.Windows.Controls.Menu> estilo de controle pode aproximar o comportamento e aparência do <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> classe.|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.NumericUpDown>|<xref:System.Windows.Controls.TextBox> e dois <xref:System.Windows.Controls.Primitives.RepeatButton> controles.||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|O <xref:Microsoft.Win32.OpenFileDialog> classe é um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper em torno de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controle.|  
|<xref:System.Windows.Forms.PageSetupDialog>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|Nenhum controle equivalente.||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|O <xref:Microsoft.Win32.SaveFileDialog> classe é um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper em torno de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controle.|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<xref:System.Windows.Controls.ToolBar> com a composição.||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<xref:System.Windows.Controls.ToolBar> com a composição.||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<xref:System.Windows.Controls.ToolBar> com a composição.||  
|<xref:System.Windows.Forms.ToolStripPanel>|<xref:System.Windows.Controls.ToolBar> com a composição.||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|A rolagem é incorporada em controles de recipiente.|  
|<xref:System.Windows.Forms.WebBrowser>|<xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>|O <xref:System.Windows.Controls.Frame> controle pode hospedar páginas HTML.<br /><br /> A partir do .NET Framework 3.5 SP1, o <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> pode hospedar páginas HTML e também faz o <xref:System.Windows.Controls.Frame> controle.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Desenvolvedores de formulários do WPF Designer for Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))
- [Passo a passo: Hospedando um controle de formulários do Windows no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do WPF nos Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Migração e interoperabilidade](migration-and-interoperability.md)
