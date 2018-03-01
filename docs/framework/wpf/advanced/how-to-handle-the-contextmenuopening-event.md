---
title: Como tratar o evento ContextMenuOpening
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
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5eec8646a48f94fb9ffdcad14849416732618a06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Como tratar o evento ContextMenuOpening
O <xref:System.Windows.FrameworkElement.ContextMenuOpening> evento pode ser tratado em um aplicativo para ajustar um menu de contexto existente antes para exibir ou suprimir o menu que seria exibido caso contrário, definindo a <xref:System.Windows.RoutedEventArgs.Handled%2A> propriedade `true` nos dados do evento. A razão típica para configuração <xref:System.Windows.RoutedEventArgs.Handled%2A> para `true` no evento dados são substituir o menu inteiramente com um novo <xref:System.Windows.Controls.ContextMenu> do objeto, que às vezes requer Cancelando a operação e inicie uma nova abertura. Se você escrever manipuladores para o <xref:System.Windows.FrameworkElement.ContextMenuOpening> eventos, você deve estar ciente dos problemas de tempo entre um <xref:System.Windows.Controls.ContextMenu> controle e o serviço que é responsável pela abertura e posicionamento dos menus de contexto para controles em geral. Este tópico ilustra algumas das técnicas de código para vários cenários de abertura do menu de contexto e ilustra um caso em que ocorre um problema de sincronismo.  
  
 Há várias situações para tratar o <xref:System.Windows.FrameworkElement.ContextMenuOpening> evento:  
  
-   Ajustar os itens de menu antes da exibição.  
  
-   Substituir o menu inteiro antes da exibição.  
  
-   Suprimir completamente qualquer menu de contexto existente e não exibir nenhum menu de contexto.  
  
## <a name="example"></a>Exemplo  
  
## <a name="adjusting-the-menu-items-before-display"></a>Ajustar os itens de menu antes da exibição  
 Ajustar os itens de menu existentes é relativamente simples e é provavelmente o cenário mais comum. Você pode fazer isso para adicionar ou subtrair opções do menu de contexto em resposta a informações do estado atual em seu aplicativo ou informações do estado específico que está disponível como uma propriedade no objeto no qual o menu de contexto é solicitado.  
  
 A técnica geral é obter a origem do evento, que é o controle específico que foi clicado, e obter o <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriedade dele. Normalmente, você deseja verificar o <xref:System.Windows.Controls.ItemsControl.Items%2A> coleção para ver quais itens de menu de contexto já existe no menu e, em seguida, adicionar ou remover os novos <xref:System.Windows.Controls.MenuItem> de ou para a coleção de itens.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Substituir o menu inteiro antes da exibição  
 Um cenário alternativo é se você deseja substituir o menu de contexto inteiro. Você certamente também pode usar uma variação do código anterior, para remover todos os itens de um menu de contexto existente e adicionar novos começando com o item zero. Mas a abordagem mais intuitiva para substituir todos os itens no menu de contexto é criar um novo <xref:System.Windows.Controls.ContextMenu>, preenchê-lo com os itens e, em seguida, definir o <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> propriedade de um controle para ser o novo <xref:System.Windows.Controls.ContextMenu>.  
  
 A seguir está o código do manipulador simples para substituir um <xref:System.Windows.Controls.ContextMenu>. O código referencia um método `BuildMenu` personalizado, que é separado porque ele é chamado por mais de um dos manipuladores de exemplo.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 No entanto, se você usar esse estilo de manipulador para <xref:System.Windows.FrameworkElement.ContextMenuOpening>, você pode potencialmente expor um problema de sincronização se o objeto ao qual você está definindo o <xref:System.Windows.Controls.ContextMenu> não tem um menu de contexto preexistente. Quando um usuário clica um controle <xref:System.Windows.FrameworkElement.ContextMenuOpening> será gerado mesmo se existente <xref:System.Windows.Controls.ContextMenu> está vazio ou nulo. Mas nesse caso, qualquer novo <xref:System.Windows.Controls.ContextMenu> definida na fonte de elemento chega muito tarde para ser exibido. Além disso, se o usuário clique uma segunda vez, desta vez seu novo <xref:System.Windows.Controls.ContextMenu> aparece, o valor não nulo e o manipulador corretamente substituirá e exibir o menu quando o manipulador é executada uma segunda vez. Isso sugere duas soluções possíveis:  
  
1.  Garantir que <xref:System.Windows.FrameworkElement.ContextMenuOpening> manipuladores sempre executados em controles que têm pelo menos um espaço reservado <xref:System.Windows.Controls.ContextMenu> disponíveis, que você pretende ser substituído pelo código do manipulador. Nesse caso, você ainda pode usar o manipulador mostrado no exemplo anterior, mas você geralmente deseja atribuir um espaço reservado <xref:System.Windows.Controls.ContextMenu> na marcação inicial:  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  Suponha que o inicial <xref:System.Windows.Controls.ContextMenu> valor pode ser nulo, com base em alguma lógica preliminar. Você poderia verificar <xref:System.Windows.Controls.ContextMenu> nulo, ou usar um sinalizador em seu código para verificar se o manipulador foi executado pelo menos uma vez. Como você supõe que o <xref:System.Windows.Controls.ContextMenu> está prestes a ser exibido, o manipulador e define <xref:System.Windows.RoutedEventArgs.Handled%2A> para `true` nos dados do evento. Para o <xref:System.Windows.Controls.ContextMenuService> que é responsável pela exibição do menu de contexto, um `true` valor para <xref:System.Windows.RoutedEventArgs.Handled%2A> no evento dados representam uma solicitação para cancelar a exibição do menu de contexto / combinação de controles que gerou o evento.  
  
 Agora que você suprimiu o menu de contexto possivelmente suspeito, a próxima etapa é fornecer um novo e, em seguida, exibi-lo. Definindo um novo menu é basicamente o mesmo que o manipulador anterior: cria um novo <xref:System.Windows.Controls.ContextMenu> e defina a origem de controle <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> propriedade com ele. A etapa adicional é que agora você deve forçar a exibição do menu de contexto, pois você suprimiu a primeira tentativa. Para forçar a exibição, você deve definir o <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> propriedade `true` dentro do manipulador. Tenha cuidado ao fazer isso, como abrir o menu de contexto no manipulador gera o <xref:System.Windows.FrameworkElement.ContextMenuOpening> evento novamente. Se você digitar novamente o manipulador, ele se tornará infinitamente recursivo. Isso é porque você sempre precisará verificar `null` ou usar um sinalizador se você abrir um menu de contexto de dentro um <xref:System.Windows.FrameworkElement.ContextMenuOpening> manipulador de eventos.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Suprimir qualquer menu de contexto existente e não exibir nenhum menu de contexto  
 O cenário final, escrever um manipulador que suprima um menu totalmente, é incomum. Se um determinado controle não deve exibir um menu de contexto, existem maneiras provavelmente mais adequadas para garantir isso do que eliminar o menu apenas quando um usuário solicitar. Mas se você deseja usar o manipulador para suprimir um menu de contexto e não mostrar nada, o manipulador simplesmente deve definir <xref:System.Windows.RoutedEventArgs.Handled%2A> para `true` nos dados do evento. O <xref:System.Windows.Controls.ContextMenuService> que é responsável pela exibição de um menu de contexto verificará os dados do evento do evento que ele gerou no controle. Se o evento foi marcado como <xref:System.Windows.RoutedEventArgs.Handled%2A> em qualquer lugar na rota, então a ação de abertura de menu de contexto que iniciou o evento será suprimida.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>  
 [Visão geral de elementos base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Visão geral de ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
