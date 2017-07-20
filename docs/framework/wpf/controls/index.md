---
title: Controles | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7652a2e64cdc107546ac3ea51178a3542606bd43
ms.contentlocale: pt-br
ms.lasthandoff: 06/08/2017

---
# <a name="controls"></a>Controles
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é fornecido com diversos componentes comuns de interface do usuário que são usados em quase todos os aplicativos Windows, como              <xref:System.Windows.Controls.Button>,              <xref:System.Windows.Controls.Label>,              <xref:System.Windows.Controls.TextBox>,              <xref:System.Windows.Controls.Menu> e              <xref:System.Windows.Controls.ListBox>. Historicamente, esses objetos são chamados de controles. Enquanto o SDK              [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] continua a usar o termo "controle" para descrever qualquer classe que representa um objeto visível em um aplicativo, é importante observar que uma classe não precisa herdar da classe              <xref:System.Windows.Controls.Control> para ter uma presença visível. As classes que herdam da classe              <xref:System.Windows.Controls.Control> contêm um                            <xref:System.Windows.Controls.ControlTemplate>, que permite que o consumidor de um controle altere radicalmente a aparência do controle sem ter que criar uma nova subclasse.  Este tópico discute como os controles (tanto aqueles que herdam da classe              <xref:System.Windows.Controls.Control> quanto os que não herdam) são normalmente usados em              [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 
  
<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Criando uma instância de um controle  
 Você pode adicionar um controle a um aplicativo usando                  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou o código.  O exemplo a seguir mostra como criar um aplicativo simples que solicita a um usuário o nome e sobrenome.  Este exemplo cria seis controles: dois rótulos, duas caixas de texto e dois botões, em                  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Todos os controles podem ser criados da mesma forma.  
  
 [!code-xml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 O exemplo a seguir cria o mesmo aplicativo no código. Para resumir o processo, a criação de                  <xref:System.Windows.Controls.Grid>,                  `grid1`, foi excluída do exemplo.                   O `grid1` tem as mesmas definições de linha e coluna, conforme mostrado no exemplo                  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] anterior.  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)] [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Alterando a aparência de um controle  
 É comum alterar a aparência de um controle para ajustar a aparência do seu aplicativo. Você pode alterar a aparência de um controle seguindo um destes procedimentos, dependendo do que deseja realizar:  
  
-   Altere o valor de uma propriedade do controle.  
  
-   Crie um                          <xref:System.Windows.Style> para o controle.  
  
-   Crie um novo                          <xref:System.Windows.Controls.ControlTemplate> para o controle.  
  
### <a name="changing-a-controls-property-value"></a>Alterando o valor da propriedade do controle  
 Muitos controles têm propriedades que permitem que você altere como o controle é exibido, como o                          <xref:System.Windows.Controls.Control.Background%2A> de um                          <xref:System.Windows.Controls.Button>. Você pode definir as propriedades de valor em                           [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e no código. O exemplo a seguir define as propriedades                          <xref:System.Windows.Controls.Control.Background%2A>,                          <xref:System.Windows.Controls.Control.FontSize%2A> e                          <xref:System.Windows.Controls.Control.FontWeight%2A> em um                          <xref:System.Windows.Controls.Button> no                          [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 O exemplo a seguir define as mesmas propriedades no código.  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)] [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Criando um estilo para um controle  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permite que você especifique a aparência dos controles globalmente, em vez de definir propriedades em cada instância do aplicativo, criando um                          <xref:System.Windows.Style>.                           O exemplo a seguir                          cria um                          <xref:System.Windows.Style> que é aplicado a cada                          <xref:System.Windows.Controls.Button> no aplicativo.                          As definições do <xref:System.Windows.Style> são geralmente definidas no                          [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em um                          <xref:System.Windows.ResourceDictionary>, como a propriedade                          <xref:System.Windows.FrameworkElement.Resources%2A> do                          <xref:System.Windows.FrameworkElement>.  
  
 [!code-xml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Você também pode aplicar um estilo somente a determinados controles de um tipo específico ao atribuir uma chave ao estilo e especificar essa chave na propriedade                          `Style` de seu controle.  Para mais informações sobre estilos, consulte                           [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Criando um ControlTemplate  
 Um                          <xref:System.Windows.Style> permite que você defina propriedades em vários controles de uma vez, mas talvez você deseje personalizar a aparência de um                          <xref:System.Windows.Controls.Control> além do que você pode fazer ao criar um                          <xref:System.Windows.Style>. Classes que herdaram da classe                          <xref:System.Windows.Controls.Control> têm um                          <xref:System.Windows.Controls.ControlTemplate>, que define a estrutura e a aparência de um                          <xref:System.Windows.Controls.Control>. A propriedade                          <xref:System.Windows.Controls.Control.Template%2A> de um                          <xref:System.Windows.Controls.Control> é pública, portanto você pode atribuir a um                          <xref:System.Windows.Controls.Control> um                          <xref:System.Windows.Controls.ControlTemplate> diferente do padrão. Você pode especificar com frequência um novo                          <xref:System.Windows.Controls.ControlTemplate> para um                          <xref:System.Windows.Controls.Control> em vez de herdar de um controle para personalizar a aparência de um                          <xref:System.Windows.Controls.Control>.  
  
 Considere o controle muito comum,                          <xref:System.Windows.Controls.Button>.  O comportamento primário de um                          <xref:System.Windows.Controls.Button> permite que um aplicativo execute alguma ação quando o usuário clica nele.  Por padrão, o                          <xref:System.Windows.Controls.Button> no                          [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparece como um retângulo elevado.  Ao desenvolver um aplicativo, talvez você queira aproveitar o comportamento de um                          <xref:System.Windows.Controls.Button> – por exemplo, manipulando o evento de clique do botão – mas você pode alterar muito mais a aparência do botão alterando as propriedades do botão.  Nesse caso, você pode criar um novo                          <xref:System.Windows.Controls.ControlTemplate>.  
  
 O exemplo a seguir cria um                          <xref:System.Windows.Controls.ControlTemplate> para um                          <xref:System.Windows.Controls.Button>.  O                          <xref:System.Windows.Controls.ControlTemplate> cria um                          <xref:System.Windows.Controls.Button> com cantos arredondados e um plano de fundo gradiente.  O                          <xref:System.Windows.Controls.ControlTemplate> contém um                          <xref:System.Windows.Controls.Border> cujo                          <xref:System.Windows.Controls.Border.Background%2A> é um                          <xref:System.Windows.Media.LinearGradientBrush> com dois objetos                          <xref:System.Windows.Media.GradientStop>.  O primeiro                          <xref:System.Windows.Media.GradientStop> usa a associação de dados para associar a propriedade                          <xref:System.Windows.Media.GradientStop.Color%2A> do                          <xref:System.Windows.Media.GradientStop> à cor do plano de fundo do botão.  Quando você define a propriedade                          <xref:System.Windows.Controls.Control.Background%2A> do                          <xref:System.Windows.Controls.Button>, a cor desse valor é usada como o primeiro                          <xref:System.Windows.Media.GradientStop>. Para obter mais informações sobre vinculação de dados, consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md). O exemplo também cria um                          <xref:System.Windows.Trigger> que altera a aparência do                          <xref:System.Windows.Controls.Button> quando o                          <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> é                          `true`.  
  
 [!code-xml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  A propriedade                              <xref:System.Windows.Controls.Control.Background%2A> do                              <xref:System.Windows.Controls.Button> deve ser definida como um                              <xref:System.Windows.Media.SolidColorBrush> para que o exemplo funcione corretamente.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Assinando eventos  
 Você pode assinar um evento de controle usando                  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou o código, mas é possível manipular apenas um evento no código.  O exemplo a seguir mostra como assinar o evento                  `Click` de um                  <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)] [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 O exemplo a seguir identifica o evento                  `Click` de um                  <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)] [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Conteúdo avançado em controles  
 A maioria das classes que herdam da classe                  <xref:System.Windows.Controls.Control> podem ter conteúdo avançado. Por exemplo, um                  <xref:System.Windows.Controls.Label> pode conter qualquer objeto, como uma cadeia de caracteres, uma                  <xref:System.Windows.Controls.Image> ou um                  <xref:System.Windows.Controls.Panel>.  As classes a seguir dão suporte a conteúdo avançado e atuam como classes base para a maioria dos controles em                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Controls.ContentControl>-- Alguns exemplos de classes que herdaram dessa classe são                          <xref:System.Windows.Controls.Label>,                          <xref:System.Windows.Controls.Button> e                          <xref:System.Windows.Controls.ToolTip>.  
  
-   <xref:System.Windows.Controls.ItemsControl>-- Alguns exemplos de classes que herdaram dessa classe são                          <xref:System.Windows.Controls.ListBox>,                          <xref:System.Windows.Controls.Menu> e                          <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>-- Alguns exemplos de classes que herdaram dessa classe são                          <xref:System.Windows.Controls.TabItem>,                          <xref:System.Windows.Controls.GroupBox> e                          <xref:System.Windows.Controls.Expander>.  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>--Alguns exemplos de classes que herdaram dessa classe são                          <xref:System.Windows.Controls.MenuItem>,                          <xref:System.Windows.Controls.TreeViewItem> e                          <xref:System.Windows.Controls.ToolBar>.  
  
-  
  
 Para mais informações sobre essas classes base, consulte                  [Modelo de conteúdo do WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Controles por categoria](../../../../docs/framework/wpf/controls/controls-by-category.md)   
 [Biblioteca de controles](../../../../docs/framework/wpf/controls/control-library.md)   
 [Visão geral de modelagem dos dados](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [Visão geral da associação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Entrada](../../../../docs/framework/wpf/advanced/input-wpf.md)   
 [Habilitar um comando](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)   
 [Instruções passo a passo: criar um botão animado personalizado](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)   
 [Personalização do controle](../../../../docs/framework/wpf/controls/control-customization.md)
