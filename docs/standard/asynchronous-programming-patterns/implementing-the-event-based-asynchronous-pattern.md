---
title: Implementando o padrão assíncrono baseado em evento
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c503b89c63d976fe6304291aa1157765fa5c6f7
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="e4b3a-102">Implementando o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="e4b3a-103">Se você estiver escrevendo uma classe com algumas operações que possam causar atrasos notáveis, considere a opção de fornecer funcionalidade assíncrona Implementando a [Visão geral de padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="e4b3a-104">O Padrão assíncrono baseado em evento fornece uma maneira padronizada de empacotar uma classe que tem recursos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="e4b3a-105">Se for implementada com classes auxiliares como <xref:System.ComponentModel.AsyncOperationManager>, sua classe funcionará corretamente em qualquer modelo de aplicativo, incluindo [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplicativos de Console e aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="e4b3a-106">Para obter um exemplo que implementa o Padrão assíncrono baseado em evento, consulte [Como implementar um componente compatível com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="e4b3a-107">Para operações assíncronas simples, você pode obter o componente <xref:System.ComponentModel.BackgroundWorker> adequado.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="e4b3a-108">Para saber mais sobre <xref:System.ComponentModel.BackgroundWorker>, consulte [Como executar uma operação em segundo plano](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="e4b3a-109">A lista a seguir descreve os recursos do padrão assíncrono baseado em evento discutidos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="e4b3a-110">Oportunidades para a implementação do Padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="e4b3a-111">Nomenclatura de métodos assíncronos</span><span class="sxs-lookup"><span data-stu-id="e4b3a-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="e4b3a-112">Suporte opcional de cancelamento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="e4b3a-113">Suporte opcional da propriedade IsBusy</span><span class="sxs-lookup"><span data-stu-id="e4b3a-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="e4b3a-114">Fornecimento opcional de suporte para relatórios de progresso</span><span class="sxs-lookup"><span data-stu-id="e4b3a-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="e4b3a-115">Fornecimento opcional de suporte para retorno de resultados incrementais</span><span class="sxs-lookup"><span data-stu-id="e4b3a-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="e4b3a-116">Tratamento de parâmetros Out e Ref em métodos</span><span class="sxs-lookup"><span data-stu-id="e4b3a-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="e4b3a-117">Oportunidades para a implementação do Padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="e4b3a-118">Considere a implementação do Padrão assíncrono baseado em evento quando:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="e4b3a-119">Os clientes de sua classe não precisam de objetos <xref:System.Threading.WaitHandle> e <xref:System.IAsyncResult> disponíveis para operações assíncronas, ou seja, a sondagem e <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> deverão ser compilados pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="e4b3a-120">Você quer que as operações assíncronas sejam gerenciadas pelo cliente com o modelo de evento/delegado conhecido.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="e4b3a-121">Qualquer operação é candidata para uma implementação assíncrona, mas aquelas com expectativa de latência longas devem ser consideradas.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="e4b3a-122">Operações nas quais os clientes chamam um método e são notificados após a conclusão, sem necessidade de intervenção adicional, são especialmente apropriadas.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="e4b3a-123">Também são apropriadas as operações executadas continuamente, notificando periodicamente os clientes sobre o andamento, resultados incrementais ou alterações de estado.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="e4b3a-124">Para saber mais sobre como decidir pelo suporte ao Padrão assíncrono baseado em evento, confira [Decidir quando implementar o Padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="e4b3a-125">Nomenclatura de métodos assíncronos</span><span class="sxs-lookup"><span data-stu-id="e4b3a-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="e4b3a-126">Para cada método síncrono *MethodName* para o qual você deseja fornecer uma contraparte assíncrona:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="e4b3a-127">Defina um método *MethodName***Async** que:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-127">Define a *MethodName***Async** method that:</span></span>  
  
-   <span data-ttu-id="e4b3a-128">Retorna `void`.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="e4b3a-129">Usa os mesmos parâmetros que o método *MethodName*.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="e4b3a-130">Aceita várias invocações.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="e4b3a-131">Opcionalmente, defina uma sobrecarga *MethodName***Async**, idêntica ao *MethodName***Async**, mas com um parâmetro adicional com valor de objeto chamado `userState`.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-131">Optionally define a *MethodName***Async** overload, identical to *MethodName***Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="e4b3a-132">Faça isso se você estiver preparado para gerenciar várias chamadas simultâneas de seu método. Nesse caso, o valor `userState` será entregue novamente para todos os manipuladores de eventos a fim de distinguir invocações do método.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="e4b3a-133">Você também pode optar por fazer isso simplesmente como um local para armazenar o estado do usuário para recuperação posterior.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="e4b3a-134">Para cada assinatura de método *MethodName***Async** separada:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-134">For each separate *MethodName***Async** method signature:</span></span>  
  
1.  <span data-ttu-id="e4b3a-135">Defina o evento a seguir na mesma classe que o método:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="e4b3a-136">Defina o representante a seguir e <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="e4b3a-137">Provavelmente, eles serão definidos fora da própria classe, mas no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
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
  
    -   <span data-ttu-id="e4b3a-138">Certifique-se de que a classe *MethodName***CompletedEventArgs** expõe seus membros como propriedades somente leitura, e não como campos, pois os campos impedem a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-138">Ensure that the *MethodName***CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="e4b3a-139">Não defina qualquer classe derivada de <xref:System.ComponentModel.AsyncCompletedEventArgs> para métodos que não produzem resultados.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="e4b3a-140">Simplesmente use uma instância do próprio <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e4b3a-141">É perfeitamente aceitável, quando apropriada e plausível, a reutilização de delegados e tipos <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="e4b3a-142">Nesse caso, a nomenclatura não será consistente com o nome do método, pois um delegado e <xref:System.ComponentModel.AsyncCompletedEventArgs> específicos não ficarão vinculados a um único método.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="e4b3a-143">Suporte opcional de cancelamento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="e4b3a-144">Se sua classe oferecer suporte ao cancelamento de operações assíncronas, o cancelamento deverá ser exposto ao cliente, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="e4b3a-145">Perceba que há dois pontos de decisão que precisam ser alcançados antes de definir o suporte ao cancelamento:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="e4b3a-146">Sua classe, incluindo acréscimos futuros antecipados, tem apenas uma operação assíncrona que oferece suporte ao cancelamento?</span><span class="sxs-lookup"><span data-stu-id="e4b3a-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="e4b3a-147">As operações assíncronas que oferecem suporte ao cancelamento podem dar suporte a várias operações pendentes?</span><span class="sxs-lookup"><span data-stu-id="e4b3a-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="e4b3a-148">Ou seja, o método *MethodName***Async** usa um parâmetro `userState`, e permite várias invocações antes da conclusão de alguma?</span><span class="sxs-lookup"><span data-stu-id="e4b3a-148">That is, does the *MethodName***Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="e4b3a-149">Use as respostas para essas duas perguntas na tabela abaixo para determinar qual deve ser a assinatura para o método de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="e4b3a-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4b3a-150">Visual Basic</span></span>  
  
||<span data-ttu-id="e4b3a-151">Várias operações simultâneas com suporte</span><span class="sxs-lookup"><span data-stu-id="e4b3a-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="e4b3a-152">Apenas uma operação por vez</span><span class="sxs-lookup"><span data-stu-id="e4b3a-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="e4b3a-153">Uma operação assíncrona em toda a classe</span><span class="sxs-lookup"><span data-stu-id="e4b3a-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="e4b3a-154">Várias operações assíncronas em classe</span><span class="sxs-lookup"><span data-stu-id="e4b3a-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="e4b3a-155">C#</span><span class="sxs-lookup"><span data-stu-id="e4b3a-155">C#</span></span>  
  
||<span data-ttu-id="e4b3a-156">Várias operações simultâneas com suporte</span><span class="sxs-lookup"><span data-stu-id="e4b3a-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="e4b3a-157">Apenas uma operação por vez</span><span class="sxs-lookup"><span data-stu-id="e4b3a-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="e4b3a-158">Uma operação assíncrona em toda a classe</span><span class="sxs-lookup"><span data-stu-id="e4b3a-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="e4b3a-159">Várias operações assíncronas em classe</span><span class="sxs-lookup"><span data-stu-id="e4b3a-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="e4b3a-160">Se você definir o método `CancelAsync(object userState)`, os clientes deverão ter cuidado ao escolher seus valores de estado a fim de torná-los capazes de distinguir entre todos os métodos assíncronos invocados no objeto, e não apenas entre todas as invocações de um único método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="e4b3a-161">A decisão de nomear a versão de operação assíncrona única *MethodName***AsyncCancel** tem base em ser capaz de descobrir mais facilmente o método em um ambiente de design como IntelliSense do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-161">The decision to name the single-async-operation version *MethodName***AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="e4b3a-162">Isso agrupa os membros relacionados e os distingue de outros membros que não têm qualquer relação com funcionalidade assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="e4b3a-163">Se você espera que outras operações assíncronas sejam adicionadas em versões subsequentes, é melhor definir `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="e4b3a-164">Não defina vários métodos da tabela acima na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="e4b3a-165">Isso não fará sentido, ou sobrecarregará a interface de classe com a proliferação de métodos.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="e4b3a-166">Normalmente, esses métodos retornarão imediatamente, e a operação poderá ou não ser realmente cancelada.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="e4b3a-167">No manipulador de eventos do evento *MethodName***Completed**, o objeto *MethodName***CompletedEventArgs** contém um campo `Cancelled`, o qual os clientes podem usar para determinar se o cancelamento ocorreu.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-167">In the event handler for the *MethodName***Completed** event, the *MethodName***CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="e4b3a-168">Obedeça à semântica de cancelamento descrita em [Melhores práticas para implementar o Padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="e4b3a-169">Suporte opcional da propriedade IsBusy</span><span class="sxs-lookup"><span data-stu-id="e4b3a-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="e4b3a-170">Se sua classe não oferecer suporte a várias invocações simultâneas, considere a exposição de uma propriedade `IsBusy`.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="e4b3a-171">Isso permite que os desenvolvedores determinem se um método *MethodName***Async** está sendo executado sem capturar uma exceção do método *MethodName***Async**.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-171">This allows developers to determine whether a *MethodName***Async** method is running without catching an exception from the *MethodName***Async** method.</span></span>  
  
 <span data-ttu-id="e4b3a-172">Obedeça à semântica `IsBusy` descrita em [Melhores práticas para implementar o Padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="e4b3a-173">Fornecimento opcional de suporte para relatórios de progresso</span><span class="sxs-lookup"><span data-stu-id="e4b3a-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="e4b3a-174">Costuma ser bom relatar o progresso durante uma operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="e4b3a-175">O padrão assíncrono baseado em evento fornece uma orientação para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="e4b3a-176">Opcionalmente, defina um evento que será gerado pela operação assíncrona e invocado no thread apropriado.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="e4b3a-177">O objeto <xref:System.ComponentModel.ProgressChangedEventArgs> transporta um indicador de progresso com valor de inteiro que deve estar entre 0 e 100.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="e4b3a-178">Nomeie esse evento da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="e4b3a-179">`ProgressChanged` se a classe tiver várias operações assíncronas (ou exista a expectativa de crescimento a fim de incluir várias operações assíncronas em versões futuras);</span><span class="sxs-lookup"><span data-stu-id="e4b3a-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="e4b3a-180">*MethodName***ProgressChanged** se a classe tiver uma única operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-180">*MethodName***ProgressChanged** if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="e4b3a-181">Essa opção de nomenclatura é comparável à feita para o método de cancelamento, conforme descrito na seção Suporte opcional de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="e4b3a-182">Esse evento deve usar a assinatura do delegado <xref:System.ComponentModel.ProgressChangedEventHandler> e a classe <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="e4b3a-183">Como alternativa, se um indicador de progresso mais específico ao domínio puder ser fornecido (por exemplo, bytes lidos e total de bytes de uma operação de download), você deverá definir uma classe derivada de <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="e4b3a-184">Observe que há apenas um evento `ProgressChanged` ou *MethodName***ProgressChanged** para a classe, independentemente do número de métodos assíncronos para os quais ela dá suporte.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-184">Note that there is only one `ProgressChanged` or *MethodName***ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="e4b3a-185">Os clientes devem usar o objeto `userState` que é passado para os métodos *MethodName***Async** a fim de distinguir entre as atualizações de andamento em várias operações simultâneas.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-185">Clients are expected to use the `userState` object that is passed to the *MethodName***Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="e4b3a-186">Pode haver situações em que várias operações dão suporte ao progresso e cada uma retorna um indicador diferente para o progresso.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="e4b3a-187">Nesse caso, um único `ProgressChanged` evento não é apropriado, e você pode considerar o suporte a vários eventos `ProgressChanged`.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="e4b3a-188">Nesse caso, use um padrão de nomenclatura de *MethodName***ProgressChanged** para cada método *MethodName***Async**.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-188">In this case use a naming pattern of *MethodName***ProgressChanged** for each *MethodName***Async** method.</span></span>  
  
 <span data-ttu-id="e4b3a-189">Obedeça à semântica de relatório de progresso descrita em [Melhores práticas para implementar o Padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="e4b3a-190">Fornecimento opcional de suporte para retorno de resultados incrementais</span><span class="sxs-lookup"><span data-stu-id="e4b3a-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="e4b3a-191">Às vezes, uma operação assíncrona pode retornar resultados incrementais antes da conclusão.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="e4b3a-192">Há várias opções que podem ser usadas para oferecer suporte a esse cenário.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="e4b3a-193">Veja a seguir alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="e4b3a-194">Classe de operação única</span><span class="sxs-lookup"><span data-stu-id="e4b3a-194">Single-operation Class</span></span>  
 <span data-ttu-id="e4b3a-195">Se sua classe der suporte apenas a uma única operação assíncrona, e essa operação for capaz de retornar resultados incrementais, então:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="e4b3a-196">Estenda o tipo <xref:System.ComponentModel.ProgressChangedEventArgs> para carregar os dados de resultado incrementais e definir um evento *MethodName***ProgressChanged** com esses dados estendidos.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a *MethodName***ProgressChanged** event with this extended data.</span></span>  
  
-   <span data-ttu-id="e4b3a-197">Gere este evento *MethodName***ProgressChanged** quando houver um resultado incremental ao relatório.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-197">Raise this *MethodName***ProgressChanged** event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="e4b3a-198">Essa solução aplica-se especificamente a uma classe de operação assíncrona única, pois não há nenhum problema com o mesmo evento ocorrendo para retornar resultados incrementais em "todas as operações", como faz o evento *MethodName***ProgressChanged**.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the *MethodName***ProgressChanged** event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="e4b3a-199">Classe de várias operações com resultados incrementais homogêneos</span><span class="sxs-lookup"><span data-stu-id="e4b3a-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="e4b3a-200">Nesse caso, sua classe oferece suporte a vários métodos assíncronos, cada um capaz de retornar resultados incrementais, e todos esses resultados incrementais têm o mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="e4b3a-201">Siga o modelo descrito acima para classes de operação única, pois a mesma estrutura <xref:System.EventArgs> funcionará para todos os resultados incrementais.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="e4b3a-202">Defina um evento `ProgressChanged` em vez de um evento *MethodName***ProgressChanged**, já que ele se aplica a vários métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-202">Define a `ProgressChanged` event instead of a *MethodName***ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="e4b3a-203">Classe de várias operações com resultados incrementais heterogêneos</span><span class="sxs-lookup"><span data-stu-id="e4b3a-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="e4b3a-204">Se sua classe oferece suporte a vários métodos assíncronos, cada um retornando um tipo diferente de dados, você deve:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="e4b3a-205">Separar o relatório de resultado incremental de seu relatório de progresso.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="e4b3a-206">Definir um evento *MethodName***ProgressChanged** com <xref:System.EventArgs> apropriado para cada método assíncrono manipular dados de resultados incrementais desse método.</span><span class="sxs-lookup"><span data-stu-id="e4b3a-206">Define a separate *MethodName***ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="e4b3a-207">Invocar esse manipulador de eventos no thread apropriado, conforme descrito em [Melhores práticas para implementar o Padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="e4b3a-208">Tratamento de parâmetros Out e Ref em métodos</span><span class="sxs-lookup"><span data-stu-id="e4b3a-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="e4b3a-209">Embora o uso de `out` e `ref` seja, em geral, desencorajado no .NET Framework, estas são as regras quando eles estiverem presentes:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="e4b3a-210">Em um método síncrono *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="e4b3a-211">Os parâmetros `out` para *MethodName* não devem fazer parte de *MethodName***Async**. Em vez disso, devem fazer parte de *MethodName***CompletedEventArgs** com o mesmo nome que seu parâmetro equivalente em *MethodName* (a menos que haja um nome mais apropriado).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-211">`out` parameters to *MethodName* should not be part of *MethodName***Async**. Instead, they should be part of *MethodName***CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="e4b3a-212">Os parâmetros `ref` para *MethodName* devem aparecer como parte de *MethodName***Async** e como parte de *MethodName***CompletedEventArgs** com o mesmo nome que seu parâmetro equivalente em *MethodName* (a menos que haja um nome mais apropriado).</span><span class="sxs-lookup"><span data-stu-id="e4b3a-212">`ref` parameters to *MethodName* should appear as part of *MethodName***Async**, and as part of *MethodName***CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="e4b3a-213">Por exemplo, com base em:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-213">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="e4b3a-214">Seu método assíncrono e sua classe <xref:System.ComponentModel.AsyncCompletedEventArgs> teria esta aparência:</span><span class="sxs-lookup"><span data-stu-id="e4b3a-214">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4b3a-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4b3a-215">See Also</span></span>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [<span data-ttu-id="e4b3a-216">Como implementar um componente compatível com o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-216">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="e4b3a-217">Como executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="e4b3a-217">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="e4b3a-218">Como implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="e4b3a-218">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="e4b3a-219">Decidindo quando implementar o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-219">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="e4b3a-220">Programação multi-threaded com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-220">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="e4b3a-221">Práticas recomendadas para a implementação do Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="e4b3a-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
