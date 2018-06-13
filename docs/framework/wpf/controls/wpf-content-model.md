---
title: Modelo de conteúdo do WPF
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: 48e96b04a3459aa18a52624758d5fa2347570fcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558194"
---
# <a name="wpf-content-model"></a>Modelo de conteúdo do WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é uma plataforma de apresentação que fornece muitos controles e tipos de controle cujo objetivo principal é exibir diferentes tipos de conteúdo. Para determinar qual controle usar ou de qual controle derivar, você deve compreender os tipos de objetos que um controle específico pode exibir.  
  
 Este tópico resume o modelo de conteúdo para os controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o tipos semelhantes a controle. O modelo de conteúdo descreve qual conteúdo pode ser usado em um controle. Este tópico também lista as propriedades de conteúdo para cada modelo de conteúdo. Uma propriedade de conteúdo é uma propriedade que é usada para armazenar o conteúdo do objeto.  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Classes que Contêm Conteúdo Arbitrário  
 Alguns controles podem conter um objeto de qualquer tipo, como uma cadeia de caracteres, um <xref:System.DateTime> objeto, ou um <xref:System.Windows.UIElement> que é um contêiner para outros itens. Por exemplo, um <xref:System.Windows.Controls.Button> pode conter uma imagem e texto; ou um <xref:System.Windows.Controls.CheckBox> pode conter o valor de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem quatro classes que podem conter conteúdo arbitrário. A tabela a seguir lista as classes, que herdam de <xref:System.Windows.Controls.Control>.  
  
