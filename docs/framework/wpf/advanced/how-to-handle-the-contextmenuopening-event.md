---
title: 'Como: Tratar o evento ContextMenuOpening'
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: 794fad2708c799b9e5fb8ff1d2875648f886fdbb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655836"
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Como: Tratar o evento ContextMenuOpening
O <xref:System.Windows.FrameworkElement.ContextMenuOpening> evento pode ser tratado em um aplicativo para ajustar um menu de contexto existente antes para exibir ou suprimir o menu que seria exibido, definindo o <xref:System.Windows.RoutedEventArgs.Handled%2A> propriedade `true` nos dados do evento. A razão típica para configuração <xref:System.Windows.RoutedEventArgs.Handled%2A> à `true` no evento dados são substituir o menu completamente com um novo <xref:System.Windows.Controls.ContextMenu> do objeto, que requer, às vezes, o cancelamento da operação e inicie uma nova abertura. Se você escrever manipuladores para o <xref:System.Windows.FrameworkElement.ContextMenuOpening> evento, você deve conhecer os problemas de tempo entre um <xref:System.Windows.Controls.ContextMenu> controle e o serviço que é responsável pela abertura e posicionamento dos menus de contexto para controles em geral. Este tópico ilustra algumas das técnicas de código para vários cenários de abertura do menu de contexto e ilustra um caso em que ocorre um problema de sincronismo.  
  
 Há vários cenários para a manipulação de <xref:System.Windows.FrameworkElement.ContextMenuOpening> eventos:  
  
-   Ajustar os itens de menu antes da exibição.  
  
-   Substituir o menu inteiro antes da exibição.  
  
-   Suprimir completamente qualquer menu de contexto existente e não exibir nenhum menu de contexto.  
  
## <a name="example"></a>Exemplo  
  
## <a name="adjusting-the-menu-items-before-display"></a>Ajustar os itens de menu antes da exibição  
 Ajustar os itens de menu existentes é relativamente simples e é provavelmente o cenário mais comum. Você pode fazer isso para adicionar ou subtrair opções do menu de contexto em resposta a informações do estado atual em seu aplicativo ou informações do estado específico que está disponível como uma propriedade no objeto no qual o menu de contexto é solicitado.  
  
 A técnica geral é obter a origem do evento, que é o controle específico que foi clicado, e obter o <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriedade dele. Você geralmente deseja verificar a <xref:System.Windows.Controls.ItemsControl.Items%2A> coleção para ver quais itens de menu de contexto já existem no menu e, em seguida, adicionar ou remover os novos <xref:System.Windows.Controls.MenuItem> de ou para a coleção de itens.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Substituir o menu inteiro antes da exibição  
 Um cenário alternativo é se você deseja substituir o menu de contexto inteiro. Você certamente também pode usar uma variação do código anterior, para remover todos os itens de um menu de contexto existente e adicionar novos começando com o item zero. Mas a abordagem mais intuitiva para substituir todos os itens de menu de contexto é criar um novo <xref:System.Windows.Controls.ContextMenu>, preenchê-lo com itens e, em seguida, defina a <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> propriedade de um controle para ser o novo <xref:System.Windows.Controls.ContextMenu>.  
  
 A seguir está o código do manipulador simples para substituir um <xref:System.Windows.Controls.ContextMenu>. O código referencia um método `BuildMenu` personalizado, que é separado porque ele é chamado por mais de um dos manipuladores de exemplo.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 No entanto, se você usar esse estilo de manipulador <xref:System.Windows.FrameworkElement.ContextMenuOpening>, você pode potencialmente expor um problema de sincronismo se o objeto ao qual você está definindo o <xref:System.Windows.Controls.ContextMenu> não tem um menu de contexto preexistente. Quando um usuário clica um controle <xref:System.Windows.FrameworkElement.ContextMenuOpening> é gerado mesmo se existente <xref:System.Windows.Controls.ContextMenu> está vazio ou nulo. Mas nesse caso, qualquer novo <xref:System.Windows.Controls.ContextMenu> definida na fonte de elemento chega muito tarde para ser exibido. Além disso, se o usuário para o botão direito do mouse uma segunda vez, desta vez seu novo <xref:System.Windows.Controls.ContextMenu> for exibida, o valor é não nulo e seu manipulador corretamente substituirá e exibir o menu quando o manipulador é executado uma segunda vez. Isso sugere duas soluções possíveis:  
  
