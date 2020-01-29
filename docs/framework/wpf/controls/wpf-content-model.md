---
title: Modelo de conteúdo
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
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738275"
---
# <a name="wpf-content-model"></a>Modelo de conteúdo do WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é uma plataforma de apresentação que fornece muitos controles e tipos de controle cujo objetivo principal é exibir diferentes tipos de conteúdo. Para determinar qual controle usar ou de qual controle derivar, você deve compreender os tipos de objetos que um controle específico pode exibir.  
  
 Este tópico resume o modelo de conteúdo para os controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e o tipos semelhantes a controle. O modelo de conteúdo descreve qual conteúdo pode ser usado em um controle. Este tópico também lista as propriedades de conteúdo para cada modelo de conteúdo. Uma propriedade de conteúdo é uma propriedade que é usada para armazenar o conteúdo do objeto.  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Classes que Contêm Conteúdo Arbitrário  
 Alguns controles podem conter um objeto de qualquer tipo, como uma cadeia de caracteres, um objeto <xref:System.DateTime> ou um <xref:System.Windows.UIElement> que seja um contêiner para itens adicionais. Por exemplo, um <xref:System.Windows.Controls.Button> pode conter uma imagem e algum texto; ou um <xref:System.Windows.Controls.CheckBox> pode conter o valor de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem quatro classes que podem conter conteúdo arbitrário. A tabela a seguir lista as classes, que herdam de <xref:System.Windows.Controls.Control>.  
  