|Classes que contêm conteúdo arbitrário|Conteúdo|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Um único objeto arbitrário.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Um cabeçalho e um único item, que são objetos arbitrários.|  
|<xref:System.Windows.Controls.ItemsControl>|Uma coleção de objetos arbitrários.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Um cabeçalho e uma coleção de itens, que são objetos arbitrários.|  
  
 Os controles que herdam essas classes podem conter o mesmo tipo de conteúdo e tratar o conteúdo da mesma forma. A ilustração a seguir mostra um controle de cada modelo de conteúdo que contém uma imagem e texto.  
  
 ![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Controles que contêm um único objeto arbitrário  
 O <xref:System.Windows.Controls.ContentControl> classe contém uma única parte do conteúdo arbitrário. A propriedade de conteúdo é <xref:System.Windows.Controls.ContentControl.Content%2A>. Os seguintes controles herdam <xref:System.Windows.Controls.ContentControl> e usar o modelo de conteúdo:  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 A ilustração a seguir mostra quatro botões cujo <xref:System.Windows.Controls.ContentControl.Content%2A> é definido como uma cadeia de caracteres, um <xref:System.DateTime> objeto, um <xref:System.Windows.Shapes.Rectangle>e um <xref:System.Windows.Controls.Panel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>.  
  
 ![Quatro botões](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")  
Quatro botões que têm diferentes tipos de conteúdo  
  
 Para obter um exemplo de como definir o <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade, consulte <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Controles que contêm um único objeto arbitrário e um cabeçalho  
 O <xref:System.Windows.Controls.HeaderedContentControl> classe herda de <xref:System.Windows.Controls.ContentControl> e exibe o conteúdo com um cabeçalho. Ele herda a propriedade de conteúdo, <xref:System.Windows.Controls.ContentControl.Content%2A>, de <xref:System.Windows.Controls.ContentControl> e define o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> propriedade que é do tipo <xref:System.Object>; portanto, pode ser um objeto arbitrário.  
  
 Os seguintes controles herdam <xref:System.Windows.Controls.HeaderedContentControl> e usar o modelo de conteúdo:  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 A ilustração a seguir mostra duas <xref:System.Windows.Controls.TabItem> objetos. A primeira <xref:System.Windows.Controls.TabItem> tem <xref:System.Windows.UIElement> objetos como o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e <xref:System.Windows.Controls.ContentControl.Content%2A>. O <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> é definido como um <xref:System.Windows.Controls.StackPanel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>. O <xref:System.Windows.Controls.ContentControl.Content%2A> é definido como um <xref:System.Windows.Controls.StackPanel> que contém um <xref:System.Windows.Controls.TextBlock> e um <xref:System.Windows.Controls.Label>. A segunda <xref:System.Windows.Controls.TabItem> tem uma cadeia de caracteres no <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e um <xref:System.Windows.Controls.TextBlock> no <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")  
TabControl que usa diferentes tipos de propriedade de cabeçalho  
  
 Para obter um exemplo de como criar <xref:System.Windows.Controls.TabItem> objetos, consulte <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Controles que contêm uma coleção de objetos arbitrários  
 O <xref:System.Windows.Controls.ItemsControl> classe herda de <xref:System.Windows.Controls.Control> e pode conter vários itens, como cadeias de caracteres, objetos ou outros elementos. Suas propriedades de conteúdo são <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> e <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> normalmente é usado para popular o <xref:System.Windows.Controls.ItemsControl> com um conjunto de dados. Se você não deseja usar uma coleção para preencher o <xref:System.Windows.Controls.ItemsControl>, você pode adicionar itens usando o <xref:System.Windows.Controls.ItemsControl.Items%2A> propriedade.  
  
 Os seguintes controles herdam <xref:System.Windows.Controls.ItemsControl> e usar o modelo de conteúdo:  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 A ilustração a seguir mostra um <xref:System.Windows.Controls.ListBox> que contém esses tipos de itens:  
  
-   Uma cadeia de caracteres.  
  
-   Um objeto <xref:System.DateTime>.  
  
-   Um <xref:System.Windows.UIElement>.  
  
-   Um <xref:System.Windows.Controls.Panel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>.  
  
 ![Caixa de listagem com quatro tipos de conteúdo](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")  
ListBox que contém vários tipos de objetos  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Controles que contêm uma coleção de objetos arbitrários e um cabeçalho  
 O <xref:System.Windows.Controls.HeaderedItemsControl> classe herda de <xref:System.Windows.Controls.ItemsControl> e pode conter vários itens, como cadeias de caracteres, objetos, ou outros elementos e um cabeçalho. Ele herda o <xref:System.Windows.Controls.ItemsControl> conteúdo propriedades, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, e <xref:System.Windows.Controls.ItemsControl.Items%2A>, e define o <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedade que pode ser um objeto arbitrário.  
  
 Os seguintes controles herdam <xref:System.Windows.Controls.HeaderedItemsControl> e usar o modelo de conteúdo:  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Classes que contêm uma coleção de objetos de UIElement  
 O <xref:System.Windows.Controls.Panel> classe posiciona e organiza filho <xref:System.Windows.UIElement> objetos. A propriedade de conteúdo é <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 As seguintes classes herdam o <xref:System.Windows.Controls.Panel> classe e usar o modelo de conteúdo:  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Para obter mais informações, consulte [Visão geral dos painéis](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Classes que afetam a aparência de um UIElement  
 O <xref:System.Windows.Controls.Decorator> classe se aplica efeitos visuais e ao redor de um único filho <xref:System.Windows.UIElement>. A propriedade de conteúdo é <xref:System.Windows.Controls.Decorator.Child%2A>. As seguintes classes herdam <xref:System.Windows.Controls.Decorator> e usar o modelo de conteúdo:  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 A ilustração a seguir mostra um <xref:System.Windows.Controls.TextBox> que tem (é decorado com) um <xref:System.Windows.Controls.Border> ao redor dele.  
  
 ![Caixa de texto com borda preta](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock que tem uma borda  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Classes que fornecem comentários visuais sobre um UIElement  
 O <xref:System.Windows.Documents.Adorner> classe fornece indicações visuais para um usuário. Por exemplo, use um <xref:System.Windows.Documents.Adorner> para adicionar ganchos funcionais a elementos ou fornecer informações de estado sobre um controle. O <xref:System.Windows.Documents.Adorner> classe fornece uma estrutura para que você pode criar seus próprios adorners. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não fornece adornos implementados. Para mais informações, consulte [Visão geral dos adornos](../../../../docs/framework/wpf/controls/adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Classes que habilitam os usuários a inserir texto  
 O WPF fornece três principais controles que habilitam os usuários a inserir texto. Cada controle exibe o texto de forma diferente. A tabela a seguir lista esses três controles relacionados ao texto, seus recursos quando eles exibem texto e suas propriedades que contêm o texto do controle.  
  
|Controle|O texto é exibido como|Propriedade de conteúdo|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Texto sem formatação|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Texto formatado|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Texto oculto (os caracteres são mascarados)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Classes que exibem seu texto  
 Várias classes podem ser usadas para exibir texto simples ou formatado. Você pode usar <xref:System.Windows.Controls.TextBlock> para exibir pequenas quantidades de texto. Se você quiser exibir grandes quantidades de texto, use o <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ou <xref:System.Windows.Controls.FlowDocumentScrollViewer> controles.  
  
 O <xref:System.Windows.Controls.TextBlock> tem duas propriedades de conteúdo: <xref:System.Windows.Controls.TextBlock.Text%2A> e <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Quando você deseja exibir o texto que usa a formatação consistente, o <xref:System.Windows.Controls.TextBlock.Text%2A> propriedade geralmente é a melhor opção. Se você planeja usar uma formatação diferente em todo o texto, use o <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriedade. O <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriedade é uma coleção de <xref:System.Windows.Documents.Inline> objetos, que especifica como formatar texto.  
  
 A tabela a seguir lista a propriedade de conteúdo para <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, e <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.  
  
|Controle|Propriedade de conteúdo|Tipo de propriedade de conteúdo|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Documento|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Documento|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Documento|<xref:System.Windows.Documents.FlowDocument>|  
  
 O <xref:System.Windows.Documents.FlowDocument> implementa o <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; portanto, todas as três classes podem levar um <xref:System.Windows.Documents.FlowDocument> como conteúdo.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Classes que formatam seu texto  
 <xref:System.Windows.Documents.TextElement> e suas classes relacionadas permitem que você formate o texto. <xref:System.Windows.Documents.TextElement> objetos contêm e formatar o texto em <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument> objetos. Os dois tipos principais de <xref:System.Windows.Documents.TextElement> são objetos <xref:System.Windows.Documents.Block> elementos e <xref:System.Windows.Documents.Inline> elementos. Um <xref:System.Windows.Documents.Block> elemento representa um bloco de texto, como uma lista ou um parágrafo. Um <xref:System.Windows.Documents.Inline> elemento representa uma parte do texto em um bloco. Muitos <xref:System.Windows.Documents.Inline> classes especificam a formatação de texto ao qual elas são aplicadas. Cada <xref:System.Windows.Documents.TextElement> tem seu próprio modelo de conteúdo. Para obter mais informações, consulte [Visão geral do modelo de conteúdo TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Avançado](../../../../docs/framework/wpf/advanced/index.md)
