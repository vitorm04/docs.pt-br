---
title: Visão geral de GridView
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 98bc7985172cabeab19469af4b4c21e13a6bce73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181894"
---
# <a name="gridview-overview"></a>Visão geral de GridView
<xref:System.Windows.Controls.GridView>modo de exibição é um <xref:System.Windows.Controls.ListView> dos modos de exibição para um controle. A <xref:System.Windows.Controls.GridView> classe e suas classes de suporte permitem que você e seus usuários visualizem coleções de itens em uma tabela que normalmente usa botões como cabeçalhos de coluna interativos. Este tópico introduz <xref:System.Windows.Controls.GridView> a classe e descreve seu uso.  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>O que é um modo de exibição GridView?  
 O <xref:System.Windows.Controls.GridView> modo de exibição exibe uma lista de itens de dados vinculando campos de dados a colunas e exibindo um cabeçalho de coluna para identificar o campo. O <xref:System.Windows.Controls.GridView> estilo padrão implementa botões como cabeçalhos de coluna. Ao usar botões para cabeçalhos de coluna, você pode implementar recursos importantes de interação do usuário; por exemplo, os usuários podem <xref:System.Windows.Controls.GridView> clicar no cabeçalho da coluna para classificar dados de acordo com o conteúdo de uma coluna específica.  
  
