---
title: Visão geral do menu
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 3d5cfba0734e684349f7d73b7242f4b69089b94d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124644"
---
# <a name="menu-overview"></a>Visão geral do menu
A classe <xref:System.Windows.Controls.Menu> permite que você organize elementos associados a comandos e manipuladores de eventos em uma ordem hierárquica. Cada elemento <xref:System.Windows.Controls.Menu> contém uma coleção de elementos <xref:System.Windows.Controls.MenuItem>.  

<a name="menu_control"></a>   
## <a name="menu-control"></a>Controle de Menu  
 O controle <xref:System.Windows.Controls.Menu> apresenta uma lista de itens que especificam comandos ou opções para um aplicativo. Normalmente, clicar em um <xref:System.Windows.Controls.MenuItem> abre um submenu ou faz com que um aplicativo execute um comando.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Criando Menus  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Menu> para manipular texto em um <xref:System.Windows.Controls.TextBox>. O <xref:System.Windows.Controls.Menu> contém <xref:System.Windows.Controls.MenuItem> objetos que usam as propriedades <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>e <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> e os eventos <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>e <xref:System.Windows.Controls.MenuItem.Click>.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>MenuItems com Atalhos de Teclado  
 Atalhos de teclado são combinações de caracteres que podem ser inseridas com o teclado para invocar <xref:System.Windows.Controls.Menu> comandos. Por exemplo, o atalho para **Copiar** é CTRL+C. Há duas propriedades a serem usadas com os atalhos de teclado e os itens de menu —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> ou <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 O exemplo a seguir mostra como usar a propriedade <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> para atribuir texto de atalho de teclado a controles de <xref:System.Windows.Controls.MenuItem>. Isso somente coloca o atalho de teclado no item de menu.  Ele não associa o comando ao <xref:System.Windows.Controls.MenuItem>. O aplicativo deve manipular a entrada do usuário para executar a ação.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>{1&gt;Comando&lt;1}  
 O exemplo a seguir mostra como usar a propriedade <xref:System.Windows.Controls.MenuItem.Command%2A> para associar os comandos **abrir** e **salvar** aos controles <xref:System.Windows.Controls.MenuItem>. Não apenas a propriedade Command associa um comando a um <xref:System.Windows.Controls.MenuItem>, mas também fornece o texto do gesto de entrada a ser usado como um atalho.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 A classe <xref:System.Windows.Controls.MenuItem> também tem uma propriedade <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>, que especifica o elemento no qual o comando ocorre. Se <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> não for definido, o elemento que tem o foco do teclado receberá o comando. Para obter mais informações sobre comandos, consulte [Visão Geral dos Comandos](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Estilo de Menu  
 Com o estilo de controle, você pode alterar drasticamente a aparência e o comportamento dos controles de <xref:System.Windows.Controls.Menu> sem precisar escrever um controle personalizado. Além de definir propriedades visuais, você também pode aplicar um <xref:System.Windows.Style> a partes individuais de um controle, alterar o comportamento de partes do controle por meio de propriedades ou adicionar outras partes ou alterar o layout de um controle. Os exemplos a seguir demonstram várias maneiras de adicionar um <xref:System.Windows.Style> a um controle de <xref:System.Windows.Controls.Menu>.  
  
 O primeiro exemplo de código define um <xref:System.Windows.Style> chamado `Simple` que mostra como usar as configurações atuais do sistema em seu estilo. O código atribui a cor do `MenuHighlightBrush` como cor da tela de fundo do menu e o `MenuTextBrush` como cor de primeiro plano do menu. Observe que as chaves de recurso são utilizadas para atribuir os pincéis.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 O exemplo a seguir usa <xref:System.Windows.Trigger> elementos que permitem alterar a aparência de uma <xref:System.Windows.Controls.MenuItem> em resposta a eventos que ocorrem no <xref:System.Windows.Controls.Menu>. Quando você move o mouse sobre a <xref:System.Windows.Controls.Menu>, a cor do primeiro plano e as características da fonte dos itens de menu são alteradas.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplo da galeria de controles de WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