|Classes que contêm conteúdo arbitrário|Conteúdo|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Um único objeto arbitrário.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Um cabeçalho e um único item, que são objetos arbitrários.|  
|<xref:System.Windows.Controls.ItemsControl>|Uma coleção de objetos arbitrários.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Um cabeçalho e uma coleção de itens, que são objetos arbitrários.|  
  
 Os controles que herdam essas classes podem conter o mesmo tipo de conteúdo e tratar o conteúdo da mesma forma. A ilustração a seguir mostra um controle de cada modelo de conteúdo que contém uma imagem e algum texto:  
  
 ![Captura de tela que mostra quatro controles diferentes, um de cada modelo de conteúdo.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Controles que contêm um único objeto arbitrário  
 A classe <xref:System.Windows.Controls.ContentControl> contém uma única parte do conteúdo arbitrário. Sua propriedade de conteúdo é <xref:System.Windows.Controls.ContentControl.Content%2A>. Os seguintes controles herdam de <xref:System.Windows.Controls.ContentControl> e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 A ilustração a seguir mostra quatro botões cujo <xref:System.Windows.Controls.ContentControl.Content%2A> está definido como uma cadeia de caracteres, um objeto <xref:System.DateTime>, um <xref:System.Windows.Shapes.Rectangle>e um <xref:System.Windows.Controls.Panel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>:  
  
 ![Captura de tela que mostra quatro botões com tipos de conteúdo diferentes.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Para obter um exemplo de como definir a propriedade <xref:System.Windows.Controls.ContentControl.Content%2A>, consulte <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Controles que contêm um único objeto arbitrário e um cabeçalho  
 A classe <xref:System.Windows.Controls.HeaderedContentControl> herda de <xref:System.Windows.Controls.ContentControl> e exibe o conteúdo com um cabeçalho. Ele herda a propriedade Content, <xref:System.Windows.Controls.ContentControl.Content%2A>, de <xref:System.Windows.Controls.ContentControl> e define a propriedade <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> que é do tipo <xref:System.Object>; Portanto, ambos podem ser um objeto arbitrário.  
  
 Os seguintes controles herdam de <xref:System.Windows.Controls.HeaderedContentControl> e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 A ilustração a seguir mostra dois objetos <xref:System.Windows.Controls.TabItem>. A primeira <xref:System.Windows.Controls.TabItem> tem <xref:System.Windows.UIElement> objetos que o <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e o <xref:System.Windows.Controls.ContentControl.Content%2A>. O <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> é definido como um <xref:System.Windows.Controls.StackPanel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>. O <xref:System.Windows.Controls.ContentControl.Content%2A> é definido como um <xref:System.Windows.Controls.StackPanel> que contém uma <xref:System.Windows.Controls.TextBlock> e uma <xref:System.Windows.Controls.Label>. A segunda <xref:System.Windows.Controls.TabItem> tem uma cadeia de caracteres na <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e uma <xref:System.Windows.Controls.TextBlock> no <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl que usa tipos diferentes na propriedade Header.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Para obter um exemplo de como criar <xref:System.Windows.Controls.TabItem> objetos, consulte <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Controles que contêm uma coleção de objetos arbitrários  
 A classe <xref:System.Windows.Controls.ItemsControl> herda de <xref:System.Windows.Controls.Control> e pode conter vários itens, como cadeias de caracteres, objetos ou outros elementos. Suas propriedades de conteúdo são <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> e <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> normalmente é usado para preencher o <xref:System.Windows.Controls.ItemsControl> com uma coleção de dados. Se você não quiser usar uma coleção para popular a <xref:System.Windows.Controls.ItemsControl>, poderá adicionar itens usando a propriedade <xref:System.Windows.Controls.ItemsControl.Items%2A>.  
  
 Os seguintes controles herdam de <xref:System.Windows.Controls.ItemsControl> e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 A ilustração a seguir mostra um <xref:System.Windows.Controls.ListBox> que contém estes tipos de itens:  
  
- Uma cadeia de caracteres.  
  
- Um objeto <xref:System.DateTime>.  
  
- Um <xref:System.Windows.UIElement>.  
  
- Um <xref:System.Windows.Controls.Panel> que contém um <xref:System.Windows.Shapes.Ellipse> e um <xref:System.Windows.Controls.TextBlock>.  
  
 ![Captura de tela que mostra uma caixa de listagem com quatro tipos de conteúdo.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Controles que contêm uma coleção de objetos arbitrários e um cabeçalho  
 A classe <xref:System.Windows.Controls.HeaderedItemsControl> herda de <xref:System.Windows.Controls.ItemsControl> e pode conter vários itens, como cadeias de caracteres, objetos ou outros elementos, e um cabeçalho. Ele herda as propriedades de conteúdo <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>e <xref:System.Windows.Controls.ItemsControl.Items%2A>, e define a propriedade <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> que pode ser um objeto arbitrário.  
  
 Os seguintes controles herdam de <xref:System.Windows.Controls.HeaderedItemsControl> e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Classes que contêm uma coleção de objetos de UIElement  
 A classe <xref:System.Windows.Controls.Panel> posiciona e organiza objetos <xref:System.Windows.UIElement> filhos. Sua propriedade de conteúdo é <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 As classes a seguir herdam da classe <xref:System.Windows.Controls.Panel> e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 Para obter mais informações, consulte [Visão geral dos painéis](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Classes que afetam a aparência de um UIElement  
 A classe <xref:System.Windows.Controls.Decorator> aplica efeitos visuais em ou em um único <xref:System.Windows.UIElement>filho. Sua propriedade de conteúdo é <xref:System.Windows.Controls.Decorator.Child%2A>. As classes a seguir herdam de <xref:System.Windows.Controls.Decorator> e usam seu modelo de conteúdo:  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 A ilustração a seguir mostra um <xref:System.Windows.Controls.TextBox> que tem (decorado com) um <xref:System.Windows.Controls.Border> em volta dele.  
  
 ![TextBox com borda preta](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock que tem uma borda  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Classes que fornecem comentários visuais sobre um UIElement  
 A classe <xref:System.Windows.Documents.Adorner> fornece indicações visuais para um usuário. Por exemplo, use um <xref:System.Windows.Documents.Adorner> para adicionar identificadores funcionais a elementos ou fornecer informações de estado sobre um controle. A classe <xref:System.Windows.Documents.Adorner> fornece uma estrutura para que você possa criar seus próprios adornos. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não fornece adornos implementados. Para mais informações, consulte [Visão geral dos adornos](adorners-overview.md).  
  
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
 Várias classes podem ser usadas para exibir texto simples ou formatado. Você pode usar <xref:System.Windows.Controls.TextBlock> para exibir pequenas quantidades de texto. Se você quiser exibir grandes quantidades de texto, use os controles <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 O <xref:System.Windows.Controls.TextBlock> tem duas propriedades de conteúdo: <xref:System.Windows.Controls.TextBlock.Text%2A> e <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Quando você deseja exibir o texto que usa formatação consistente, a propriedade <xref:System.Windows.Controls.TextBlock.Text%2A> geralmente é a melhor opção. Se você planeja usar formatação diferente em todo o texto, use a propriedade <xref:System.Windows.Controls.TextBlock.Inlines%2A>. A propriedade <xref:System.Windows.Controls.TextBlock.Inlines%2A> é uma coleção de objetos <xref:System.Windows.Documents.Inline>, que especificam como formatar o texto.  
  
 A tabela a seguir lista a propriedade de conteúdo para as classes <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>e <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
|Controle|Propriedade de conteúdo|Tipo de propriedade de conteúdo|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Documento|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Documento|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Documento|<xref:System.Windows.Documents.FlowDocument>|  
  
 O <xref:System.Windows.Documents.FlowDocument> implementa a interface <xref:System.Windows.Documents.IDocumentPaginatorSource>; Portanto, todas as três classes podem pegar um <xref:System.Windows.Documents.FlowDocument> como conteúdo.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Classes que formatam seu texto  
 <xref:System.Windows.Documents.TextElement> e suas classes relacionadas permitem que você formate o texto. <xref:System.Windows.Documents.TextElement> objetos contêm e formatam texto em objetos <xref:System.Windows.Controls.TextBlock> e <xref:System.Windows.Documents.FlowDocument>. Os dois tipos principais de objetos <xref:System.Windows.Documents.TextElement> são elementos de <xref:System.Windows.Documents.Block> e elementos de <xref:System.Windows.Documents.Inline>. Um elemento <xref:System.Windows.Documents.Block> representa um bloco de texto, como um parágrafo ou uma lista. Um elemento <xref:System.Windows.Documents.Inline> representa uma parte do texto em um bloco. Muitas classes de <xref:System.Windows.Documents.Inline> especificam a formatação para o texto ao qual elas são aplicadas. Cada <xref:System.Windows.Documents.TextElement> tem seu próprio modelo de conteúdo. Para obter mais informações, consulte [Visão geral do modelo de conteúdo TextElement](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Veja também

- [Avançado](../advanced/index.md)