> [!NOTE]
> Os controles de <xref:System.Windows.Controls.GridView> botão que são usos <xref:System.Windows.Controls.Primitives.ButtonBase>para cabeçalhos de coluna são derivados de .  
  
 A ilustração <xref:System.Windows.Controls.GridView> a <xref:System.Windows.Controls.ListView> seguir mostra uma visão do conteúdo.  

 ![Captura de tela que mostra a exibição de GridView do conteúdo ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>as colunas <xref:System.Windows.Controls.GridViewColumn> são representadas por objetos, que podem dimensionar automaticamente seu conteúdo. Opcionalmente, você pode definir <xref:System.Windows.Controls.GridViewColumn> explicitamente um para uma largura específica. Você pode redimensionar colunas arrastando a alça entre cabeçalhos de coluna. Você também pode adicionar, remover, substituir e reordenar colunas dinamicamente porque essa funcionalidade está incorporada <xref:System.Windows.Controls.GridView>em . No <xref:System.Windows.Controls.GridView> entanto, não é possível atualizar diretamente os dados que ele exibe.  
  
 O exemplo a seguir <xref:System.Windows.Controls.GridView> mostra como definir um que exibe os dados dos funcionários. Neste exemplo, <xref:System.Windows.Controls.ListView> define `EmployeeInfoDataSource` como <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>o . As definições <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> de <xref:System.Windows.Controls.GridViewColumn> propriedade `EmployeeInfoDataSource` de vincular conteúdo a categorias de dados.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 A ilustração a seguir mostra a tabela que o exemplo anterior cria. O controle GridView exibe dados de um objeto ItemsSource:

 ![Captura de tela que mostra uma listView com saída GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>Layout e estilo do GridView  
 As células da coluna e <xref:System.Windows.Controls.GridViewColumn> o cabeçalho da coluna de a têm a mesma largura. Por padrão, cada coluna redimensiona sua largura para caber seu conteúdo. Opcionalmente, você pode definir uma coluna com uma largura fixa.  
  
 Conteúdo de dados relacionado são exibidos em linhas horizontais. Por exemplo, na ilustração anterior, sobrenome, nome e número de identificação de cada funcionário são exibidos como um conjunto porque eles aparecem em uma linha horizontal.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definindo e aplicando estilos sobre colunas em um GridView  
 Ao definir o campo de <xref:System.Windows.Controls.GridViewColumn>dados <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>a <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>ser <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> exibido em um , use as propriedades ou propriedades. A <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriedade tem precedência sobre qualquer uma das propriedades do modelo.  
  
 Para especificar o alinhamento do <xref:System.Windows.Controls.GridView>conteúdo em <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>uma coluna de a, defina um . Não use <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> as <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> propriedades <xref:System.Windows.Controls.ListView> e propriedades para o <xref:System.Windows.Controls.GridView>conteúdo exibido usando um .  
  
 Para especificar propriedades de modelo e <xref:System.Windows.Controls.GridView>estilo <xref:System.Windows.Controls.GridViewColumn>para <xref:System.Windows.Controls.GridViewColumnHeader> cabeçalhos de coluna, use as classes e classes . Para obter mais informações, consulte [Visão geral de modelos e estilos de cabeçalho de coluna GridView](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>Adicionando elementos visuais a um GridView  
 Para adicionar elementos <xref:System.Windows.Controls.CheckBox> visuais, como <xref:System.Windows.Controls.Button> e <xref:System.Windows.Controls.GridView> controles, a um modo de exibição, use modelos ou estilos.  
  
 Se você definir explicitamente um elemento visual como um item de <xref:System.Windows.Controls.GridView>dados, ele pode aparecer apenas uma vez em um . Essa limitação existe porque um elemento pode ter apenas um pai e portanto, pode aparecer apenas uma vez na árvore visual.  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>Aplicando estilo a linhas em um GridView  
 Use <xref:System.Windows.Controls.GridViewRowPresenter> as <xref:System.Windows.Controls.GridViewHeaderRowPresenter> classes e para formatar <xref:System.Windows.Controls.GridView>e exibir as linhas de a . Para obter um exemplo de como <xref:System.Windows.Controls.GridView> estilizar linhas em um modo de exibição, consulte [Style a Row em uma ListView Que implementa uma GradeView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problemas de alinhamento ao usar ItemContainerStyle  
 Para evitar problemas de alinhamento entre cabeçalhos de coluna e células, não defina <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>uma propriedade ou especifique um modelo que afete a largura de um item em um . Por exemplo, não <xref:System.Windows.FrameworkElement.Margin%2A> defina a <xref:System.Windows.Controls.ControlTemplate> propriedade <xref:System.Windows.Controls.CheckBox> ou <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> especifique <xref:System.Windows.Controls.ListView> um que adicione um a um que é definido em um controle. Em vez disso, especifique as propriedades e <xref:System.Windows.Controls.GridView> modelos que afetam a largura da coluna diretamente nas classes que definem um modo de exibição.  
  
 Por exemplo, para <xref:System.Windows.Controls.CheckBox> adicionar a <xref:System.Windows.Controls.GridView> às linhas no <xref:System.Windows.Controls.CheckBox> modo <xref:System.Windows.DataTemplate>de exibição, adicione a a a e, em seguida, defina a <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> propriedade para isso <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>Interações do usuário com um GridView  
 Quando você <xref:System.Windows.Controls.GridView> usa um em seu aplicativo, os usuários <xref:System.Windows.Controls.GridView>podem interagir e modificar a formatação do . Por exemplo, os usuários podem reordenar colunas, redimensionar uma coluna, selecionar itens em uma tabela e navegar pelo conteúdo. Você também pode definir um manipulador de eventos que responde quando um usuário clica no botão de cabeçalho de coluna. O manipulador de eventos pode realizar operações como <xref:System.Windows.Controls.GridView> classificar os dados exibidos no conteúdo de uma coluna.  
  
 A lista a seguir discute com mais <xref:System.Windows.Controls.GridView> detalhes os recursos de uso para interação do usuário:  
  
- **Reordene colunas usando o método do tipo "arrastar e soltar".**  
  
     Os usuários podem reordenar <xref:System.Windows.Controls.GridView> colunas em um pressionando o botão esquerdo do mouse enquanto ele está sobre um cabeçalho de coluna e, em seguida, arrastando essa coluna para uma nova posição. Enquanto o usuário arrasta o cabeçalho da coluna, uma versão flutuante do cabeçalho é exibida, bem como uma linha preta sólida que mostra onde inserir a coluna.  
  
     Se você quiser modificar o estilo padrão para a <xref:System.Windows.Controls.ControlTemplate> versão <xref:System.Windows.Controls.GridViewColumnHeader> flutuante de um cabeçalho, especifique um para um tipo que é acionado quando a <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> propriedade é definida para <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Para mais informações, consulte [Criar um estilo para um cabeçalho de coluna GridView arrastado](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Redimensionar uma coluna para seu conteúdo.**  
  
     Os usuários podem clicar duas vezes na garra à direita do cabeçalho da coluna para redimensionar uma coluna para caber seu conteúdo.  
  
    > [!NOTE]
    > Você pode <xref:System.Windows.Controls.GridViewColumn.Width%2A> definir `Double.NaN` a propriedade para produzir o mesmo efeito.  
  
- **Selecionar os itens de linha.**  
  
     Os usuários podem selecionar um ou <xref:System.Windows.Controls.GridView>mais itens em um .  
  
     Se você quiser <xref:System.Windows.Style> alterar o de um item selecionado, consulte [Usar gatilhos para estilo itens selecionados em uma listaExibir](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Barra de rolagem para exibir o conteúdo que não está visível inicialmente na tela.**  
  
     Se o tamanho <xref:System.Windows.Controls.GridView> do não for grande o suficiente para exibir todos os itens, os usuários podem rolar <xref:System.Windows.Controls.ScrollViewer> horizontal ou verticalmente usando barras de rolagem, que são fornecidas por um controle. A <xref:System.Windows.Controls.Primitives.ScrollBar> é oculto se todo o conteúdo for visível em uma direção específica. Cabeçalhos de coluna não rolam com uma barra de rolagem vertical, mas rolam horizontalmente.  
  
- **Interagir com colunas clicando nos botões de cabeçalho de coluna.**  
  
     Quando os usuários clicam um botão de cabeçalho de coluna, eles podem classificar os dados que serão exibidos na coluna se você tiver fornecido um algoritmo de classificação.  
  
     Você pode <xref:System.Windows.Controls.Primitives.ButtonBase.Click> lidar com o evento para botões de cabeçalho de coluna, a fim de fornecer funcionalidade como um algoritmo de classificação. Para lidar <xref:System.Windows.Controls.Primitives.ButtonBase.Click> com o evento para um único <xref:System.Windows.Controls.GridViewColumnHeader>cabeçalho de coluna, defina um manipulador de eventos no . Para definir um manipulador de <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos que lida com o evento <xref:System.Windows.Controls.ListView> para todos os cabeçalhos da coluna, defina o manipulador no controle.  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>Obtendo outros modos de exibição personalizados  
 A <xref:System.Windows.Controls.GridView> classe, que é <xref:System.Windows.Controls.ViewBase> derivada da classe abstrata, é apenas <xref:System.Windows.Controls.ListView> um dos modos de exibição possíveis para a classe. Você pode criar outras visualizações personalizadas para <xref:System.Windows.Controls.ListView> derivar da <xref:System.Windows.Controls.ViewBase> classe. Para obter um exemplo de um modo de exibição personalizado, consulte [Criar um modo de exibição personalizado para um ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>Classes de apoio a GridView  
 As classes a <xref:System.Windows.Controls.GridView> seguir suportam o modo de exibição.  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [Visão geral de ListView](listview-overview.md)
- [Classificar uma coluna GridView quando um cabeçalho é clicado](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Tópicos de como fazer](listview-how-to-topics.md)
