---
title: Novidades do WPF versão 4.5
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
ms.openlocfilehash: 708b2fc231bfe7a9bc1f52872a0ec41c91931f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174700"
---
# <a name="whats-new-in-wpf-version-45"></a>Novidades do WPF versão 4.5
<a name="introduction"></a>Este tópico contém informações sobre recursos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] novos e aprimorados na versão 4.5.  
  
 Este tópico contém as seguintes seções:  
  
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
 O WPF 4.5 <xref:System.Windows.Controls.Ribbon.Ribbon> é fornecido com um controle que hospeda uma barra de ferramentas de acesso rápido, menu de aplicativos e guias.  Para obter mais informações, consulte a [visão geral da faixa de opções](/visualstudio/vsto/ribbon-overview).  
  
<a name="grouped_virtualization"></a>
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a>Desempenho aprimorado ao exibir grandes conjuntos de dados agrupados  
 Virtualização de interface do usuário ocorre quando um subconjunto de elementos da interface do usuário (IU) gerados de um grande número de itens de dados com base em quais itens estão visíveis na tela. O <xref:System.Windows.Controls.VirtualizingPanel> define <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> a propriedade anexada que permite a virtualização da ui para dados agrupados.  Para obter mais informações sobre o agrupamento de dados, consulte como: Classificar e Agrupar dados usando um modo de exibição em XAML.  Para obter mais informações sobre a <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> virtualização de dados agrupados, consulte a propriedade anexada.  
  
<a name="VirtualizingPanel"></a>
## <a name="new-features-for-the-virtualizingpanel"></a>Novos recursos para o VirtualizingPanel  
  
1. Você pode especificar se <xref:System.Windows.Controls.VirtualizingPanel> <xref:System.Windows.Controls.VirtualizingStackPanel>um , como o , <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> exibe itens parciais usando a propriedade anexada. Se <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> estiver <xref:System.Windows.Controls.ScrollUnit.Item>definido <xref:System.Windows.Controls.VirtualizingPanel> como , o exibirá apenas itens completamente visíveis. Se <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> estiver <xref:System.Windows.Controls.ScrollUnit.Pixel>definido <xref:System.Windows.Controls.VirtualizingPanel> como , a lata pode exibir itens parcialmente visíveis.  
  
2. Você pode especificar o tamanho do cache antes <xref:System.Windows.Controls.VirtualizingPanel> e depois da <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> porta de exibição quando estiver virtualizando usando a propriedade anexada.  O cache é a quantidade de espaço acima ou abaixo do visor no qual itens não serão virtualizados.  Usando um cache para evitar a geração de elementos de interface do usuário conforme eles estão colocados na exibição pode melhorar o desempenho. O cache é preenchido com uma prioridade mais baixa para que o aplicativo não estão mais respondendo durante a operação. A <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> propriedade determina a unidade de <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>medida que é usada por .  
  
<a name="static_properties"></a>
## <a name="binding-to-static-properties"></a>Associando a propriedades estáticas  
 Você pode usar propriedades estáticas como a origem de vinculação de dados. O mecanismo de vinculação de dados reconhece quando o valor da propriedade muda se um evento estático será gerado.  Por exemplo, se a classe `SomeClass` define uma propriedade estática chamada `MyProperty`, `SomeClass` pode definir um evento estático que é gerado quando o valor de `MyProperty` alterações.  O evento estático pode usar qualquer uma das seguintes assinaturas.  
  
- `public static event EventHandler MyPropertyChanged;`  
  
