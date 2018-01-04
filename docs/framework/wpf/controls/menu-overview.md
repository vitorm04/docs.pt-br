---
title: "Visão geral do menu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ab5092b1bc9db22390a18b2c1cb1ad5725a2037
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="menu-overview"></a>Visão geral do menu
O <xref:System.Windows.Controls.Menu> classe permite que você organize elementos associados com comandos e manipuladores de eventos em ordem hierárquica. Cada <xref:System.Windows.Controls.Menu> elemento contém uma coleção de <xref:System.Windows.Controls.MenuItem> elementos.  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>Controle de Menu  
 O <xref:System.Windows.Controls.Menu> controle apresenta uma lista de itens que especificam comandos ou opções para um aplicativo. Geralmente, clicar em um <xref:System.Windows.Controls.MenuItem> abre um submenu ou faz com que um aplicativo executar um comando.  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>Criando Menus  
 O exemplo a seguir cria um <xref:System.Windows.Controls.Menu> para manipular texto em um <xref:System.Windows.Controls.TextBox>. O <xref:System.Windows.Controls.Menu> contém <xref:System.Windows.Controls.MenuItem> objetos que usam o <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, e <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriedades e o <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, e <xref:System.Windows.Controls.MenuItem.Click> eventos.  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>MenuItems com Atalhos de Teclado  
 Atalhos de teclado são combinações de caracteres que podem ser inseridas com o teclado para invocar <xref:System.Windows.Controls.Menu> comandos. Por exemplo, o atalho para **Copiar** é CTRL+C. Há duas propriedades para usar com atalhos de teclado e itens de menu —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> ou <xref:System.Windows.Controls.MenuItem.Command%2A>.  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> propriedade para atribuir texto de atalho de teclado <xref:System.Windows.Controls.MenuItem> controles. Isso somente coloca o atalho de teclado no item de menu.  Ele não associa o comando com o <xref:System.Windows.Controls.MenuItem>. O aplicativo deve manipular a entrada do usuário para executar a ação.  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>Comando  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.MenuItem.Command%2A> propriedade para associar o **abrir** e **salvar** comandos com <xref:System.Windows.Controls.MenuItem> controles. Não apenas a propriedade de comando associa um comando com um <xref:System.Windows.Controls.MenuItem>, mas ela também fornece o gesto de entrada de texto a ser usado como um atalho.  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 O <xref:System.Windows.Controls.MenuItem> classe também tem um <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> propriedade, que especifica o elemento no qual o comando ocorre. Se <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> não estiver definido, o elemento que tem o foco do teclado recebe o comando. Para obter mais informações sobre comandos, consulte [Visão Geral dos Comandos](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>Estilo de Menu  
 Com estilo de controle, você pode alterar consideravelmente a aparência e comportamento de <xref:System.Windows.Controls.Menu> controles sem precisar escrever um controle personalizado. Além de definir propriedades visuais, você também pode aplicar um <xref:System.Windows.Style> a partes individuais de um controle, alterar o comportamento das partes do controle através das propriedades, ou adicionar partes adicionais ou alterar o layout de um controle. Os exemplos a seguir demonstram várias maneiras de adicionar um <xref:System.Windows.Style> para um <xref:System.Windows.Controls.Menu> controle.  
  
 O primeiro exemplo de código define uma <xref:System.Windows.Style> chamado `Simple` que mostra como usar as configurações atuais do sistema no seu estilo. O código atribui a cor do `MenuHighlightBrush` como cor da tela de fundo do menu e o `MenuTextBrush` como cor de primeiro plano do menu. Observe que as chaves de recurso são utilizadas para atribuir os pincéis.  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 O exemplo a seguir usa <xref:System.Windows.Trigger> elementos que permitem que você alterar a aparência de um <xref:System.Windows.Controls.MenuItem> em resposta a eventos que ocorrem no <xref:System.Windows.Controls.Menu>. Quando você move o mouse sobre o <xref:System.Windows.Controls.Menu>, a cor de primeiro plano e as características da fonte dos itens de menu alterar.  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo da galeria de controles de WPF](http://go.microsoft.com/fwlink/?LinkID=160053)
