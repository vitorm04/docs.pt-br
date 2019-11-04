---
title: Controles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 42596c8adf1b8b27f250fa7a3cf6cc173a63e2eb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459452"
---
# <a name="controls"></a>Controles
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] é fornecido com muitos dos componentes comuns da interface do usuário que são usados em quase todos os aplicativos do Windows, como <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>e <xref:System.Windows.Controls.ListBox>. Historicamente, esses objetos são chamados de controles. Embora o SDK do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] continue a usar o termo "controle" para significar de forma flexível qualquer classe que representa um objeto visível em um aplicativo, é importante observar que uma classe não precisa herdar da classe <xref:System.Windows.Controls.Control> para ter uma presença visível. As classes que herdam da classe <xref:System.Windows.Controls.Control> contêm um <xref:System.Windows.Controls.ControlTemplate>, que permite ao consumidor de um controle alterar radicalmente a aparência do controle sem precisar criar uma nova subclasse.  Este tópico discute como os controles (tanto os que herdam da classe <xref:System.Windows.Controls.Control> e os que não são) são usados normalmente no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Criando uma instância de um controle  
 Você pode adicionar um controle a um aplicativo usando o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou o código.  O exemplo a seguir mostra como criar um aplicativo simples que solicita a um usuário o nome e sobrenome.  Este exemplo cria seis controles: dois rótulos, duas caixas de texto e dois botões, em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Todos os controles podem ser criados da mesma forma.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 O exemplo a seguir cria o mesmo aplicativo no código. Para resumir, a criação do <xref:System.Windows.Controls.Grid>, `grid1`, foi excluída do exemplo. `grid1` tem as mesmas definições de coluna e linha, conforme mostrado no exemplo anterior [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Alterando a aparência de um controle  
 É comum alterar a aparência de um controle para ajustar a aparência do seu aplicativo. Você pode alterar a aparência de um controle seguindo um destes procedimentos, dependendo do que deseja realizar:  
  
- Altere o valor de uma propriedade do controle.  
  
- Crie um <xref:System.Windows.Style> para o controle.  
  
- Crie um novo <xref:System.Windows.Controls.ControlTemplate> para o controle.  
  
### <a name="changing-a-controls-property-value"></a>Alterando o valor da propriedade do controle  
 Muitos controles têm propriedades que permitem alterar a forma como o controle é exibido, como o <xref:System.Windows.Controls.Control.Background%2A> de um <xref:System.Windows.Controls.Button>. Você pode definir as propriedades de valor no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e no código. O exemplo a seguir define as propriedades <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>e <xref:System.Windows.Controls.Control.FontWeight%2A> em um <xref:System.Windows.Controls.Button> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 O exemplo a seguir define as mesmas propriedades no código.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Criando um estilo para um controle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferece a capacidade de especificar a aparência dos controles atacados, em vez de definir propriedades em cada instância no aplicativo, criando um <xref:System.Windows.Style>. O exemplo a seguir cria um <xref:System.Windows.Style> que é aplicado a cada <xref:System.Windows.Controls.Button> no aplicativo. as definições de <xref:System.Windows.Style> geralmente são definidas em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em uma <xref:System.Windows.ResourceDictionary>, como a propriedade <xref:System.Windows.FrameworkElement.Resources%2A> da <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Você também pode aplicar um estilo a apenas determinados controles de um tipo específico atribuindo uma chave ao estilo e especificando essa chave na propriedade `Style` do seu controle.  Para obter mais informações sobre estilos, consulte [estilização e modelagem](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Criando um ControlTemplate  
 Um <xref:System.Windows.Style> permite que você defina propriedades em vários controles por vez, mas às vezes você pode querer personalizar a aparência de um <xref:System.Windows.Controls.Control> além do que você pode fazer criando uma <xref:System.Windows.Style>. As classes que herdam da classe <xref:System.Windows.Controls.Control> têm um <xref:System.Windows.Controls.ControlTemplate>, que define a estrutura e a aparência de uma <xref:System.Windows.Controls.Control>. A propriedade <xref:System.Windows.Controls.Control.Template%2A> de uma <xref:System.Windows.Controls.Control> é pública, para que você possa fornecer uma <xref:System.Windows.Controls.Control> um <xref:System.Windows.Controls.ControlTemplate> diferente do padrão. Geralmente, você pode especificar um novo <xref:System.Windows.Controls.ControlTemplate> para uma <xref:System.Windows.Controls.Control> em vez de herdar de um controle para personalizar a aparência de um <xref:System.Windows.Controls.Control>.  
  
 Considere o controle muito comum, <xref:System.Windows.Controls.Button>.  O comportamento principal de um <xref:System.Windows.Controls.Button> é permitir que um aplicativo execute alguma ação quando o usuário clicar nele.  Por padrão, o <xref:System.Windows.Controls.Button> em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparece como um retângulo elevado.  Ao desenvolver um aplicativo, talvez você queira aproveitar o comportamento de um <xref:System.Windows.Controls.Button>– ou seja, manipulando o evento de clique do botão, mas você pode alterar a aparência do botão além do que você pode fazer alterando as propriedades do botão.  Nesse caso, você pode criar um novo <xref:System.Windows.Controls.ControlTemplate>.  
  
 O exemplo a seguir cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.Button>.  O <xref:System.Windows.Controls.ControlTemplate> cria um <xref:System.Windows.Controls.Button> com cantos arredondados e um plano de fundo de gradiente.  O <xref:System.Windows.Controls.ControlTemplate> contém um <xref:System.Windows.Controls.Border> cujo <xref:System.Windows.Controls.Border.Background%2A> é um <xref:System.Windows.Media.LinearGradientBrush> com dois objetos <xref:System.Windows.Media.GradientStop>.  A primeira <xref:System.Windows.Media.GradientStop> usa a vinculação de dados para associar a propriedade <xref:System.Windows.Media.GradientStop.Color%2A> do <xref:System.Windows.Media.GradientStop> à cor do plano de fundo do botão.  Quando você define a propriedade <xref:System.Windows.Controls.Control.Background%2A> da <xref:System.Windows.Controls.Button>, a cor desse valor será usada como a primeira <xref:System.Windows.Media.GradientStop>. Para obter mais informações sobre vinculação de dados, veja [Noções básicas de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md). O exemplo também cria um <xref:System.Windows.Trigger> que altera a aparência do <xref:System.Windows.Controls.Button> quando <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> é `true`.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> A propriedade <xref:System.Windows.Controls.Control.Background%2A> da <xref:System.Windows.Controls.Button> deve ser definida como um <xref:System.Windows.Media.SolidColorBrush> para que o exemplo funcione corretamente.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Assinando eventos  
 Você pode assinar o evento de um controle usando o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou o código, mas só pode manipular um evento no código.  O exemplo a seguir mostra como assinar o evento de `Click` de um <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 O exemplo a seguir manipula o evento `Click` de um <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Conteúdo avançado em controles  
 A maioria das classes que herdam da classe <xref:System.Windows.Controls.Control> tem a capacidade de conter conteúdo rico. Por exemplo, um <xref:System.Windows.Controls.Label> pode conter qualquer objeto, como uma cadeia de caracteres, uma <xref:System.Windows.Controls.Image>ou uma <xref:System.Windows.Controls.Panel>.  As classes a seguir fornecem suporte para conteúdo avançado e atuam como classes base para a maioria dos controles no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- <xref:System.Windows.Controls.ContentControl>--alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>e <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>--alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>e <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>e <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--alguns exemplos de classes que herdam dessa classe são <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>e <xref:System.Windows.Controls.ToolBar>.  

 Para obter mais informações sobre essas classes base, consulte [modelo de conteúdo do WPF](wpf-content-model.md).  
  
## <a name="see-also"></a>Consulte também

- [Estilo e modelagem](styling-and-templating.md)
- [Controles por categoria](controls-by-category.md)
- [Biblioteca de controles](control-library.md)
- [Visão geral de modelagem dos dados](../data/data-templating-overview.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Entrada](../advanced/input-wpf.md)
- [Habilitar um comando](../advanced/how-to-enable-a-command.md)
- [Instruções passo a passo: criar um botão animado personalizado](walkthroughs-create-a-custom-animated-button.md)
- [Personalização do controle](control-customization.md)