1.  Garantir que <xref:System.Windows.FrameworkElement.ContextMenuOpening> sempre são executados em controles que têm pelo menos um espaço reservado de manipuladores <xref:System.Windows.Controls.ContextMenu> disponível, que você pretende ser substituído pelo código do manipulador. Nesse caso, você ainda pode usar o manipulador mostrado no exemplo anterior, mas você geralmente deseja atribuir um espaço reservado <xref:System.Windows.Controls.ContextMenu> na marcação inicial:  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  Suponha que o inicial <xref:System.Windows.Controls.ContextMenu> valor pode ser nulo, com base em alguma lógica preliminar. Você poderia verificar <xref:System.Windows.Controls.ContextMenu> nulo, ou usar um sinalizador em seu código para verificar se seu manipulador tiver sido executado pelo menos uma vez. Como você supõe que o <xref:System.Windows.Controls.ContextMenu> sobre a ser exibido, seu manipulador e define <xref:System.Windows.RoutedEventArgs.Handled%2A> para `true` nos dados do evento. Para o <xref:System.Windows.Controls.ContextMenuService> que é responsável pela exibição do menu de contexto, uma `true` valor para <xref:System.Windows.RoutedEventArgs.Handled%2A> no evento dados representa uma solicitação para cancelar a exibição do menu de contexto / combinação de controles que acionou o evento.  
  
 Agora que você suprimiu o menu de contexto possivelmente suspeito, a próxima etapa é fornecer um novo e, em seguida, exibi-lo. Definir o novo menu é basicamente o mesmo que o manipulador anterior: cria um novo <xref:System.Windows.Controls.ContextMenu> e defina a origem de controle <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> propriedade com ele. A etapa adicional é que agora você deve forçar a exibição do menu de contexto, pois você suprimiu a primeira tentativa. Para forçar a exibição, você deve definir a <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> propriedade para `true` dentro do manipulador. Tenha cuidado ao fazer isso, pois abrindo o menu de contexto no manipulador gera o <xref:System.Windows.FrameworkElement.ContextMenuOpening> evento novamente. Se você digitar novamente o manipulador, ele se tornará infinitamente recursivo. Isso é por isso que você sempre precisará verificar se há `null` ou usar um sinalizador se você abrir um menu de contexto de dentro um <xref:System.Windows.FrameworkElement.ContextMenuOpening> manipulador de eventos.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Suprimir qualquer menu de contexto existente e não exibir nenhum menu de contexto  
 O cenário final, escrever um manipulador que suprima um menu totalmente, é incomum. Se um determinado controle não deve exibir um menu de contexto, existem maneiras provavelmente mais adequadas para garantir isso do que eliminar o menu apenas quando um usuário solicitar. Mas se você deseja usar o manipulador para suprimir um menu de contexto e não mostrar nada, então o manipulador deve simplesmente definir <xref:System.Windows.RoutedEventArgs.Handled%2A> para `true` nos dados do evento. O <xref:System.Windows.Controls.ContextMenuService> que é responsável por exibir um menu de contexto verificará os dados do evento do evento que ele gerou no controle. Se o evento foi marcado como <xref:System.Windows.RoutedEventArgs.Handled%2A> em qualquer lugar ao longo da rota, então a ação de abertura de menu de contexto que iniciou o evento será suprimida.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>
- [Visão geral de elementos base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)
- [Visão geral de ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