- `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 Observe que, no primeiro caso, a classe expõe um <xref:System.EventArgs> evento estático chamado *PropertyName* `Changed` que passa para o manipulador de eventos.  No segundo caso, a classe expõe `StaticPropertyChanged` um <xref:System.ComponentModel.PropertyChangedEventArgs> evento estático chamado que passa para o manipulador de eventos. Uma classe que implementa a propriedade estática pode optar por gerar notificações de alteração de propriedade usando um método.  
  
<a name="xthread_access"></a>
## <a name="accessing-collections-on-non-ui-threads"></a>Acesso a coleções em Threads que não sejam de interface do usuário  
 WPF permite acessar e modificar as coleções em threads diferente daquele que criou a coleção de dados.  Isso permite que você use um thread em segundo plano para receber dados de uma fonte externa, como um banco de dados e exibir os dados no thread da interface do usuário.  Usando outro thread para modificar a coleção, a interface do usuário continua a responder à interação do usuário.  
  
<a name="INotifyDataErrorInfo"></a>
## <a name="synchronously-and-asynchronously-validating-data"></a>Validação de dados de forma síncrona e assíncrona  
 A <xref:System.ComponentModel.INotifyDataErrorInfo> interface permite que as classes de entidades de dados implementem regras de validação personalizadas e exponham os resultados de validação de forma assíncrona. Essa interface também dá suporte a objetos de erro personalizados, vários erros por propriedade, erros de propriedades cruzadas e erros de nível de entidade.  Para obter mais informações, consulte <xref:System.ComponentModel.INotifyDataErrorInfo>.  
  
<a name="delay"></a>
## <a name="automatically-updating-the-source-of-a-data-binding"></a>Atualizar automaticamente a fonte de vinculação de dados  
 Se você usar uma vinculação de dados para <xref:System.Windows.Data.BindingBase.Delay%2A> atualizar uma fonte de dados, você pode usar a propriedade para especificar um período de tempo para passar após as alterações de propriedade no destino antes das atualizações de origem.  Por exemplo, suponha <xref:System.Windows.Controls.Slider> que <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> você tenha um que tenha seus dados de <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade vinculados a uma propriedade de um objeto de dados e a propriedade está definida como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  Neste exemplo, quando o <xref:System.Windows.Controls.Slider>usuário move o , a <xref:System.Windows.Controls.Slider> fonte atualiza para cada pixel que o movimento.  O objeto de origem normalmente precisa do valor do <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> controle deslizante somente quando o controle deslizante parar de mudar.  Para evitar a atualização da <xref:System.Windows.Data.BindingBase.Delay%2A> fonte com muita freqüência, use para especificar que a fonte não deve ser atualizada até que uma certa quantidade de tempo decorrido depois que o polegar parar de se mover.  
  
<a name="ICustomTypeProvider"></a>
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a>Associando a tipos que implementam ICustomTypeProvider  
 O WPF suporta a vinculação de dados a objetos que implementam, <xref:System.Reflection.ICustomTypeProvider>também conhecidos como tipos personalizados.  Você pode usar tipos personalizados nos seguintes casos.  
  
1. Como <xref:System.Windows.PropertyPath> um em uma vinculação de dados. Por exemplo, <xref:System.Windows.Data.Binding.Path%2A> a <xref:System.Windows.Data.Binding> propriedade de uma lata pode referenciar uma propriedade de um tipo personalizado.  
  
2. Como o valor <xref:System.Windows.DataTemplate.DataType%2A> da propriedade.  
  
3. Como um tipo que determina as colunas <xref:System.Windows.Controls.DataGrid>geradas automaticamente em um .  
  
<a name="binding_state"></a>
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a>Recuperando informações de vinculação de dados de uma expressão de associação  
 Em certos casos, você <xref:System.Windows.Data.BindingExpression> pode <xref:System.Windows.Data.Binding> obter a de um e precisa de informações sobre a origem e objetos de destino da vinculação.  Novas APIs foram adicionadas para que você possa obter o código-fonte ou objeto de destino ou a propriedade associada.  Quando você <xref:System.Windows.Data.BindingExpression>tiver um , use as seguintes APIs para obter informações sobre o alvo e a fonte.  
  
|Para encontrar esse valor da associação|Use essa API|  
|---------------------------------------|------------------|  
|O objeto de destino|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|Propriedade de destino|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|Objeto de origem|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|Propriedade de origem|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|Se <xref:System.Windows.Data.BindingExpression> o pertence a um<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|O dono de um<xref:System.Windows.Data.BindingGroup>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>
## <a name="checking-for-a-valid-datacontext-object"></a>Verificando um objeto DataContext válido  
 Há casos em <xref:System.Windows.FrameworkElement.DataContext%2A> que o recipiente <xref:System.Windows.Controls.ItemsControl> de um item em um fica desconectado.  Um recipiente de itens é o elemento UI <xref:System.Windows.Controls.ItemsControl>que exibe um item em um .  Quando <xref:System.Windows.Controls.ItemsControl> um é vinculado a uma coleção, um contêiner de itens é gerado para cada item. Em alguns casos, os contêineres de itens são removidos da árvore visual. Dois casos típicos em que um recipiente de itens é removido são quando um item <xref:System.Windows.Controls.ItemsControl>é removido da coleção subjacente e quando a virtualização é ativada no . Nestes casos, <xref:System.Windows.FrameworkElement.DataContext%2A> a propriedade do contêiner de itens será definida para <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> o objeto sentinela que é devolvido pela propriedade estática.  Você deve verificar <xref:System.Windows.FrameworkElement.DataContext%2A> se o <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> objeto é <xref:System.Windows.FrameworkElement.DataContext%2A> igual ao objeto antes de acessar o recipiente de um item.  
  
<a name="live_shaping"></a>
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a>Reposicionamento de dados à medida que os valores mudam (shaping dinâmico)  
 Uma coleção de dados pode ser agrupada, classificada ou filtrada. WPF 4.5 permite que os dados sejam reorganizados quando os dados são modificados. Por exemplo, suponha <xref:System.Windows.Controls.DataGrid> que um aplicativo use um para listar ações em um mercado de ações e as ações são classificadas pelo valor das ações. Se a classificação ao vivo <xref:System.Windows.Data.CollectionView>estiver habilitada nas ações, uma posição de ação nos <xref:System.Windows.Controls.DataGrid> movimentos quando o valor das ações se torna maior ou menor do que o valor de outra ação.   Para obter mais <xref:System.ComponentModel.ICollectionViewLiveShaping> informações, consulte a interface.  
  
<a name="weak_event_pattern"></a>
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a>Suporte aprimorado para estabelecer uma referência fraca em um evento  
 Implementar o padrão de evento fraco agora é mais fácil porque os assinantes de eventos podem participar dele sem implementar uma interface adicional.  A <xref:System.Windows.WeakEventManager> classe genérica também permite que os assinantes participem <xref:System.Windows.WeakEventManager> do padrão de evento fraco se um dedicado não existir para um determinado evento.  Para obter mais informações, consulte [Padrões de evento fraco](../advanced/weak-event-patterns.md).  
  
<a name="async"></a>
## <a name="new-methods-for-the-dispatcher-class"></a>Novos métodos para a classe Dispatcher  
 A classe Dispatcher define novos métodos para operações síncronas e assíncronas.  O <xref:System.Windows.Threading.Dispatcher.Invoke%2A> método síncrono define sobrecargas que tomam um <xref:System.Action> ou <xref:System.Func%601> parâmetro. O <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>novo método assíncrono, <xref:System.Action> <xref:System.Func%601> também toma um ou como <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601>parâmetro de retorno de chamada e retorna a ou .   As <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601> aulas definem uma <xref:System.Threading.Tasks.Task> propriedade.  Quando você <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>ligar, você `await` pode usar <xref:System.Windows.Threading.DispatcherOperation> a palavra-chave com o ou o associado <xref:System.Threading.Tasks.Task>. Se você precisar esperar sincronizadamente <xref:System.Threading.Tasks.Task> para o que <xref:System.Windows.Threading.DispatcherOperation> <xref:System.Windows.Threading.DispatcherOperation%601>é devolvido <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> por um ou , ligue para o método de extensão. A <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> chamada resultará em um impasse se a operação estiver na fila de um segmento de chamada. Para obter mais <xref:System.Threading.Tasks.Task> informações sobre como usar um para executar operações assíncronas, consulte [O Paralelismo de Tarefas (Biblioteca Paralela de Tarefas)](../../../standard/parallel-programming/task-based-asynchronous-programming.md).  
  
<a name="events_markup_extenions"></a>
## <a name="markup-extensions-for-events"></a>Extensões de marcação para eventos  
 WPF 4.5 dá suporte a extensões de marcação de eventos.  Embora o WPF não define uma extensão de marcação a ser usado para eventos, terceiros são capazes de criar uma extensão de marcação que pode ser usada com eventos.  
  
## <a name="see-also"></a>Confira também

- [O que há de novo no Quadro .NET](../../whats-new/index.md)
