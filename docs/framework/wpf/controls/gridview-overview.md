---
title: Visão geral de GridView
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 6da556296679de1161f609a7731c6fbf14e94730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966479"
---
# <a name="gridview-overview"></a>Visão geral de GridView
<xref:System.Windows.Controls.GridView>o modo de exibição é um dos modos de exibição <xref:System.Windows.Controls.ListView> para um controle. A <xref:System.Windows.Controls.GridView> classe e suas classes de suporte permitem que você e seus usuários exibam coleções de itens em uma tabela que normalmente usa botões como cabeçalhos de coluna interativos. Este tópico apresenta a <xref:System.Windows.Controls.GridView> classe e descreve seu uso.  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>O que é um modo de exibição GridView?  
 O <xref:System.Windows.Controls.GridView> modo de exibição exibe uma lista de itens de dados associando campos de dados a colunas e exibindo um cabeçalho de coluna para identificar o campo. O estilo <xref:System.Windows.Controls.GridView> padrão implementa botões como cabeçalhos de coluna. Usando botões para cabeçalhos de coluna, você pode implementar recursos importantes de interação do usuário; por exemplo, os usuários podem clicar no cabeçalho da coluna <xref:System.Windows.Controls.GridView> para classificar dados de acordo com o conteúdo de uma coluna específica.  
  
