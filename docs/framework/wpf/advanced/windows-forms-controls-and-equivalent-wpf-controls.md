---
title: Controles dos Windows Forms e controles WPF equivalentes
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: e80379700b43ed5d0e74ea890c2a0eafe67159e6
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740231"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="22f41-102">Controles dos Windows Forms e controles WPF equivalentes</span><span class="sxs-lookup"><span data-stu-id="22f41-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="22f41-103">Muitos controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] equivalentes, mas alguns controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não têm equivalentes em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22f41-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="22f41-104">Este tópico compara os tipos de controle fornecidos pelas duas tecnologias.</span><span class="sxs-lookup"><span data-stu-id="22f41-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="22f41-105">Sempre é possível usar interoperação para hospedar controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que não têm equivalentes nos aplicativos baseados em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22f41-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="22f41-106">A tabela a seguir mostra quais controles e componentes [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm funcionalidade de controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="22f41-107">Controle de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22f41-107">Windows Forms control</span></span>|<span data-ttu-id="22f41-108">Controle equivalente WPF</span><span class="sxs-lookup"><span data-stu-id="22f41-108">WPF equivalent control</span></span>|<span data-ttu-id="22f41-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="22f41-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="22f41-110">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<span data-ttu-id="22f41-111"><xref:System.Windows.Controls.ListBox> com composição.</span><span class="sxs-lookup"><span data-stu-id="22f41-111"><xref:System.Windows.Controls.ListBox> with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="22f41-112">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<span data-ttu-id="22f41-113">o <xref:System.Windows.Controls.ComboBox> não oferece suporte a preenchimento automático.</span><span class="sxs-lookup"><span data-stu-id="22f41-113"><xref:System.Windows.Controls.ComboBox> does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<span data-ttu-id="22f41-114"><xref:System.Windows.Controls.TextBox> e dois controles <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="22f41-114"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="22f41-115">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<span data-ttu-id="22f41-116"><xref:System.Windows.Controls.WrapPanel> ou <xref:System.Windows.Controls.StackPanel></span><span class="sxs-lookup"><span data-stu-id="22f41-116"><xref:System.Windows.Controls.WrapPanel> or <xref:System.Windows.Controls.StackPanel></span></span>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="22f41-117">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="22f41-118">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<span data-ttu-id="22f41-119"><xref:System.Windows.Window> não oferece suporte a janelas filhas.</span><span class="sxs-lookup"><span data-stu-id="22f41-119"><xref:System.Windows.Window> does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="22f41-120">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-120">No equivalent control.</span></span>|<span data-ttu-id="22f41-121">Sem ajuda F1.</span><span class="sxs-lookup"><span data-stu-id="22f41-121">No F1 Help.</span></span> <span data-ttu-id="22f41-122">A ajuda “O que é Isso” é substituída por ToolTips.</span><span class="sxs-lookup"><span data-stu-id="22f41-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="22f41-123">A rolagem é incorporada em controles de recipiente.</span><span class="sxs-lookup"><span data-stu-id="22f41-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="22f41-124">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="22f41-125">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-125">No equivalent control.</span></span>|<span data-ttu-id="22f41-126">Você pode usar a classe <xref:System.Windows.Documents.Hyperlink> para hospedar hiperlinks dentro do conteúdo do fluxo.</span><span class="sxs-lookup"><span data-stu-id="22f41-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="22f41-127">O controle <xref:System.Windows.Controls.ListView> fornece uma exibição de detalhes somente leitura.</span><span class="sxs-lookup"><span data-stu-id="22f41-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="22f41-128">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<span data-ttu-id="22f41-129"><xref:System.Windows.Controls.Menu> estilo de controle pode aproximar o comportamento e a aparência da classe <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22f41-129"><xref:System.Windows.Controls.Menu> control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="22f41-130">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<span data-ttu-id="22f41-131"><xref:System.Windows.Controls.TextBox> e dois controles <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="22f41-131"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="22f41-132">A classe <xref:Microsoft.Win32.OpenFileDialog> é um wrapper de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em volta do controle Win32.</span><span class="sxs-lookup"><span data-stu-id="22f41-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the Win32 control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="22f41-133">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="22f41-134">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="22f41-135">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="22f41-136">Nenhum controle equivalente.</span><span class="sxs-lookup"><span data-stu-id="22f41-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="22f41-137">A classe <xref:Microsoft.Win32.SaveFileDialog> é um wrapper de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em volta do controle Win32.</span><span class="sxs-lookup"><span data-stu-id="22f41-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the Win32 control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="22f41-138"><xref:System.Windows.Controls.ToolBar> com composição.</span><span class="sxs-lookup"><span data-stu-id="22f41-138"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="22f41-139"><xref:System.Windows.Controls.ToolBar> com composição.</span><span class="sxs-lookup"><span data-stu-id="22f41-139"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<span data-ttu-id="22f41-140"><xref:System.Windows.Controls.ToolBar> com composição.</span><span class="sxs-lookup"><span data-stu-id="22f41-140"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<span data-ttu-id="22f41-141"><xref:System.Windows.Controls.ToolBar> com composição.</span><span class="sxs-lookup"><span data-stu-id="22f41-141"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="22f41-142">A rolagem é incorporada em controles de recipiente.</span><span class="sxs-lookup"><span data-stu-id="22f41-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<span data-ttu-id="22f41-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="22f41-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span></span>|<span data-ttu-id="22f41-144">O controle de <xref:System.Windows.Controls.Frame> pode hospedar páginas HTML.</span><span class="sxs-lookup"><span data-stu-id="22f41-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="22f41-145">A partir do .NET Framework 3,5 SP1, o controle de <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> pode hospedar páginas HTML e também faz backup do controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="22f41-145">Starting in the .NET Framework 3.5 SP1, the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22f41-146">Veja também</span><span class="sxs-lookup"><span data-stu-id="22f41-146">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- <span data-ttu-id="22f41-147">[Designer do WPF para desenvolvedores de Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="22f41-147">[WPF Designer for Windows Forms Developers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))</span></span>
- [<span data-ttu-id="22f41-148">Passo a passo: hospedando um controle do Windows Forms no WPF</span><span class="sxs-lookup"><span data-stu-id="22f41-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="22f41-149">Passo a passo: hospedando um controle composto do WPF no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22f41-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="22f41-150">Migração e Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="22f41-150">Migration and Interoperability</span></span>](migration-and-interoperability.md)
