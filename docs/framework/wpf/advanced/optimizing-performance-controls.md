---
title: 'Otimizando desempenho: Controles'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: 0917b1555f98fca9cf48cb7d208992848bd8e4b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694627"
---
# <a name="optimizing-performance-controls"></a>Otimizando desempenho: Controles
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] inclui muitos dos componentes comuns de interface do usuário que são usados na maioria dos aplicativos do Windows. Este tópico contém técnicas para melhorar o desempenho de sua interface do usuário.  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>Exibindo conjuntos de dados grandes  
 Controles de WPF como o <xref:System.Windows.Controls.ListView> e <xref:System.Windows.Controls.ComboBox> são usados para exibir listas de itens em um aplicativo. Se a lista a ser exibida for grande, o desempenho do aplicativo poderá ser afetado. Isso ocorre porque o sistema de layout padrão cria um contêiner de layout para cada item associado ao controle de lista e computa a posição e tamanho do layout. Normalmente, você não precisa exibir todos os itens ao mesmo tempo. Em vez disso, você exibe um subconjunto e o usuário rola pela lista. Nesse caso, faz sentido usar a *virtualização* da interface do usuário, o que significa que a geração de contêiner do item e a computação do layout associado a um item são adiadas até que o item esteja visível.  
  
 A virtualização da interface do usuário é um aspecto importante dos controles de lista. A virtualização da interface do usuário não deve ser confundida com a virtualização de dados. A virtualização da interface do usuário armazena somente os itens visíveis na memória, mas em um cenário de associação de dados, armazena toda a estrutura de dados na memória. Em contraste, a virtualização de dados armazena somente os itens de dados visíveis na tela na memória.  
  
 Por padrão, a virtualização de interface do usuário está habilitada para o <xref:System.Windows.Controls.ListView> e <xref:System.Windows.Controls.ListBox> controla quando seus itens de lista estão associados a dados. <xref:System.Windows.Controls.TreeView> a virtualização pode ser habilitada definindo o <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> --> `IsVirtualizing` anexado à propriedade `true`. Se você deseja habilitar a virtualização de interface do usuário para controles personalizados que derivam de <xref:System.Windows.Controls.ItemsControl> ou controles de item existente que usam o <xref:System.Windows.Controls.StackPanel> classe, como <xref:System.Windows.Controls.ComboBox>, você pode definir a <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> para <xref:System.Windows.Controls.VirtualizingStackPanel> e defina <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> para `true`. Infelizmente, você pode desabilitar a virtualização da interface do usuário para esses controles sem perceber. A seguir, temos uma lista de condições que desabilitam a virtualização da interface do usuário.  
  
-   Contêineres de itens são adicionados diretamente para o <xref:System.Windows.Controls.ItemsControl>. Por exemplo, se um aplicativo adicionar explicitamente <xref:System.Windows.Controls.ListBoxItem> objetos para um <xref:System.Windows.Controls.ListBox>, o <xref:System.Windows.Controls.ListBox> não virtualizará os <xref:System.Windows.Controls.ListBoxItem> objetos.  
  
-   Contêineres de item de <xref:System.Windows.Controls.ItemsControl> são de tipos diferentes. Por exemplo, uma <xref:System.Windows.Controls.Menu> que usa <xref:System.Windows.Controls.Separator> objetos não é possível implementar a reciclagem de itens porque o <xref:System.Windows.Controls.Menu> contém objetos do tipo <xref:System.Windows.Controls.Separator> e <xref:System.Windows.Controls.MenuItem>.  
  
-   Definindo <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> para `false`.  
  
