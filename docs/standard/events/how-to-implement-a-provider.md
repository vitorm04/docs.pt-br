---
title: Como implementar um provedor
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
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9d8f96de8cb3d13568e755f1d5e885e0474d891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-provider"></a>Como implementar um provedor
O padrão de design do observador requer uma divisão entre um provedor, que monitora os dados e envia notificações, e um ou mais observadores, que recebem notificações (retornos de chamada) do provedor. Este tópico discute como criar um provedor. Um tópico relacionado, [como: implementar um observador](../../../docs/standard/events/how-to-implement-an-observer.md), descreve como criar um observador.  
  
### <a name="to-create-a-provider"></a>Para criar um provedor  
  
1.  Defina os dados que o provedor é responsável por enviar para observadores. Embora o provedor e os dados que ele envia para observadores podem ser um único tipo, elas geralmente são representadas por diferentes tipos. Por exemplo, em uma temperatura de monitoramento do aplicativo, o `Temperature` estrutura define os dados que o provedor (que é representado pela `TemperatureMonitor` classe definida na próxima etapa) monitora e quais observadores deseja assinar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  Definir o provedor de dados, que é um tipo que implementa o <xref:System.IObservable%601?displayProperty=nameWithType> interface. O argumento de tipo genérico do provedor é o tipo que o provedor envia a observadores. O exemplo a seguir define uma `TemperatureMonitor` classe, que é um construído <xref:System.IObservable%601?displayProperty=nameWithType> implementação com um argumento de tipo genérico de `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  Determine como o provedor armazena as referências a observadores para que cada observador pode ser notificado quando apropriado. Normalmente, um objeto de coleção como um genérico <xref:System.Collections.Generic.List%601> objeto é usado para essa finalidade. O exemplo a seguir define uma particular <xref:System.Collections.Generic.List%601> objeto é instanciado no `TemperatureMonitor` construtor de classe.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  Definir um <xref:System.IDisposable> implementação que o provedor pode retornar para os assinantes para que eles podem interromper o recebimento de notificações a qualquer momento. O exemplo a seguir define uma construção `Unsubscriber` classe que é passada uma referência à coleção de assinantes e ao assinante quando a classe é instanciada. Esse código permite que o assinante chamar o objeto <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementação para remover a mesmo da coleção de assinantes.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  Implementar o método de <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> . O método é passado uma referência para o <xref:System.IObserver%601?displayProperty=nameWithType> interface e deve ser armazenado no objeto criado para essa finalidade na etapa 3. O método deve retornar o <xref:System.IDisposable> implementação desenvolvido na etapa 4. O exemplo a seguir mostra a implementação do <xref:System.IObservable%601.Subscribe%2A> método o `TemperatureMonitor` classe.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  Notificar observadores conforme apropriado, chamando seus <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, e <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementações. Em alguns casos, um provedor não pode chamar o <xref:System.IObserver%601.OnError%2A> método quando ocorre um erro. Por exemplo, a seguinte `GetTemperature` método simula um monitor que lê dados de temperatura a cada cinco segundos e notifica observadores se a temperatura foi alterado pelo menos.1 grau desde a leitura anterior. Se o dispositivo não relata uma temperatura (ou seja, se o valor for nulo), o provedor notifica observadores que a transmissão foi concluída. Observe que, além de chamar cada observador <xref:System.IObserver%601.OnCompleted%2A> método, o `GetTemperature` método limpa o <xref:System.Collections.Generic.List%601> coleção. Nesse caso, o provedor não torna nenhuma chamada para o <xref:System.IObserver%601.OnError%2A> método seu observadores.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém o código-fonte completo para definir um <xref:System.IObservable%601> implementação para uma aplicativo de monitoramento de temperatura. Ele inclui o `Temperature` estrutura, os dados enviados para observadores, e o `TemperatureMonitor` classe, que é o <xref:System.IObservable%601> implementação.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IObservable%601>  
 [Padrão de design do observador](../../../docs/standard/events/observer-design-pattern.md)  
 [Como implementar um observador](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [Práticas recomendadas para o padrão de design do observador](../../../docs/standard/events/observer-design-pattern-best-practices.md)
