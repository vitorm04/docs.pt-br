---
title: "Padrão de design do observador"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IObserver(Of T) interface
- IObservable<T> interface
- IObserver<T> interface
- IObservable(Of T) interface
- observer design pattern [.NET Framework]
ms.assetid: 3680171f-f522-453c-aa4a-54f755a78f88
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83663a28ac7ae19848552583f2ec39a5e96c7fdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="observer-design-pattern"></a>Padrão de design do observador
O padrão de design do observador permite que um assinante para se registrar e receber notificações de um provedor. Ele é adequado para qualquer cenário que requer a notificação por push. Define o padrão de um *provedor* (também conhecido como um *assunto* ou um *observável*) e zero, um ou mais *observadores*. Observadores registrar com o provedor e sempre que uma condição predefinida, evento ou alteração de estado ocorre, o provedor notifica automaticamente todos os observadores chamando um dos seus métodos. Esta chamada de método, o provedor também pode fornecer informações sobre o estado atual para observadores. No .NET Framework, o padrão de design do observador é aplicado com a implementação genérica <xref:System.IObservable%601?displayProperty=nameWithType> e <xref:System.IObserver%601?displayProperty=nameWithType> interfaces. O parâmetro de tipo genérico representa o tipo que fornece informações de notificação.  
  
## <a name="applying-the-pattern"></a>Aplicar o padrão  
 O padrão de design do observador é adequado para notificações por push distribuídas, pois suporta uma separação clara entre dois componentes diferentes ou camadas de aplicativo, como uma camada de (lógica de negócios) de fonte de dados e uma camada de interface (exibição) do usuário. O padrão pode ser implementado sempre que um provedor usa retornos de chamada para fornecer a seus clientes com informações atuais.  
  
 Implementando o padrão exige que você forneça o seguinte:  
  
-   Um provedor ou o assunto, que é o objeto que envia notificações para observadores. Um provedor é uma classe ou estrutura que implementa o <xref:System.IObservable%601> interface. O provedor deve implementar um único método, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, que é chamado pelo observadores que deseja receber notificações do provedor.  
  
-   Um observador, que é um objeto que recebe notificações de um provedor. Um observador é uma classe ou estrutura que implementa o <xref:System.IObserver%601> interface. O observador deve implementar os três métodos, que são chamados pelo provedor:  
  
    -   <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, que fornece o observador com informações novas ou atuais.  
  
    -   <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, que informa o observador que ocorreu um erro.  
  
    -   <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, que indica que o provedor finalizou a enviar notificações.  
  
-   Um mecanismo que permite que o provedor de controlar os observadores. Normalmente, o provedor usa um objeto de contêiner, como um <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> objeto manter referências ao <xref:System.IObserver%601> implementações que se inscreveu para notificações. Usar um contêiner de armazenamento para essa finalidade, permite que o provedor lidar com zero para um número ilimitado de observadores. A ordem na qual os observadores recebem notificações não está definida. o provedor é livre para usar qualquer método para determinar a ordem.  
  
-   Um <xref:System.IDisposable> implementação que permite que o provedor remover os observadores quando a notificação é concluída. Observadores recebem uma referência para o <xref:System.IDisposable> implementação do <xref:System.IObservable%601.Subscribe%2A> método, portanto, eles também podem chamar o <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> método para cancelar a assinatura antes do provedor finalizou a enviar notificações.  
  
-   Um objeto que contém os dados que o provedor envia para seus observadores. O tipo do objeto corresponde ao parâmetro de tipo genérico de <xref:System.IObservable%601> e <xref:System.IObserver%601> interfaces. Embora esse objeto pode ser o mesmo que o <xref:System.IObservable%601> implementação, geralmente é um tipo separado.  
  