> [!NOTE]
> Os controles de botão <xref:System.Windows.Controls.GridView> que o usa para cabeçalhos de coluna <xref:System.Windows.Controls.Primitives.ButtonBase>são derivados de.  
  
 A ilustração a seguir mostra <xref:System.Windows.Controls.GridView> uma exibição <xref:System.Windows.Controls.ListView> do conteúdo.  
    
 ![Captura de tela que mostra a exibição GridView do conteúdo de ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>as colunas são representadas por <xref:System.Windows.Controls.GridViewColumn> objetos, que podem ser dimensionadas automaticamente para seu conteúdo. Opcionalmente, você pode definir explicitamente um <xref:System.Windows.Controls.GridViewColumn> para uma largura específica. Você pode redimensionar colunas arrastando a alça entre cabeçalhos de coluna. Você também pode adicionar, remover, substituir e reordenar colunas dinamicamente, pois essa funcionalidade é incorporada ao <xref:System.Windows.Controls.GridView>. No entanto, <xref:System.Windows.Controls.GridView> o não pode atualizar diretamente os dados que ele exibe.  
  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.GridView> que exibe dados de funcionários. Neste exemplo, <xref:System.Windows.Controls.ListView> define o `EmployeeInfoDataSource` como o <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. As definições de propriedade <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> de <xref:System.Windows.Controls.GridViewColumn> associar conteúdo `EmployeeInfoDataSource` a categorias de dados.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 A ilustração a seguir mostra a tabela que o exemplo anterior cria. O controle GridView exibe dados de um objeto ItemsSource:
    
 ![Captura de tela que mostra um ListView com saída GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Layout e estilo do GridView  
 As células de coluna e o cabeçalho de coluna <xref:System.Windows.Controls.GridViewColumn> de um têm a mesma largura. Por padrão, cada coluna redimensiona sua largura para caber seu conteúdo. Opcionalmente, você pode definir uma coluna com uma largura fixa.  
  
 Conteúdo de dados relacionado são exibidos em linhas horizontais. Por exemplo, na ilustração anterior, sobrenome, nome e número de identificação de cada funcionário são exibidos como um conjunto porque eles aparecem em uma linha horizontal.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definindo e aplicando estilos sobre colunas em um GridView  
 Ao definir o campo de dados a ser exibido <xref:System.Windows.Controls.GridViewColumn>em um, <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>use <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>as propriedades <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> , ou. A <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriedade tem precedência sobre qualquer uma das propriedades do modelo.  
  
 Para especificar o alinhamento do conteúdo em uma coluna de a <xref:System.Windows.Controls.GridView>, defina um <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. Não use as propriedades <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> e <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> para <xref:System.Windows.Controls.ListView> o conteúdo que é exibido usando um <xref:System.Windows.Controls.GridView>.  
  
 Para especificar propriedades de modelo e estilo para cabeçalhos de coluna, <xref:System.Windows.Controls.GridView>use <xref:System.Windows.Controls.GridViewColumn>as classes <xref:System.Windows.Controls.GridViewColumnHeader> , e. Para obter mais informações, consulte [Visão geral de modelos e estilos de cabeçalho de coluna GridView](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Adicionando elementos visuais a um GridView  
 Para adicionar elementos visuais, <xref:System.Windows.Controls.CheckBox> como e <xref:System.Windows.Controls.Button> controles, a um <xref:System.Windows.Controls.GridView> modo de exibição, use modelos ou estilos.  
  
 Se você definir explicitamente um elemento visual como um item de dados, ele poderá aparecer apenas uma vez em <xref:System.Windows.Controls.GridView>um. Essa limitação existe porque um elemento pode ter apenas um pai e portanto, pode aparecer apenas uma vez na árvore visual.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Aplicando estilo a linhas em um GridView  
 Use as <xref:System.Windows.Controls.GridViewRowPresenter> classes <xref:System.Windows.Controls.GridViewHeaderRowPresenter> e para formatar e exibir as linhas de um <xref:System.Windows.Controls.GridView>. Para obter um exemplo de como estilizar linhas em <xref:System.Windows.Controls.GridView> um modo de exibição, consulte [Estilizar uma linha em um ListView que implementa um GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problemas de alinhamento ao usar ItemContainerStyle  
 Para evitar problemas de alinhamento entre cabeçalhos e células de coluna, não defina uma propriedade ou especifique um modelo que afete a largura de um item <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>em um. Por exemplo, não defina a <xref:System.Windows.FrameworkElement.Margin%2A> propriedade ou especifique um <xref:System.Windows.Controls.ControlTemplate> que adicione um <xref:System.Windows.Controls.CheckBox> a um <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> que esteja definido em um <xref:System.Windows.Controls.ListView> controle. Em vez disso, especifique as propriedades e os modelos que afetam a largura da coluna diretamente <xref:System.Windows.Controls.GridView> em classes que definem um modo de exibição.  
  
 Por exemplo, para adicionar uma <xref:System.Windows.Controls.CheckBox> às linhas no <xref:System.Windows.Controls.GridView> modo de exibição <xref:System.Windows.DataTemplate>, adicione a <xref:System.Windows.Controls.CheckBox> a a e, em seguida, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> defina a propriedade <xref:System.Windows.DataTemplate>para isso.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interações do usuário com um GridView  
 Quando você usa um <xref:System.Windows.Controls.GridView> em seu aplicativo, os usuários podem interagir com e modificar a formatação <xref:System.Windows.Controls.GridView>do. Por exemplo, os usuários podem reordenar colunas, redimensionar uma coluna, selecionar itens em uma tabela e navegar pelo conteúdo. Você também pode definir um manipulador de eventos que responde quando um usuário clica no botão de cabeçalho de coluna. O manipulador de eventos pode executar operações como classificar os dados que são exibidos no <xref:System.Windows.Controls.GridView> de acordo com o conteúdo de uma coluna.  
  
 A lista a seguir aborda mais detalhadamente os recursos de uso <xref:System.Windows.Controls.GridView> para a interação do usuário:  
  
- **Reordene colunas usando o método do tipo "arrastar e soltar".**  
  
     Os usuários podem reordenar colunas <xref:System.Windows.Controls.GridView> em um pressionando o botão esquerdo do mouse enquanto ele estiver sobre um cabeçalho de coluna e, em seguida, arrastando essa coluna para uma nova posição. Enquanto o usuário arrasta o cabeçalho da coluna, uma versão flutuante do cabeçalho é exibida, bem como uma linha preta sólida que mostra onde inserir a coluna.  
  
     Se você quiser modificar o estilo padrão para a versão flutuante de um cabeçalho <xref:System.Windows.Controls.ControlTemplate> , especifique um para um <xref:System.Windows.Controls.GridViewColumnHeader> tipo que é disparado quando <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> a propriedade é definida <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>como. Para mais informações, consulte [Criar um estilo para um cabeçalho de coluna GridView arrastado](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Redimensionar uma coluna para seu conteúdo.**  
  
     Os usuários podem clicar duas vezes na garra à direita do cabeçalho da coluna para redimensionar uma coluna para caber seu conteúdo.  
  
    > [!NOTE]
    > Você pode definir a <xref:System.Windows.Controls.GridViewColumn.Width%2A> Propriedade como `Double.NaN` para produzir o mesmo efeito.  
  
- **Selecionar os itens de linha.**  
  
     Os usuários podem selecionar um ou mais itens em <xref:System.Windows.Controls.GridView>um.  
  
     Se você quiser alterar o <xref:System.Windows.Style> de um item selecionado, consulte [usar gatilhos para estilizar itens selecionados em um ListView](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Barra de rolagem para exibir o conteúdo que não está visível inicialmente na tela.**  
  
     Se o tamanho do <xref:System.Windows.Controls.GridView> não for grande o suficiente para exibir todos os itens, os usuários poderão rolar horizontal ou verticalmente usando barras de rolagem, que são fornecidas por um <xref:System.Windows.Controls.ScrollViewer> controle. Um <xref:System.Windows.Controls.Primitives.ScrollBar> ficará oculto se todo o conteúdo estiver visível em uma direção específica. Cabeçalhos de coluna não rolam com uma barra de rolagem vertical, mas rolam horizontalmente.  
  
- **Interagir com colunas clicando nos botões de cabeçalho de coluna.**  
  
     Quando os usuários clicam um botão de cabeçalho de coluna, eles podem classificar os dados que serão exibidos na coluna se você tiver fornecido um algoritmo de classificação.  
  
     Você pode manipular o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento para botões de cabeçalho de coluna a fim de fornecer funcionalidade como um algoritmo de classificação. Para manipular o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento para um único cabeçalho de coluna, defina um manipulador de eventos <xref:System.Windows.Controls.GridViewColumnHeader>no. Para definir um manipulador de eventos que manipula <xref:System.Windows.Controls.Primitives.ButtonBase.Click> o evento para todos os cabeçalhos de coluna, defina o <xref:System.Windows.Controls.ListView> manipulador no controle.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Obtendo outros modos de exibição personalizados  
 A <xref:System.Windows.Controls.GridView> classe, que é derivada <xref:System.Windows.Controls.ViewBase> da classe abstract, é apenas um dos modos de exibição possíveis para a <xref:System.Windows.Controls.ListView> classe. Você pode criar outros modos de exibição <xref:System.Windows.Controls.ListView> personalizados para derivando <xref:System.Windows.Controls.ViewBase> da classe. Para obter um exemplo de um modo de exibição personalizado, consulte [Criar um modo de exibição personalizado para um ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Classes de apoio a GridView  
 As classes a seguir dão <xref:System.Windows.Controls.GridView> suporte ao modo de exibição.  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [Visão geral de ListView](listview-overview.md)
- [Classificar uma coluna GridView quando um cabeçalho é clicado](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Tópicos de instruções](listview-how-to-topics.md)
