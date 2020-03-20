---
title: Visão geral do menu
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 53bc8f10e61b6e4e9e1f3b9a484340d9e2ec2a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186967"
---
# <a name="menu-overview"></a>Visão geral do menu
A <xref:System.Windows.Controls.Menu> classe permite que você organize elementos associados a comandos e manipuladores de eventos em uma ordem hierárquica. Cada <xref:System.Windows.Controls.Menu> elemento contém <xref:System.Windows.Controls.MenuItem> uma coleção de elementos.  

<a name="menu_control"></a>
## <a name="menu-control"></a>Controle de Menu  
 O <xref:System.Windows.Controls.Menu> controle apresenta uma lista de itens que especificam comandos ou opções para um aplicativo. Normalmente, clicar <xref:System.Windows.Controls.MenuItem> em um abre um submenu ou faz com que um aplicativo realize um comando.  
  
<a name="creating_menus"></a>
## <a name="creating-menus"></a>Criando Menus  
 O exemplo a <xref:System.Windows.Controls.Menu> seguir cria <xref:System.Windows.Controls.TextBox>um para manipular texto em um . O <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.MenuItem> contém objetos <xref:System.Windows.Controls.MenuItem.Command%2A> <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>que <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> usam as <xref:System.Windows.Controls.MenuItem.Checked> <xref:System.Windows.Controls.MenuItem.Unchecked>propriedades <xref:System.Windows.Controls.MenuItem.Click> e eventos.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>
## <a name="menuitems-with-keyboard-shortcuts"></a>MenuItems com Atalhos de Teclado  
 Atalhos de teclado são combinações de caracteres <xref:System.Windows.Controls.Menu> que podem ser inseridas com o teclado para invocar comandos. Por exemplo, o atalho para **Copiar** é CTRL+C. Há duas propriedades para usar com atalhos de<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> <xref:System.Windows.Controls.MenuItem.Command%2A>teclado e itens de menu — ou .  
  
<a name="menus_inputgesturetext"></a>
### <a name="inputgesturetext"></a>InputGestureText  
 O exemplo a seguir <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> mostra como usar a <xref:System.Windows.Controls.MenuItem> propriedade para atribuir texto de atalho de teclado aos controles. Isso somente coloca o atalho de teclado no item de menu.  Não associa o comando <xref:System.Windows.Controls.MenuItem>ao . O aplicativo deve manipular a entrada do usuário para executar a ação.  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>
### <a name="command"></a>Comando  
 O exemplo a seguir <xref:System.Windows.Controls.MenuItem.Command%2A> mostra como usar a propriedade <xref:System.Windows.Controls.MenuItem> para associar os comandos **Open** e **Save** com controles. Não só a propriedade de comando <xref:System.Windows.Controls.MenuItem>associa um comando a um , mas também fornece o texto de gesto de entrada para usar como um atalho.  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 A <xref:System.Windows.Controls.MenuItem> classe também <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> tem uma propriedade, que especifica o elemento onde o comando ocorre. Se <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> não estiver definido, o elemento que tem foco no teclado recebe o comando. Para obter mais informações sobre comandos, consulte [Visão Geral dos Comandos](../advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>
## <a name="menu-styling"></a>Estilo de Menu  
 Com o estilo de controle, você pode <xref:System.Windows.Controls.Menu> mudar drasticamente a aparência e o comportamento dos controles sem ter que escrever um controle personalizado. Além de definir propriedades visuais, você <xref:System.Windows.Style> também pode aplicar a partes individuais de um controle, alterar o comportamento de partes do controle através de propriedades ou adicionar peças adicionais ou alterar o layout de um controle. Os exemplos a seguir demonstram <xref:System.Windows.Style> várias <xref:System.Windows.Controls.Menu> maneiras de adicionar a a a um controle.  
  
 O primeiro exemplo de <xref:System.Windows.Style> `Simple` código define um chamado que mostra como usar as configurações atuais do sistema em seu estilo. O código atribui a cor do `MenuHighlightBrush` como cor da tela de fundo do menu e o `MenuTextBrush` como cor de primeiro plano do menu. Observe que as chaves de recurso são utilizadas para atribuir os pincéis.  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 A amostra <xref:System.Windows.Trigger> a seguir usa elementos que <xref:System.Windows.Controls.MenuItem> permitem alterar a aparência <xref:System.Windows.Controls.Menu>de a em resposta aos eventos que ocorrem no . Quando você move o <xref:System.Windows.Controls.Menu>mouse sobre a cor do primeiro plano e as características da fonte dos itens do menu mudam.  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Confira também

- [Exemplo da galeria de controles de WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
