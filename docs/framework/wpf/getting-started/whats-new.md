---
title: "Novidades do WPF versão 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
caps.latest.revision: "55"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4dc6a35a0ff8586b91ab7d74abc182fa6002f88
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="what39s-new-in-wpf-version-45"></a>Novidades do WPF versão 4.5
<a name="introduction"></a>Este tópico contém informações sobre recursos novos e aprimorados no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] versão 4.5.  
  
 Esse tópico contém as seguintes seções:  
  
-   [Controle de faixa de opções](#ribbon_control)  
  
-   [Desempenho aprimorado ao exibir grandes conjuntos de dados agrupados](#grouped_virtualization)  
  
-   [Novos recursos para o VirtualizingPanel](#VirtualizingPanel)  
  
-   [Associando a propriedades estáticas](#static_properties)  
  
-   [Acesso a coleções em Threads que não sejam de interface do usuário](#xthread_access)  
  
-   [Validação de dados de forma síncrona e assíncrona](#INotifyDataErrorInfo)  
  
-   [Atualizar automaticamente a fonte de vinculação de dados](#delay)  
  
-   [Associando a tipos que implementam ICustomTypeProvider](#ICustomTypeProvider)  
  
-   [Recuperando informações de vinculação de dados de uma expressão de associação](#binding_state)  
  
-   [Verificando um objeto DataContext válido](#DisconnectedSource)  
  
-   [Reposicionamento de dados à medida que os valores mudam (shaping dinâmico)](#live_shaping)  
  
-   [Suporte aprimorado para estabelecer uma referência fraca em um evento](#weak_event_pattern)  
  
-   [Novos métodos para a classe Dispatcher](#async)  
  
-   [Extensões de marcação para eventos](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Controle de faixa de opções  
 WPF 4.5 acompanha um <xref:System.Windows.Controls.Ribbon.Ribbon> controle que hospeda uma barra de ferramentas de acesso rápido, guias e o Menu de aplicativo.  Para obter mais informações, consulte a [visão geral da faixa de opções](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Desempenho aprimorado ao exibir grandes conjuntos de dados agrupados  
 Virtualização de interface do usuário ocorre quando um subconjunto de elementos da interface do usuário (IU) gerados de um grande número de itens de dados com base em quais itens estão visíveis na tela. O <xref:System.Windows.Controls.VirtualizingPanel> define o <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> anexado a propriedade que habilita a virtualização de interface do usuário para dados agrupados.  Para obter mais informações sobre o agrupamento de dados, consulte como: Classificar e Agrupar dados usando um modo de exibição em XAML.  Para obter mais informações sobre virtualização de dados agrupados, consulte o <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> propriedade anexada.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Novos recursos para o VirtualizingPanel  
  
1.  Você pode especificar se um <xref:System.Windows.Controls.VirtualizingPanel>, como o <xref:System.Windows.Controls.VirtualizingStackPanel>, exibe itens parciais usando a <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> propriedade anexada. Se <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> é definido como <xref:System.Windows.Controls.ScrollUnit.Item>, o <xref:System.Windows.Controls.VirtualizingPanel> exibirá somente os itens que estão completamente visíveis. Se <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> é definido como <xref:System.Windows.Controls.ScrollUnit.Pixel>, o <xref:System.Windows.Controls.VirtualizingPanel> pode exibir os itens visíveis parcialmente.  
  
2.  Você pode especificar o tamanho do cache antes e depois o visor quando o <xref:System.Windows.Controls.VirtualizingPanel> é virtualização usando o <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> propriedade anexada.  O cache é a quantidade de espaço acima ou abaixo do visor no qual itens não serão virtualizados.  Usando um cache para evitar a geração de elementos de interface do usuário conforme eles estão colocados na exibição pode melhorar o desempenho. O cache é preenchido com uma prioridade mais baixa para que o aplicativo não estão mais respondendo durante a operação. O <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> propriedade determina a unidade de medida é usada pelo <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Associando a propriedades estáticas  
 Você pode usar propriedades estáticas como a origem de vinculação de dados. O mecanismo de vinculação de dados reconhece quando o valor da propriedade muda se um evento estático será gerado.  Por exemplo, se a classe `SomeClass` define uma propriedade estática chamada `MyProperty`, `SomeClass` pode definir um evento estático que é gerado quando o valor de `MyProperty` alterações.  O evento estático pode usar qualquer uma das seguintes assinaturas.  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Observe que, no primeiro caso, a classe expõe um evento estático chamado *PropertyName* `Changed` que passa <xref:System.EventArgs> ao manipulador de eventos.  No segundo caso, a classe expõe um evento estático chamado `StaticPropertyChanged` que passa <xref:System.ComponentModel.PropertyChangedEventArgs> ao manipulador de eventos. Uma classe que implementa a propriedade estática pode optar por gerar notificações de alteração de propriedade usando um método.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Acesso a coleções em Threads que não sejam de interface do usuário  
 WPF permite acessar e modificar as coleções em threads diferente daquele que criou a coleção de dados.  Isso permite que você use um thread em segundo plano para receber dados de uma fonte externa, como um banco de dados e exibir os dados no thread da interface do usuário.  Usando outro thread para modificar a coleção, a interface do usuário continua a responder à interação do usuário.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Validação de dados de forma síncrona e assíncrona  
 O <xref:System.ComponentModel.INotifyDataErrorInfo> interface permite que classes de entidade de dados implementar regras de validação personalizadas e expor os resultados da validação assincronamente. Essa interface também dá suporte a objetos de erro personalizados, vários erros por propriedade, erros de propriedades cruzadas e erros de nível de entidade.  Para obter mais informações, consulte <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Atualizar automaticamente a fonte de vinculação de dados  
 Se você usar uma associação de dados para atualizar uma fonte de dados, você pode usar o <xref:System.Windows.Data.BindingBase.Delay%2A> propriedade para especificar um período de tempo para passar após as alterações de propriedade de destino antes das atualizações de origem.  Por exemplo, suponha que você tenha um <xref:System.Windows.Controls.Slider> com seus <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> bidirecional de dados de propriedade associados a uma propriedade de um objeto de dados e o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> está definida como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  Neste exemplo, quando o usuário move o <xref:System.Windows.Controls.Slider>, as atualizações de origem para cada pixel que o <xref:System.Windows.Controls.Slider> move.  O objeto de origem normalmente precisa o valor do controle deslizante somente quando o controle deslizante <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> interrompe a alteração.  Para evitar que a origem de atualização com muita frequência, use <xref:System.Windows.Data.BindingBase.Delay%2A> para especificar que a origem não deve ser atualizada até que uma determinada quantidade de tempo decorrido após o elevador para de se mover.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Associando a tipos que implementam ICustomTypeProvider  
 WPF oferece suporte à associação de dados para objetos que implementam <xref:System.Reflection.ICustomTypeProvider>, também conhecidos como tipos personalizados.  Você pode usar tipos personalizados nos seguintes casos.  
  
1.  Como um <xref:System.Windows.PropertyPath> em uma associação de dados. Por exemplo, o <xref:System.Windows.Data.Binding.Path%2A> propriedade de um <xref:System.Windows.Data.Binding> pode fazer referência a uma propriedade de um tipo personalizado.  
  
2.  Como o valor de <xref:System.Windows.DataTemplate.DataType%2A> propriedade.  
  
3.  Como um tipo que determina as colunas geradas automaticamente em um <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Recuperando informações de vinculação de dados de uma expressão de associação  
 Em certos casos, você pode obter o <xref:System.Windows.Data.BindingExpression> de um <xref:System.Windows.Data.Binding> e precisar de informações sobre os objetos de origem e de destino da associação.  Novas APIs foram adicionadas para que você possa obter o código-fonte ou objeto de destino ou a propriedade associada.  Quando você tiver um <xref:System.Windows.Data.BindingExpression>, use as seguintes APIs para obter informações sobre a origem e destino.  
  
|Para encontrar esse valor da associação|Use essa API|  
|---------------------------------------|------------------|  
|O objeto de destino|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Propriedade de destino|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Objeto de origem|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Propriedade de origem|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Se o <xref:System.Windows.Data.BindingExpression> pertence a um<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|O proprietário de um<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Verificando um objeto DataContext válido  
 Há casos em que o <xref:System.Windows.FrameworkElement.DataContext%2A> de um contêiner de itens em uma <xref:System.Windows.Controls.ItemsControl> estiver desconectado.  Um contêiner de itens é o elemento de interface do usuário que exibe um item em uma <xref:System.Windows.Controls.ItemsControl>.  Quando um <xref:System.Windows.Controls.ItemsControl> dados associado a uma coleção, um contêiner de itens é gerado para cada item. Em alguns casos, os contêineres de itens são removidos da árvore visual. São de dois casos comuns em que um contêiner do item é removido quando um item é removido da coleção subjacente e quando a opção de virtualização está ativada o <xref:System.Windows.Controls.ItemsControl>. Nesses casos, o <xref:System.Windows.FrameworkElement.DataContext%2A> propriedade do item contêiner será definida para o objeto de sentinela retornado pelo <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> propriedade estática.  Você deve verificar se o <xref:System.Windows.FrameworkElement.DataContext%2A> é igual de <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> objeto antes de acessar o <xref:System.Windows.FrameworkElement.DataContext%2A> de um contêiner de itens.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Reposicionamento de dados à medida que os valores mudam (shaping dinâmico)  
 Uma coleção de dados pode ser agrupada, classificada ou filtrada. WPF 4.5 permite que os dados sejam reorganizados quando os dados são modificados. Por exemplo, suponha que um aplicativo usa um <xref:System.Windows.Controls.DataGrid> para listar as ações em um mercado de ações e as ações são classificadas pelo valor de estoque. Se a classificação ao vivo está habilitada nas ações <xref:System.Windows.Data.CollectionView>, a posição do estoque no <xref:System.Windows.Controls.DataGrid> move quando o valor do estoque se torna maior ou o valor do estoque menor que outro.   Para obter mais informações, consulte o <xref:System.ComponentModel.ICollectionViewLiveShaping> interface.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Suporte aprimorado para estabelecer uma referência fraca em um evento  
 Implementar o padrão de evento fraco agora é mais fácil porque os assinantes de eventos podem participar dele sem implementar uma interface adicional.  Genérica <xref:System.Windows.WeakEventManager> classe também habilita os assinantes participar no padrão de evento fraco se dedicado <xref:System.Windows.WeakEventManager> não existe para um determinado evento.  Para obter mais informações, consulte [Padrões de evento fraco](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Novos métodos para a classe Dispatcher  
 A classe Dispatcher define novos métodos para operações síncronas e assíncronas.  Síncronos <xref:System.Windows.Threading.Dispatcher.Invoke%2A> método define sobrecargas que têm um <xref:System.Action> ou <xref:System.Func%601> parâmetro. O novo método assíncrono, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, também usa um <xref:System.Action> ou <xref:System.Func%601> como o parâmetro de retorno de chamada e retorna um <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>.   O <xref:System.Windows.Threading.DispatcherOperation> e <xref:System.Windows.Threading.DispatcherOperation%601> classes definem um <xref:System.Threading.Tasks.Task> propriedade.  Quando você chama <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, você pode usar o `await` palavra-chave com o o <xref:System.Windows.Threading.DispatcherOperation> ou associado <xref:System.Threading.Tasks.Task>. Se você precisa esperar de forma síncrona para o <xref:System.Threading.Tasks.Task> que é retornado por uma <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, chame o <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> método de extensão. Chamando <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> resultará em um deadlock se a operação está em fila em um thread de chamada. Para obter mais informações sobre como usar um <xref:System.Threading.Tasks.Task> para executar operações assíncronas, consulte [paralelismo de tarefas (Task Parallel Library)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Extensões de marcação para eventos  
 WPF 4.5 dá suporte a extensões de marcação de eventos.  Embora o WPF não define uma extensão de marcação a ser usado para eventos, terceiros são capazes de criar uma extensão de marcação que pode ser usada com eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Novidades no .NET Framework](../../../../docs/framework/whats-new/index.md)
