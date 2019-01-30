---
title: 'Como: Implementar um observador'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b7534843c1f724dc4544b9a5a7062e79e973a34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738047"
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="483eb-102">Como: Implementar um observador</span><span class="sxs-lookup"><span data-stu-id="483eb-102">How to: Implement an Observer</span></span>
<span data-ttu-id="483eb-103">O padrão de design do observador exige uma divisão entre um observador, que registra as notificações, e um provedor, que monitora os dados e envia notificações e um ou mais observadores.</span><span class="sxs-lookup"><span data-stu-id="483eb-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="483eb-104">Este tópico discute como criar um observador.</span><span class="sxs-lookup"><span data-stu-id="483eb-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="483eb-105">Um tópico relacionado, [Como: Implementar um provedor](../../../docs/standard/events/how-to-implement-a-provider.md), descreve como criar um provedor.</span><span class="sxs-lookup"><span data-stu-id="483eb-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="483eb-106">Para criar um observador</span><span class="sxs-lookup"><span data-stu-id="483eb-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="483eb-107">Defina o observador, que é um tipo que implementa a interface <xref:System.IObserver%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="483eb-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="483eb-108">Por exemplo, o código a seguir define um tipo chamado `TemperatureReporter`, que é uma implementação <xref:System.IObserver%601?displayProperty=nameWithType> construída com um argumento de tipo genérico de `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="483eb-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="483eb-109">Se o observador puder interromper o recebimento de notificações antes de o provedor chamar sua implementação de <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, defina uma variável privada que armazenará a implementação de <xref:System.IDisposable> retornada pelo método <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> do provedor.</span><span class="sxs-lookup"><span data-stu-id="483eb-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="483eb-110">Você também deve definir um método de assinatura que chama o método <xref:System.IObservable%601.Subscribe%2A> do provedor e armazena o objeto <xref:System.IDisposable> retornado.</span><span class="sxs-lookup"><span data-stu-id="483eb-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="483eb-111">Por exemplo, o código a seguir define uma variável privada chamada `unsubscriber`, e define um método `Subscribe` que chama o método <xref:System.IObservable%601.Subscribe%2A> do provedor e atribui o objeto retornado à variável `unsubscriber`.</span><span class="sxs-lookup"><span data-stu-id="483eb-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="483eb-112">Defina um método que permite ao observador interromper o recebimento de notificações antes de o provedor chamar sua implementação de <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, se esse recurso for necessário.</span><span class="sxs-lookup"><span data-stu-id="483eb-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="483eb-113">O exemplo a seguir define um método `Unsubscribe`.</span><span class="sxs-lookup"><span data-stu-id="483eb-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="483eb-114">Forneça implementações dos três métodos definidos pela interface <xref:System.IObserver%601>: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> e <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="483eb-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="483eb-115">Dependendo do provedor e das necessidades do aplicativo, os métodos <xref:System.IObserver%601.OnError%2A> e <xref:System.IObserver%601.OnCompleted%2A> podem ser implementações de stub.</span><span class="sxs-lookup"><span data-stu-id="483eb-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="483eb-116">Observe que o método <xref:System.IObserver%601.OnError%2A> não deve tratar do objeto <xref:System.Exception> transmitido como uma exceção, e o método <xref:System.IObserver%601.OnCompleted%2A> é livre para chamar a implementação <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> do provedor.</span><span class="sxs-lookup"><span data-stu-id="483eb-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="483eb-117">O exemplo a seguir mostra a implementação <xref:System.IObserver%601> da classe `TemperatureReporter`.</span><span class="sxs-lookup"><span data-stu-id="483eb-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="483eb-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="483eb-118">Example</span></span>  
 <span data-ttu-id="483eb-119">O exemplo a seguir contém o código-fonte completo para a classe `TemperatureReporter`, que fornece a implementação <xref:System.IObserver%601> para uma aplicativo de monitoramento de temperatura.</span><span class="sxs-lookup"><span data-stu-id="483eb-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="483eb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="483eb-120">See also</span></span>

- <xref:System.IObserver%601>
- [<span data-ttu-id="483eb-121">Padrão de design do observador</span><span class="sxs-lookup"><span data-stu-id="483eb-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)
- [<span data-ttu-id="483eb-122">Como: Implementar um provedor</span><span class="sxs-lookup"><span data-stu-id="483eb-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)
- [<span data-ttu-id="483eb-123">Práticas recomendadas para o padrão de design do observador</span><span class="sxs-lookup"><span data-stu-id="483eb-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
