---
title: Implementando o padrão assíncrono baseado em evento
description: Saiba como implementar o padrão assíncrono baseado em evento (EAP) no .NET. O EAP é uma maneira padrão de empacotar uma classe que tem recursos assíncronos.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: ca4b1b3ff1fb7180250de7436db9a4d642e8118c
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888783"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="2728e-104">Implementando o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="2728e-104">Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="2728e-105">Se você estiver escrevendo uma classe com algumas operações que podem incorrer em atrasos perceptíveis, considere a possibilidade de fornecer funcionalidade assíncrona implementando o [padrão assíncrono baseado em evento](event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2728e-105">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing the [Event-based Asynchronous Pattern](event-based-asynchronous-pattern-overview.md).</span></span>

<span data-ttu-id="2728e-106">O Padrão assíncrono baseado em evento fornece uma maneira padronizada de empacotar uma classe que tem recursos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="2728e-106">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="2728e-107">Se for implementada com classes auxiliares como <xref:System.ComponentModel.AsyncOperationManager>, sua classe funcionará corretamente em qualquer modelo de aplicativo, incluindo ASP.NET, aplicativos de Console e aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2728e-107">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including ASP.NET, Console applications, and Windows Forms applications.</span></span>

<span data-ttu-id="2728e-108">Para obter um exemplo que implementa o Padrão assíncrono baseado em evento, consulte [Como implementar um componente compatível com o padrão assíncrono baseado em evento](component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2728e-108">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="2728e-109">Para operações assíncronas simples, você pode obter o componente <xref:System.ComponentModel.BackgroundWorker> adequado.</span><span class="sxs-lookup"><span data-stu-id="2728e-109">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="2728e-110">Para saber mais sobre <xref:System.ComponentModel.BackgroundWorker>, consulte [Como executar uma operação em segundo plano](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background).</span><span class="sxs-lookup"><span data-stu-id="2728e-110">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background).</span></span>

<span data-ttu-id="2728e-111">A lista a seguir descreve os recursos do padrão assíncrono baseado em evento discutidos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2728e-111">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>

- <span data-ttu-id="2728e-112">Oportunidades para a implementação do Padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="2728e-112">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

- <span data-ttu-id="2728e-113">Nomenclatura de métodos assíncronos</span><span class="sxs-lookup"><span data-stu-id="2728e-113">Naming Asynchronous Methods</span></span>

- <span data-ttu-id="2728e-114">Suporte opcional de cancelamento</span><span class="sxs-lookup"><span data-stu-id="2728e-114">Optionally Support Cancellation</span></span>

- <span data-ttu-id="2728e-115">Suporte opcional da propriedade IsBusy</span><span class="sxs-lookup"><span data-stu-id="2728e-115">Optionally Support the IsBusy Property</span></span>

- <span data-ttu-id="2728e-116">Fornecimento opcional de suporte para relatórios de progresso</span><span class="sxs-lookup"><span data-stu-id="2728e-116">Optionally Provide Support for Progress Reporting</span></span>

- <span data-ttu-id="2728e-117">Fornecimento opcional de suporte para retorno de resultados incrementais</span><span class="sxs-lookup"><span data-stu-id="2728e-117">Optionally Provide Support for Returning Incremental Results</span></span>

- <span data-ttu-id="2728e-118">Tratamento de parâmetros Out e Ref em métodos</span><span class="sxs-lookup"><span data-stu-id="2728e-118">Handling Out and Ref Parameters in Methods</span></span>

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="2728e-119">Oportunidades para a implementação do Padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="2728e-119">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="2728e-120">Considere a implementação do Padrão assíncrono baseado em evento quando:</span><span class="sxs-lookup"><span data-stu-id="2728e-120">Consider implementing the Event-based Asynchronous Pattern when:</span></span>

- <span data-ttu-id="2728e-121">Os clientes de sua classe não precisam de objetos <xref:System.Threading.WaitHandle> e <xref:System.IAsyncResult> disponíveis para operações assíncronas, ou seja, a sondagem e <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> deverão ser compilados pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="2728e-121">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>

- <span data-ttu-id="2728e-122">Você quer que as operações assíncronas sejam gerenciadas pelo cliente com o modelo de evento/delegado conhecido.</span><span class="sxs-lookup"><span data-stu-id="2728e-122">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>

<span data-ttu-id="2728e-123">Qualquer operação é candidata para uma implementação assíncrona, mas aquelas com expectativa de latência longas devem ser consideradas.</span><span class="sxs-lookup"><span data-stu-id="2728e-123">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="2728e-124">Operações nas quais os clientes chamam um método e são notificados após a conclusão, sem necessidade de intervenção adicional, são especialmente apropriadas.</span><span class="sxs-lookup"><span data-stu-id="2728e-124">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="2728e-125">Também são apropriadas as operações executadas continuamente, notificando periodicamente os clientes sobre o andamento, resultados incrementais ou alterações de estado.</span><span class="sxs-lookup"><span data-stu-id="2728e-125">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>

<span data-ttu-id="2728e-126">Para saber mais sobre como decidir pelo suporte ao Padrão assíncrono baseado em evento, confira [Decidir quando implementar o Padrão assíncrono baseado em evento](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2728e-126">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="naming-asynchronous-methods"></a><span data-ttu-id="2728e-127">Nomenclatura de métodos assíncronos</span><span class="sxs-lookup"><span data-stu-id="2728e-127">Naming Asynchronous Methods</span></span>

<span data-ttu-id="2728e-128">Para cada método síncrono *MethodName* para o qual você deseja fornecer uma contraparte assíncrona:</span><span class="sxs-lookup"><span data-stu-id="2728e-128">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>

<span data-ttu-id="2728e-129">Defina um método _MethodName_**Async** que:</span><span class="sxs-lookup"><span data-stu-id="2728e-129">Define a _MethodName_**Async** method that:</span></span>

- <span data-ttu-id="2728e-130">Retorna `void`.</span><span class="sxs-lookup"><span data-stu-id="2728e-130">Returns `void`.</span></span>

- <span data-ttu-id="2728e-131">Usa os mesmos parâmetros que o método *MethodName* .</span><span class="sxs-lookup"><span data-stu-id="2728e-131">Takes the same parameters as the *MethodName* method.</span></span>

- <span data-ttu-id="2728e-132">Aceita várias invocações.</span><span class="sxs-lookup"><span data-stu-id="2728e-132">Accepts multiple invocations.</span></span>

<span data-ttu-id="2728e-133">Opcionalmente, defina uma sobrecarga _MethodName_**Async** , idêntica ao _MethodName_**Async** , mas com um parâmetro adicional com valor de objeto chamado `userState`.</span><span class="sxs-lookup"><span data-stu-id="2728e-133">Optionally define a _MethodName_**Async** overload, identical to _MethodName_**Async** , but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="2728e-134">Faça isso se você estiver preparado para gerenciar várias chamadas simultâneas de seu método. Nesse caso, o valor `userState` será entregue novamente para todos os manipuladores de eventos a fim de distinguir invocações do método.</span><span class="sxs-lookup"><span data-stu-id="2728e-134">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="2728e-135">Você também pode optar por fazer isso simplesmente como um local para armazenar o estado do usuário para recuperação posterior.</span><span class="sxs-lookup"><span data-stu-id="2728e-135">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>

<span data-ttu-id="2728e-136">Para cada assinatura de método _MethodName_**Async** separada:</span><span class="sxs-lookup"><span data-stu-id="2728e-136">For each separate _MethodName_**Async** method signature:</span></span>

1. <span data-ttu-id="2728e-137">Defina o evento a seguir na mesma classe que o método:</span><span class="sxs-lookup"><span data-stu-id="2728e-137">Define the following event in the same class as the method:</span></span>

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. <span data-ttu-id="2728e-138">Defina o representante a seguir e <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2728e-138">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="2728e-139">Provavelmente, eles serão definidos fora da própria classe, mas no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="2728e-139">These will likely be defined outside of the class itself, but in the same namespace.</span></span>

    ```vb
    Public Delegate Sub MethodNameCompletedEventHandler( _
        ByVal sender As Object, _
        ByVal e As MethodNameCompletedEventArgs)

    Public Class MethodNameCompletedEventArgs
        Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As MyReturnType
    End Property
    ```

    ```csharp
    public delegate void MethodNameCompletedEventHandler(object sender,
        MethodNameCompletedEventArgs e);

    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
    {
        public MyReturnType Result { get; }
    }
    ```

    - <span data-ttu-id="2728e-140">Certifique-se de que a classe _MethodName_**CompletedEventArgs** expõe seus membros como propriedades somente leitura, e não como campos, pois os campos impedem a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="2728e-140">Ensure that the _MethodName_**CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>

    - <span data-ttu-id="2728e-141">Não defina qualquer classe derivada de <xref:System.ComponentModel.AsyncCompletedEventArgs> para métodos que não produzem resultados.</span><span class="sxs-lookup"><span data-stu-id="2728e-141">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="2728e-142">Simplesmente use uma instância do próprio <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2728e-142">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>

      > [!NOTE]
      > <span data-ttu-id="2728e-143">É perfeitamente aceitável, quando apropriada e plausível, a reutilização de delegados e tipos <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2728e-143">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="2728e-144">Nesse caso, a nomenclatura não será consistente com o nome do método, pois um delegado e <xref:System.ComponentModel.AsyncCompletedEventArgs> específicos não ficarão vinculados a um único método.</span><span class="sxs-lookup"><span data-stu-id="2728e-144">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>

## <a name="optionally-support-cancellation"></a><span data-ttu-id="2728e-145">Suporte opcional de cancelamento</span><span class="sxs-lookup"><span data-stu-id="2728e-145">Optionally Support Cancellation</span></span>

<span data-ttu-id="2728e-146">Se sua classe oferecer suporte ao cancelamento de operações assíncronas, o cancelamento deverá ser exposto ao cliente, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="2728e-146">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="2728e-147">Perceba que há dois pontos de decisão que precisam ser alcançados antes de definir o suporte ao cancelamento:</span><span class="sxs-lookup"><span data-stu-id="2728e-147">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>

- <span data-ttu-id="2728e-148">Sua classe, incluindo acréscimos futuros antecipados, tem apenas uma operação assíncrona que oferece suporte ao cancelamento?</span><span class="sxs-lookup"><span data-stu-id="2728e-148">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>

- <span data-ttu-id="2728e-149">As operações assíncronas que oferecem suporte ao cancelamento podem dar suporte a várias operações pendentes?</span><span class="sxs-lookup"><span data-stu-id="2728e-149">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="2728e-150">Ou seja, o método _MethodName_**Async** usa um parâmetro `userState` e ele permite várias invocações antes da conclusão de alguma?</span><span class="sxs-lookup"><span data-stu-id="2728e-150">That is, does the _MethodName_**Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>

<span data-ttu-id="2728e-151">Use as respostas para essas duas perguntas na tabela abaixo para determinar qual deve ser a assinatura para o método de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="2728e-151">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="2728e-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2728e-152">Visual Basic</span></span>

||<span data-ttu-id="2728e-153">Várias operações simultâneas com suporte</span><span class="sxs-lookup"><span data-stu-id="2728e-153">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="2728e-154">Apenas uma operação por vez</span><span class="sxs-lookup"><span data-stu-id="2728e-154">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="2728e-155">Uma operação assíncrona em toda a classe</span><span class="sxs-lookup"><span data-stu-id="2728e-155">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|<span data-ttu-id="2728e-156">Várias operações assíncronas em classe</span><span class="sxs-lookup"><span data-stu-id="2728e-156">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a><span data-ttu-id="2728e-157">C\#</span><span class="sxs-lookup"><span data-stu-id="2728e-157">C\#</span></span>

||<span data-ttu-id="2728e-158">Várias operações simultâneas com suporte</span><span class="sxs-lookup"><span data-stu-id="2728e-158">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="2728e-159">Apenas uma operação por vez</span><span class="sxs-lookup"><span data-stu-id="2728e-159">Only One Operation at a Time</span></span>|
|------|------------------------------------------------|----------------------------------|
|<span data-ttu-id="2728e-160">Uma operação assíncrona em toda a classe</span><span class="sxs-lookup"><span data-stu-id="2728e-160">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|<span data-ttu-id="2728e-161">Várias operações assíncronas em classe</span><span class="sxs-lookup"><span data-stu-id="2728e-161">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|

<span data-ttu-id="2728e-162">Se você definir o método `CancelAsync(object userState)`, os clientes deverão ter cuidado ao escolher seus valores de estado a fim de torná-los capazes de distinguir entre todos os métodos assíncronos invocados no objeto, e não apenas entre todas as invocações de um único método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="2728e-162">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>

<span data-ttu-id="2728e-163">A decisão de nomear a versão de operação assíncrona única _MethodName_**AsyncCancel** tem base em ser capaz de descobrir mais facilmente o método em um ambiente de design como IntelliSense do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2728e-163">The decision to name the single-async-operation version _MethodName_**AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="2728e-164">Isso agrupa os membros relacionados e os distingue de outros membros que não têm qualquer relação com funcionalidade assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2728e-164">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="2728e-165">Se você espera que outras operações assíncronas sejam adicionadas em versões subsequentes, é melhor definir `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="2728e-165">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>

<span data-ttu-id="2728e-166">Não defina vários métodos da tabela acima na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="2728e-166">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="2728e-167">Isso não fará sentido, ou sobrecarregará a interface de classe com a proliferação de métodos.</span><span class="sxs-lookup"><span data-stu-id="2728e-167">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>

<span data-ttu-id="2728e-168">Normalmente, esses métodos retornarão imediatamente, e a operação poderá ou não ser realmente cancelada.</span><span class="sxs-lookup"><span data-stu-id="2728e-168">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="2728e-169">No manipulador de eventos do evento _MethodName_**Completed** , o objeto _MethodName_**CompletedEventArgs** contém um campo `Cancelled`, o qual os clientes podem usar para determinar se o cancelamento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="2728e-169">In the event handler for the _MethodName_**Completed** event, the _MethodName_**CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>

<span data-ttu-id="2728e-170">Obedeça à semântica de cancelamento descrita em [Melhores práticas para implementar o Padrão assíncrono baseado em evento](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2728e-170">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="2728e-171">Suporte opcional da propriedade IsBusy</span><span class="sxs-lookup"><span data-stu-id="2728e-171">Optionally Support the IsBusy Property</span></span>

<span data-ttu-id="2728e-172">Se sua classe não oferecer suporte a várias invocações simultâneas, considere a exposição de uma propriedade `IsBusy`.</span><span class="sxs-lookup"><span data-stu-id="2728e-172">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="2728e-173">Isso permite que os desenvolvedores determinem se um método _MethodName_**Async** está sendo executado sem capturar uma exceção do método _MethodName_**Async** .</span><span class="sxs-lookup"><span data-stu-id="2728e-173">This allows developers to determine whether a _MethodName_**Async** method is running without catching an exception from the _MethodName_**Async** method.</span></span>

<span data-ttu-id="2728e-174">Obedeça à semântica `IsBusy` descrita em [Melhores práticas para implementar o Padrão assíncrono baseado em evento](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2728e-174">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="2728e-175">Fornecimento opcional de suporte para relatórios de progresso</span><span class="sxs-lookup"><span data-stu-id="2728e-175">Optionally Provide Support for Progress Reporting</span></span>

<span data-ttu-id="2728e-176">Costuma ser bom relatar o progresso durante uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2728e-176">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="2728e-177">O padrão assíncrono baseado em evento fornece uma orientação para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="2728e-177">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>

- <span data-ttu-id="2728e-178">Opcionalmente, defina um evento que será gerado pela operação assíncrona e invocado no thread apropriado.</span><span class="sxs-lookup"><span data-stu-id="2728e-178">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="2728e-179">O objeto <xref:System.ComponentModel.ProgressChangedEventArgs> transporta um indicador de progresso com valor de inteiro que deve estar entre 0 e 100.</span><span class="sxs-lookup"><span data-stu-id="2728e-179">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>

- <span data-ttu-id="2728e-180">Nomeie esse evento da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2728e-180">Name this event as follows:</span></span>

  - <span data-ttu-id="2728e-181">`ProgressChanged` se a classe tiver várias operações assíncronas (ou exista a expectativa de crescimento a fim de incluir várias operações assíncronas em versões futuras);</span><span class="sxs-lookup"><span data-stu-id="2728e-181">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>

  - <span data-ttu-id="2728e-182">_MethodName_**ProgressChanged** se a classe tiver uma única operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="2728e-182">_MethodName_**ProgressChanged** if the class has a single asynchronous operation.</span></span>

  <span data-ttu-id="2728e-183">Essa opção de nomenclatura é comparável à feita para o método de cancelamento, conforme descrito na seção Suporte opcional de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="2728e-183">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>

<span data-ttu-id="2728e-184">Esse evento deve usar a assinatura do delegado <xref:System.ComponentModel.ProgressChangedEventHandler> e a classe <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2728e-184">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="2728e-185">Como alternativa, se um indicador de progresso mais específico ao domínio puder ser fornecido (por exemplo, bytes lidos e total de bytes de uma operação de download), você deverá definir uma classe derivada de <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2728e-185">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>

<span data-ttu-id="2728e-186">Observe que há apenas um `ProgressChanged` ou _MethodName_ evento **ProgressChanged** para a classe, independentemente do número de métodos assíncronos com suporte.</span><span class="sxs-lookup"><span data-stu-id="2728e-186">Note that there is only one `ProgressChanged` or _MethodName_**ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="2728e-187">Os clientes devem usar o objeto `userState` que é passado para os métodos _MethodName_**Async** a fim de distinguir entre as atualizações de andamento em várias operações simultâneas.</span><span class="sxs-lookup"><span data-stu-id="2728e-187">Clients are expected to use the `userState` object that is passed to the _MethodName_**Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>

<span data-ttu-id="2728e-188">Pode haver situações em que várias operações dão suporte ao progresso e cada uma retorna um indicador diferente para o progresso.</span><span class="sxs-lookup"><span data-stu-id="2728e-188">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="2728e-189">Nesse caso, um único `ProgressChanged` evento não é apropriado, e você pode considerar o suporte a vários eventos `ProgressChanged`.</span><span class="sxs-lookup"><span data-stu-id="2728e-189">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="2728e-190">Nesse caso, use um padrão de nomenclatura de _MethodName_**ProgressChanged** para cada método _MethodName_**Async** .</span><span class="sxs-lookup"><span data-stu-id="2728e-190">In this case use a naming pattern of _MethodName_**ProgressChanged** for each _MethodName_**Async** method.</span></span>

<span data-ttu-id="2728e-191">Obedeça à semântica de relatório de progresso descrita em [Melhores práticas para implementar o Padrão assíncrono baseado em evento](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2728e-191">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="2728e-192">Fornecimento opcional de suporte para retorno de resultados incrementais</span><span class="sxs-lookup"><span data-stu-id="2728e-192">Optionally Provide Support for Returning Incremental Results</span></span>

<span data-ttu-id="2728e-193">Às vezes, uma operação assíncrona pode retornar resultados incrementais antes da conclusão.</span><span class="sxs-lookup"><span data-stu-id="2728e-193">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="2728e-194">Há várias opções que podem ser usadas para oferecer suporte a esse cenário.</span><span class="sxs-lookup"><span data-stu-id="2728e-194">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="2728e-195">Veja a seguir alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="2728e-195">Some examples follow.</span></span>

### <a name="single-operation-class"></a><span data-ttu-id="2728e-196">Classe de operação única</span><span class="sxs-lookup"><span data-stu-id="2728e-196">Single-operation Class</span></span>

<span data-ttu-id="2728e-197">Se sua classe der suporte apenas a uma única operação assíncrona, e essa operação for capaz de retornar resultados incrementais, então:</span><span class="sxs-lookup"><span data-stu-id="2728e-197">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>

- <span data-ttu-id="2728e-198">Estenda o tipo <xref:System.ComponentModel.ProgressChangedEventArgs> para carregar os dados de resultado incrementais e definir um evento _MethodName_**ProgressChanged** com esses dados estendidos.</span><span class="sxs-lookup"><span data-stu-id="2728e-198">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a _MethodName_**ProgressChanged** event with this extended data.</span></span>

- <span data-ttu-id="2728e-199">Gere esse evento _MethodName_**ProgressChanged** quando houver um resultado incremental para o relatório.</span><span class="sxs-lookup"><span data-stu-id="2728e-199">Raise this _MethodName_**ProgressChanged** event when there is an incremental result to report.</span></span>

<span data-ttu-id="2728e-200">Essa solução aplica-se especificamente a uma classe de operação assíncrona única, pois não há nenhum problema com o mesmo evento ocorrendo para retornar resultados incrementais em "todas as operações", como faz o evento _MethodName_**ProgressChanged** .</span><span class="sxs-lookup"><span data-stu-id="2728e-200">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the _MethodName_**ProgressChanged** event does.</span></span>

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="2728e-201">Classe de várias operações com resultados incrementais homogêneos</span><span class="sxs-lookup"><span data-stu-id="2728e-201">Multiple-operation Class with Homogeneous Incremental Results</span></span>

<span data-ttu-id="2728e-202">Nesse caso, sua classe oferece suporte a vários métodos assíncronos, cada um capaz de retornar resultados incrementais, e todos esses resultados incrementais têm o mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="2728e-202">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>

<span data-ttu-id="2728e-203">Siga o modelo descrito acima para classes de operação única, pois a mesma estrutura <xref:System.EventArgs> funcionará para todos os resultados incrementais.</span><span class="sxs-lookup"><span data-stu-id="2728e-203">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="2728e-204">Defina um evento `ProgressChanged` em vez de um evento _MethodName_**ProgressChanged** , já que ele se aplica a vários métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="2728e-204">Define a `ProgressChanged` event instead of a _MethodName_**ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="2728e-205">Classe de várias operações com resultados incrementais heterogêneos</span><span class="sxs-lookup"><span data-stu-id="2728e-205">Multiple-operation Class with Heterogeneous Incremental Results</span></span>

<span data-ttu-id="2728e-206">Se sua classe oferece suporte a vários métodos assíncronos, cada um retornando um tipo diferente de dados, você deve:</span><span class="sxs-lookup"><span data-stu-id="2728e-206">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>

- <span data-ttu-id="2728e-207">Separar o relatório de resultado incremental de seu relatório de progresso.</span><span class="sxs-lookup"><span data-stu-id="2728e-207">Separate your incremental result reporting from your progress reporting.</span></span>

- <span data-ttu-id="2728e-208">Definir um evento _MethodName_**ProgressChanged** separado com o <xref:System.EventArgs> apropriado para cada método assíncrono manipular dados de resultados incrementais desse método.</span><span class="sxs-lookup"><span data-stu-id="2728e-208">Define a separate _MethodName_**ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>

<span data-ttu-id="2728e-209">Invocar esse manipulador de eventos no thread apropriado, conforme descrito em [Melhores práticas para implementar o Padrão assíncrono baseado em evento](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2728e-209">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="2728e-210">Tratamento de parâmetros Out e Ref em métodos</span><span class="sxs-lookup"><span data-stu-id="2728e-210">Handling Out and Ref Parameters in Methods</span></span>

<span data-ttu-id="2728e-211">Embora o uso de `out` e `ref` seja, em geral, desencorajado no .net, aqui estão as regras a serem seguidas quando estiverem presentes:</span><span class="sxs-lookup"><span data-stu-id="2728e-211">Although the use of `out` and `ref` is, in general, discouraged in .NET, here are the rules to follow when they are present:</span></span>

<span data-ttu-id="2728e-212">Em um método síncrono *MethodName* :</span><span class="sxs-lookup"><span data-stu-id="2728e-212">Given a synchronous method *MethodName* :</span></span>

- <span data-ttu-id="2728e-213">`out` os parâmetros para *MethodName* não devem fazer parte de _MethodName_**Async** .</span><span class="sxs-lookup"><span data-stu-id="2728e-213">`out` parameters to *MethodName* should not be part of _MethodName_**Async** .</span></span> <span data-ttu-id="2728e-214">Em vez disso, eles devem fazer parte de _MethodName_**CompletedEventArgs** com o mesmo nome que seu parâmetro equivalente em *MethodName* (a menos que haja um nome mais apropriado).</span><span class="sxs-lookup"><span data-stu-id="2728e-214">Instead, they should be part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

- <span data-ttu-id="2728e-215">`ref` os parâmetros *para MethodName* devem aparecer como parte _de MethodName_**Async** e como parte de _MethodName_**CompletedEventArgs** com o mesmo nome que seu parâmetro equivalente em *MethodName* (a menos que haja um nome mais apropriado).</span><span class="sxs-lookup"><span data-stu-id="2728e-215">`ref` parameters to *MethodName* should appear as part of _MethodName_**Async** , and as part of _MethodName_**CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>

<span data-ttu-id="2728e-216">Por exemplo, considerando que:</span><span class="sxs-lookup"><span data-stu-id="2728e-216">For example, given:</span></span>

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

<span data-ttu-id="2728e-217">Seu método assíncrono e sua classe <xref:System.ComponentModel.AsyncCompletedEventArgs> teria esta aparência:</span><span class="sxs-lookup"><span data-stu-id="2728e-217">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>

```vb
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)

Public Class MethodNameCompletedEventArgs
    Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As Integer
    End Property
    Public ReadOnly Property Arg2() As String
    End Property
    Public ReadOnly Property Arg3() As String
    End Property
End Class
```

```csharp
public void MethodNameAsync(string arg1, string arg2);

public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
{
    public int Result { get; };
    public string Arg2 { get; };
    public string Arg3 { get; };
}
```

## <a name="see-also"></a><span data-ttu-id="2728e-218">Veja também</span><span class="sxs-lookup"><span data-stu-id="2728e-218">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="2728e-219">Como: Implementar um componente compatível com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="2728e-219">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="2728e-220">Como: Executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="2728e-220">How to: Run an Operation in the Background</span></span>](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [<span data-ttu-id="2728e-221">Como: Implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="2728e-221">How to: Implement a Form That Uses a Background Operation</span></span>](/dotnet/desktop/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation)
- [<span data-ttu-id="2728e-222">Decidindo quando implementar o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="2728e-222">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="2728e-223">Práticas recomendadas para a implementação do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="2728e-223">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="2728e-224">Padrão assíncrono baseado em evento (EAP)</span><span class="sxs-lookup"><span data-stu-id="2728e-224">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