> [!NOTE]
>  Além de implementar o padrão de design do observador, você pode estar interessado na exploração de bibliotecas que são criadas usando o <xref:System.IObservable%601> e <xref:System.IObserver%601> interfaces. Por exemplo, [extensões reativas para .NET (Rx)](http://go.microsoft.com/fwlink/?LinkId=186345) consistem em um conjunto de métodos de extensão e operadores de sequência padrão LINQ para dar suporte a programação assíncrona.  
  
## <a name="implementing-the-pattern"></a>Implementando o padrão  
 O exemplo a seguir usa o padrão de design do observador para implementar um sistema de informações de declaração do aeroporto bagagem. Um `BaggageInfo` classe fornece informações sobre voos que chegam e os carrosséis onde bagagem de cada voo está disponível para retirada. Ele é mostrado no exemplo a seguir.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
 [!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]  
  
 Um `BaggageHandler` classe é responsável por receber informações sobre voos que chegam e bagagem carrosséis de declaração. Internamente, ele mantém duas coleções:  
  
-   `observers`-Uma coleção de clientes que receberão informações atualizadas.  
  
-   `flights`-Uma coleção de voos e seus carrosséis atribuídos.  
  
 Ambas as coleções são representadas por genérico <xref:System.Collections.Generic.List%601> objetos são instanciados no `BaggageHandler` construtor de classe. O código-fonte para o `BaggageHandler` é mostrada no exemplo a seguir.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
 [!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]  
  
 Clientes que desejam receber as informações atualizadas chamar o `BaggageHandler.Subscribe` método. Se o cliente não tenha assinado anteriormente para notificações, uma referência para o cliente <xref:System.IObserver%601> implementação é adicionada para o `observers` coleção.  
  
 Sobrecarregados `BaggageHandler.BaggageStatus` método pode ser chamado para indicar que bagagem de um voo está sendo descarregada ou não está sendo descarregada. No primeiro caso, o método é passado um número de voo, aeroporto que originou o voo e o carrossel onde bagagem está sendo descarregada. No segundo caso, o método é transmitido apenas um número de voo. Para bagagem que está sendo descarregado, o método verifica se o `BaggageInfo` informações passadas para o método existem no `flights` coleção. Se não estiver, o método adiciona as informações e chama cada observador `OnNext` método. Para voos cuja bagagem não está sendo descarregada, o método verifica se as informações sobre esse voo são armazenadas na `flights` coleção. Se for, o método chama cada observador `OnNext` método e remove o `BaggageInfo` de objeto o `flights` coleção.  
  
 Quando o último voo do dia inserida e sua bagagem foi processada, o `BaggageHandler.LastBaggageClaimed` método é chamado. Este método chama cada observador `OnCompleted` método para indicar que concluiu todas as notificações e, em seguida, desmarca o `observers` coleção.  
  
 O provedor <xref:System.IObservable%601.Subscribe%2A> método retorna um <xref:System.IDisposable> que permite que os observadores interromper o recebimento de notificações antes da implementação de <xref:System.IObserver%601.OnCompleted%2A> método é chamado. O código-fonte para este `Unsubscriber(Of BaggageInfo)` é mostrada no exemplo a seguir. Quando a classe é instanciada no `BaggageHandler.Subscribe` método, ele é passado como referência para o `observers` coleção e uma referência para o observador que é adicionado à coleção. Essas referências são atribuídas a variáveis locais. Quando o objeto `Dispose` método é chamado, ele verifica se o observador ainda existe no `observers` coleção e, em caso afirmativo, remove o observador.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
 [!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]  
  
 O exemplo a seguir fornece uma <xref:System.IObserver%601> implementação denominada `ArrivalsMonitor`, que é uma classe base que exibe informações de declaração de bagagem. As informações são exibidas em ordem alfabética, por nome da cidade de origem. Os métodos de `ArrivalsMonitor` são marcados como `overridable` (no Visual Basic) ou `virtual` (em c#), assim eles podem todos ser substituídos por uma classe derivada.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
 [!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]  
  
 O `ArrivalsMonitor` classe inclui o `Subscribe` e `Unsubscribe` métodos. O `Subscribe` método permite que a classe salvar o <xref:System.IDisposable> implementação retornada pela chamada para <xref:System.IObservable%601.Subscribe%2A> para uma variável particular. O `Unsubscribe` método permite que a classe cancelar a assinatura de notificações chamando o provedor <xref:System.IDisposable.Dispose%2A> implementação. `ArrivalsMonitor`também fornece implementações do <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>, e <xref:System.IObserver%601.OnCompleted%2A> métodos. Somente o <xref:System.IObserver%601.OnNext%2A> implementação contém uma quantidade significativa de código. O método funciona com um genérico particular, classificado, <xref:System.Collections.Generic.List%601> objeto que mantém informações sobre os aeroportos de origem para voos que chegam e os carrosséis na qual sua bagagem está disponível. Se o `BaggageHandler` classe relata uma novo chegada de voo, o <xref:System.IObserver%601.OnNext%2A> implementação do método adiciona informações sobre esse voo à lista. Se o `BaggageHandler` classe relata que bagagem do voo foi descarregada, o <xref:System.IObserver%601.OnNext%2A> método remove essa voo da lista. Sempre que uma alteração é feita, a lista é classificada e exibida no console.  
  
 O exemplo a seguir contém o ponto de entrada do aplicativo que instancia o `BaggageHandler` classe, bem como duas instâncias do `ArrivalsMonitor` classe e usa o `BaggageHandler.BaggageStatus` método para adicionar e remover informações sobre voos que chegam. Em cada caso, os observadores recebem atualizações em exibem corretamente as informações de declaração de bagagem.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
 [!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Práticas recomendadas para o padrão de design do observador](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Descreve as práticas recomendadas para adotar ao desenvolver aplicativos que implementam o padrão de design do observador.|  
|[Como implementar um provedor](../../../docs/standard/events/how-to-implement-a-provider.md)|Fornece uma implementação de um provedor para uma aplicativo de monitoramento de temperatura.|  
|[Como implementar um observador](../../../docs/standard/events/how-to-implement-an-observer.md)|Fornece uma implementação passo a passo do observador para uma aplicativo de monitoramento de temperatura.|
