---
title: Novidades do WPF versão 4.5
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 8eff8da7746047c450b2e23af63d43b13f3b970c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746926"
---
# <a name="whats-new-in-wpf-version-45"></a>Novidades do WPF versão 4.5
<a name="introduction"></a>Este tópico contém informações sobre recursos novos e aprimorados no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] versão 4,5.  
  
 Esse tópico contém as seguintes seções:  
  
- [Controle de faixa de opções](#ribbon_control)  
  
- [Desempenho aprimorado ao exibir grandes conjuntos de dados agrupados](#grouped_virtualization)  
  
- [Novos recursos para o VirtualizingPanel](#VirtualizingPanel)  
  
- [Associando a propriedades estáticas](#static_properties)  
  
- [Acesso a coleções em Threads que não sejam de interface do usuário](#xthread_access)  
  
- [Validação de dados de forma síncrona e assíncrona](#INotifyDataErrorInfo)  
  
- [Atualizar automaticamente a fonte de vinculação de dados](#delay)  
  
- [Associando a tipos que implementam ICustomTypeProvider](#ICustomTypeProvider)  
  
- [Recuperando informações de vinculação de dados de uma expressão de associação](#binding_state)  
  
- [Verificando um objeto DataContext válido](#DisconnectedSource)  
  
- [Reposicionamento de dados à medida que os valores mudam (shaping dinâmico)](#live_shaping)  
  
- [Suporte aprimorado para estabelecer uma referência fraca em um evento](#weak_event_pattern)  
  
- [Novos métodos para a classe Dispatcher](#async)  
  
- [Extensões de marcação para eventos](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a>Controle de faixa de opções  
 O WPF 4,5 é fornecido com um controle de <xref:System.Windows.Controls.Ribbon.Ribbon> que hospeda uma barra de ferramentas de acesso rápido, menu do aplicativo e guias.  Para obter mais informações, consulte a [visão geral da faixa de opções](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Desempenho aprimorado ao exibir grandes conjuntos de dados agrupados  
 Virtualização de interface do usuário ocorre quando um subconjunto de elementos da interface do usuário (IU) gerados de um grande número de itens de dados com base em quais itens estão visíveis na tela. O <xref:System.Windows.Controls.VirtualizingPanel> define a propriedade anexada <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> que habilita a virtualização da interface do usuário para dados agrupados.  Para obter mais informações sobre o agrupamento de dados, consulte como: Classificar e Agrupar dados usando um modo de exibição em XAML.  Para obter mais informações sobre a virtualização de dados agrupados, consulte a propriedade <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> anexada.  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a>Novos recursos para o VirtualizingPanel  
  
1. Você pode especificar se um <xref:System.Windows.Controls.VirtualizingPanel>, como o <xref:System.Windows.Controls.VirtualizingStackPanel>, exibe itens parciais usando a propriedade <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> anexada. Se <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> for definido como <xref:System.Windows.Controls.ScrollUnit.Item>, o <xref:System.Windows.Controls.VirtualizingPanel> exibirá apenas os itens que estiverem completamente visíveis. Se <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> for definido como <xref:System.Windows.Controls.ScrollUnit.Pixel>, o <xref:System.Windows.Controls.VirtualizingPanel> poderá exibir itens parcialmente visíveis.  
  
2. Você pode especificar o tamanho do cache antes e depois do visor quando o <xref:System.Windows.Controls.VirtualizingPanel> estiver Virtualizando usando a propriedade <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> anexada.  O cache é a quantidade de espaço acima ou abaixo do visor no qual itens não serão virtualizados.  Usando um cache para evitar a geração de elementos de interface do usuário conforme eles estão colocados na exibição pode melhorar o desempenho. O cache é preenchido com uma prioridade mais baixa para que o aplicativo não estão mais respondendo durante a operação. A propriedade <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> determina a unidade de medida usada pelo <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a>Associando a propriedades estáticas  
 Você pode usar propriedades estáticas como a origem de vinculação de dados. O mecanismo de vinculação de dados reconhece quando o valor da propriedade muda se um evento estático será gerado.  Por exemplo, se a classe `SomeClass` define uma propriedade estática chamada `MyProperty`, `SomeClass` pode definir um evento estático que é gerado quando o valor de `MyProperty` alterações.  O evento estático pode usar qualquer uma das seguintes assinaturas.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Observe que, no primeiro caso, a classe expõe um evento estático chamado *PropertyName*`Changed` que passa <xref:System.EventArgs> para o manipulador de eventos.  No segundo caso, a classe expõe um evento estático chamado `StaticPropertyChanged` que passa <xref:System.ComponentModel.PropertyChangedEventArgs> para o manipulador de eventos. Uma classe que implementa a propriedade estática pode optar por gerar notificações de alteração de propriedade usando um método.  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a>Acesso a coleções em Threads que não sejam de interface do usuário  
 WPF permite acessar e modificar as coleções em threads diferente daquele que criou a coleção de dados.  Isso permite que você use um thread em segundo plano para receber dados de uma fonte externa, como um banco de dados e exibir os dados no thread da interface do usuário.  Usando outro thread para modificar a coleção, a interface do usuário continua a responder à interação do usuário.  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a>Validação de dados de forma síncrona e assíncrona  
 A interface <xref:System.ComponentModel.INotifyDataErrorInfo> permite que classes de entidade de dados implementem regras de validação personalizadas e exponham resultados de validação de forma assíncrona. Essa interface também dá suporte a objetos de erro personalizados, vários erros por propriedade, erros de propriedades cruzadas e erros de nível de entidade.  Para obter mais informações, consulte <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Atualizar automaticamente a fonte de vinculação de dados  
 Se você usar uma associação de dados para atualizar uma fonte de dados, poderá usar a propriedade <xref:System.Windows.Data.BindingBase.Delay%2A> para especificar uma quantidade de tempo a ser passada após a alteração da propriedade no destino antes da atualização da fonte.  Por exemplo, suponha que você tenha um <xref:System.Windows.Controls.Slider> que tenha seu <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> dados de propriedade duas vias vinculados a uma propriedade de um objeto de dados e a propriedade <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> seja definida como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  Neste exemplo, quando o usuário move o <xref:System.Windows.Controls.Slider>, a origem é atualizada para cada pixel que o <xref:System.Windows.Controls.Slider> se move.  O objeto de origem normalmente precisa do valor do controle deslizante somente quando o <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> do controle deslizante para de ser alterado.  Para evitar a atualização da fonte com muita frequência, use <xref:System.Windows.Data.BindingBase.Delay%2A> para especificar que a origem não deve ser atualizada até que uma determinada quantidade de tempo decorra depois que o polegar parar de ser movido.  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Associando a tipos que implementam ICustomTypeProvider  
 O WPF dá suporte à vinculação de dados a objetos que implementam <xref:System.Reflection.ICustomTypeProvider>, também conhecidos como tipos personalizados.  Você pode usar tipos personalizados nos seguintes casos.  
  
1. Como um <xref:System.Windows.PropertyPath> em uma associação de dados. Por exemplo, a propriedade <xref:System.Windows.Data.Binding.Path%2A> de uma <xref:System.Windows.Data.Binding> pode fazer referência a uma propriedade de um tipo personalizado.  
  
2. Como o valor da propriedade <xref:System.Windows.DataTemplate.DataType%2A>.  
  
3. Como um tipo que determina as colunas geradas automaticamente em um <xref:System.Windows.Controls.DataGrid>.  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Recuperando informações de vinculação de dados de uma expressão de associação  
 Em determinados casos, você pode obter a <xref:System.Windows.Data.BindingExpression> de um <xref:System.Windows.Data.Binding> e precisa de informações sobre os objetos de origem e de destino da associação.  Novas APIs foram adicionadas para que você possa obter o código-fonte ou objeto de destino ou a propriedade associada.  Quando você tiver um <xref:System.Windows.Data.BindingExpression>, use as APIs a seguir para obter informações sobre o destino e a origem.  
  
|Para encontrar esse valor da associação|Use essa API|  
|---------------------------------------|------------------|  
|O objeto de destino|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Propriedade de destino|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Objeto de origem|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Propriedade de origem|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Se o <xref:System.Windows.Data.BindingExpression> pertence a um <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|O proprietário de um <xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a>Verificando um objeto DataContext válido  
 Há casos em que a <xref:System.Windows.FrameworkElement.DataContext%2A> de um contêiner de item em um <xref:System.Windows.Controls.ItemsControl> se torna desconectada.  Um contêiner de item é o elemento de interface do usuário que exibe um item em um <xref:System.Windows.Controls.ItemsControl>.  Quando um <xref:System.Windows.Controls.ItemsControl> é associado a dados de uma coleção, um contêiner de item é gerado para cada item. Em alguns casos, os contêineres de itens são removidos da árvore visual. Dois casos típicos em que um contêiner de item é removido são quando um item é removido da coleção subjacente e quando a virtualização é habilitada no <xref:System.Windows.Controls.ItemsControl>. Nesses casos, a propriedade <xref:System.Windows.FrameworkElement.DataContext%2A> do contêiner do item será definida como o objeto Sentinel que é retornado pela propriedade estática <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType>.  Você deve verificar se o <xref:System.Windows.FrameworkElement.DataContext%2A> é igual ao objeto <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> antes de acessar o <xref:System.Windows.FrameworkElement.DataContext%2A> de um contêiner de item.  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Reposicionamento de dados à medida que os valores mudam (shaping dinâmico)  
 Uma coleção de dados pode ser agrupada, classificada ou filtrada. WPF 4.5 permite que os dados sejam reorganizados quando os dados são modificados. Por exemplo, suponha que um aplicativo use um <xref:System.Windows.Controls.DataGrid> para listar ações em um mercado de ações e que as ações sejam classificadas por valor de estoque. Se a classificação dinâmica estiver habilitada na <xref:System.Windows.Data.CollectionView>de ações, a posição de uma ação na <xref:System.Windows.Controls.DataGrid> se moverá quando o valor da ação ficar maior ou menor do que o valor de outra ação.   Para obter mais informações, consulte a interface <xref:System.ComponentModel.ICollectionViewLiveShaping>.  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Suporte aprimorado para estabelecer uma referência fraca em um evento  
 Implementar o padrão de evento fraco agora é mais fácil porque os assinantes de eventos podem participar dele sem implementar uma interface adicional.  A classe <xref:System.Windows.WeakEventManager> genérica também permite que os assinantes participem do padrão de evento fraco se um <xref:System.Windows.WeakEventManager> dedicado não existir para um determinado evento.  Para obter mais informações, consulte [Padrões de evento fraco](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a>Novos métodos para a classe Dispatcher  
 A classe Dispatcher define novos métodos para operações síncronas e assíncronas.  O método de <xref:System.Windows.Threading.Dispatcher.Invoke%2A> síncrono define sobrecargas que usam um parâmetro <xref:System.Action> ou <xref:System.Func%601>. O novo método assíncrono, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, também usa um <xref:System.Action> ou <xref:System.Func%601> como o parâmetro de retorno de chamada e retorna um <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>.   As classes <xref:System.Windows.Threading.DispatcherOperation> e <xref:System.Windows.Threading.DispatcherOperation%601> definem uma propriedade <xref:System.Threading.Tasks.Task>.  Ao chamar <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, você pode usar a palavra-chave `await` com o <xref:System.Windows.Threading.DispatcherOperation> ou o <xref:System.Threading.Tasks.Task>associado. Se você precisar esperar de forma síncrona o <xref:System.Threading.Tasks.Task> retornado por um <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, chame o método de extensão <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>. Chamar <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> resultará em um deadlock se a operação for enfileirada em um thread de chamada. Para obter mais informações sobre como usar um <xref:System.Threading.Tasks.Task> para executar operações assíncronas, consulte [paralelismo de tarefas (biblioteca paralela de tarefas)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a>Extensões de marcação para eventos  
 WPF 4.5 dá suporte a extensões de marcação de eventos.  Embora o WPF não define uma extensão de marcação a ser usado para eventos, terceiros são capazes de criar uma extensão de marcação que pode ser usada com eventos.  
  
## <a name="see-also"></a>Consulte também

- [Novidades no .NET Framework](../../whats-new/index.md)