-   Definindo <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>--> `IsVirtualizing` para `false`.    
  
 Uma consideração importante quando você virtualiza contêineres de itens é se você tem informações de estado adicionais associadas a um contêiner de item que pertence ao item. Nesse caso, você precisa salvar o estado adicional. Por exemplo, você pode ter um item contido em um <xref:System.Windows.Controls.Expander> controle e o <xref:System.Windows.Controls.Expander.IsExpanded%2A> estado está associado ao contêiner do item e não ao próprio item. Quando o contêiner é reutilizado para um novo item, o valor atual da <xref:System.Windows.Controls.Expander.IsExpanded%2A> é usado para o novo item. Além disso, o item antigo perde correto <xref:System.Windows.Controls.Expander.IsExpanded%2A> valor.  
  
 Atualmente, nenhum controle do WPF dá suporte interno para a virtualização de dados.  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>Reciclagem de Contêineres  
 Uma otimização para virtualização de interface do usuário adicionada no .NET Framework 3.5 SP1 para controles que herdam <xref:System.Windows.Controls.ItemsControl> está *reciclagem de contêineres* que também pode melhorar o desempenho de rolagem.  Quando um <xref:System.Windows.Controls.ItemsControl> que usa virtualização de interface do usuário é preenchida, ele cria um contêiner de itens para cada item que aparece na exibição e destrói o contêiner de item para cada item que sai da exibição. *Reciclagem de contêineres* permite que o controle reutilize os contêineres de item existentes para itens de dados diferentes, para que os contêineres de itens não constantemente são criados e destruídos quando o usuário rolar o <xref:System.Windows.Controls.ItemsControl>. Você pode optar por habilitar o item de reciclagem, definindo o <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> anexado à propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling>.  
  
 Qualquer <xref:System.Windows.Controls.ItemsControl> que ofereça suporte a virtualização pode usar a reciclagem de contêineres.  Para obter um exemplo de como habilitar a reciclagem de contêineres em um <xref:System.Windows.Controls.ListBox>, consulte [melhorar o desempenho de rolagem de um ListBox](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>Suporte à virtualização bidirecional  
 <xref:System.Windows.Controls.VirtualizingStackPanel> oferece suporte interno para virtualização de interface do usuário em uma direção, horizontal ou verticalmente. Se você quiser usar a virtualização bidirecional para seus controles, você deve implementar um painel personalizado que estende o <xref:System.Windows.Controls.VirtualizingStackPanel> classe. O <xref:System.Windows.Controls.VirtualizingStackPanel> classe expõe os métodos virtuais, como <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, e <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Esses métodos virtuais permitem detectar uma alteração na parte visível de uma lista e tratá-la adequadamente.  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>Otimizando modelos  
 A árvore visual contém todos os elementos visuais de um aplicativo.  Além dos objetos criados diretamente, ela também contém objetos decorrentes da expansão do modelo.  Por exemplo, quando você cria um <xref:System.Windows.Controls.Button>, você também pode obter <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> e <xref:System.Windows.Controls.ContentPresenter> objetos na árvore visual.  Se ainda não tiver otimizado seus modelos de controle, você poderá estar criando muitos objetos extra desnecessários na árvore visual.   Para obter mais informações sobre a árvore visual, consulte [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>Rolagem Adiada  
 Por padrão, quando o usuário arrasta o controle de posição em uma barra de rolagem, a exibição de conteúdo é atualizada continuamente.  Se a rolagem estiver lenta em seu controle, considere usar a rolagem adiada.  Com a rolagem adiada, o conteúdo é atualizado somente quando o usuário libera o controle de posição.  
  
 Para implementar a rolagem adiada, defina as <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> propriedade para `true`.  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> é uma propriedade anexada e pode ser definido em <xref:System.Windows.Controls.ScrollViewer> e em qualquer controle que tem um <xref:System.Windows.Controls.ScrollViewer> em seu modelo de controle.  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>Controles que implementam recursos de desempenho  
 A tabela a seguir lista os controles comuns para exibir dados e seu suporte a recursos de desempenho.  Consulte as seções anteriores para obter informações sobre como habilitar esses recursos.  
  
|Controle|Virtualização|Reciclagem de contêineres|Rolagem adiada|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.ContextMenu>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.DocumentViewer>|Não disponível|Não disponível|Pode ser habilitado|  
|<xref:System.Windows.Controls.ListBox>|Padrão|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.ListView>|Padrão|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.TreeView>|Pode ser habilitado|Pode ser habilitado|Pode ser habilitado|  
|<xref:System.Windows.Controls.ToolBar>|Não disponível|Não disponível|Pode ser habilitado|  
  
> [!NOTE]
>  Para obter um exemplo de como habilitar a virtualização e a reciclagem de contêineres em um <xref:System.Windows.Controls.TreeView>, consulte [melhorar o desempenho de um TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md).  
  
## <a name="see-also"></a>Consulte também
- [Layout](../../../../docs/framework/wpf/advanced/layout.md)
- [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
- [Associação de dados](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Controles](../../../../docs/framework/wpf/controls/index.md)
- [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Passo a passo: Cache de dados de aplicativo em um aplicativo WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
