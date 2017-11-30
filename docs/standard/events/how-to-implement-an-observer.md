---
title: Como implementar um observador
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
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a964bd031f6f8a7fc029b2b209b9693b72e688af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-observer"></a>Como implementar um observador
O padrão de design do observador requer uma divisão entre um observador, que registra para notificações, e um provedor, que monitora os dados e envia notificações para um ou mais observadores. Este tópico discute como criar um observador. Um tópico relacionado, [como: implementar um provedor](../../../docs/standard/events/how-to-implement-a-provider.md), descreve como criar um provedor.  
  
### <a name="to-create-an-observer"></a>Para criar um observador  
  
1.  Definir o observador, o que é um tipo que implementa o <xref:System.IObserver%601?displayProperty=nameWithType> interface. Por exemplo, o código a seguir define um tipo chamado `TemperatureReporter` que é um construído <xref:System.IObserver%601?displayProperty=nameWithType> implementação com um argumento de tipo genérico de `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  Se o observador pode interromper o recebimento de notificações antes de chamar o provedor seu <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementação, definir uma variável privada que armazenará o <xref:System.IDisposable> implementação retornada pelo provedor de <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> método. Você também deve definir um método de assinatura que chama o provedor <xref:System.IObservable%601.Subscribe%2A> método e repositórios retornados <xref:System.IDisposable> objeto. Por exemplo, o código a seguir define uma variável particular chamada `unsubscriber` e define uma `Subscribe` método que chama o provedor <xref:System.IObservable%601.Subscribe%2A> método e atribui o objeto retornado para o `unsubscriber` variável.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  Definir um método que permite que o observador interromper o recebimento de notificações antes de chamar o provedor seu <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementação, se esse recurso é necessário. O exemplo a seguir define um `Unsubscribe` método.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  Fornecer implementações dos três métodos definidos pelo <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, e <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Dependendo do provedor e as necessidades do aplicativo, o <xref:System.IObserver%601.OnError%2A> e <xref:System.IObserver%601.OnCompleted%2A> métodos podem ser implementações de stub. Observe que o <xref:System.IObserver%601.OnError%2A> método não deve tratar transmitido <xref:System.Exception> objeto como uma exceção e o <xref:System.IObserver%601.OnCompleted%2A> método é livre para chamar o provedor <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementação. A exemplo a seguir mostra o <xref:System.IObserver%601> implementação de `TemperatureReporter` classe.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém o código-fonte completo para o `TemperatureReporter` classe, que fornece o <xref:System.IObserver%601> implementação para uma aplicativo de monitoramento de temperatura.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IObserver%601>  
 [Padrão de design do observador](../../../docs/standard/events/observer-design-pattern.md)  
 [Como implementar um provedor](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [Práticas recomendadas para o padrão de design do observador](../../../docs/standard/events/observer-design-pattern-best-practices.md)
