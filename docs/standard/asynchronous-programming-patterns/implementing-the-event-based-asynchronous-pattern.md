---
title: "Implementando o padrão assíncrono baseado em evento"
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b4df5e4df914d932c7413e9330e8663753456c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="4ebd4-102">Implementando o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="4ebd4-103">Se você estiver escrevendo uma classe com algumas operações que podem causar atrasos notáveis, considere fornecendo funcionalidade assíncrona implementando [baseado em evento visão geral do padrão assíncrono](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="4ebd4-104">O padrão assíncrono baseado em evento fornece uma maneira padronizada para empacotar uma classe que tem recursos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="4ebd4-105">Se implementado com classes auxiliares como <xref:System.ComponentModel.AsyncOperationManager>, sua classe funcionará corretamente em qualquer modelo de aplicativo, incluindo [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], aplicativos de Console e aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="4ebd4-106">Para obter um exemplo que implementa o padrão assíncrono baseado em evento, consulte [como: implementar um componente compatível com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="4ebd4-107">Para operações assíncronas simples, você pode obter o <xref:System.ComponentModel.BackgroundWorker> componente adequado.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="4ebd4-108">Para obter mais informações sobre <xref:System.ComponentModel.BackgroundWorker>, consulte [como: executar uma operação em segundo plano](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="4ebd4-109">A lista a seguir descreve os recursos do que o padrão assíncrono baseado em evento discutidos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="4ebd4-110">Oportunidades para implementar o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="4ebd4-111">Métodos assíncronos de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="4ebd4-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="4ebd4-112">Se desejar oferecer suporte ao cancelamento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="4ebd4-113">Opcionalmente, oferece suporte à propriedade IsBusy</span><span class="sxs-lookup"><span data-stu-id="4ebd4-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="4ebd4-114">Se desejar fornecer suporte para relatórios de andamento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="4ebd4-115">Opcionalmente, fornecer suporte para retornar resultados Incremental</span><span class="sxs-lookup"><span data-stu-id="4ebd4-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="4ebd4-116">Tratamento de Out e Ref parâmetros em métodos</span><span class="sxs-lookup"><span data-stu-id="4ebd4-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="4ebd4-117">Oportunidades para implementar o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="4ebd4-118">Considere implementar o padrão assíncrono baseado em evento quando:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="4ebd4-119">Os clientes da sua classe não é necessário <xref:System.Threading.WaitHandle> e <xref:System.IAsyncResult> objetos disponíveis para operações assíncronas, o que significa que a sondagem e <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> precisam ser criados pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="4ebd4-120">Você deseja que as operações assíncronas para serem gerenciados pelo cliente com o modelo de evento/delegado familiarizado.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="4ebd4-121">Qualquer operação é um candidato para uma implementação assíncrona, mas aqueles que esperar a incidência de latências de tempo devem ser considerados.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="4ebd4-122">Especialmente apropriadas são operações em que os clientes chamar um método em notificados após a conclusão, sem necessidade de intervenção adicional.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="4ebd4-123">Também apropriadas são operações que são executados continuamente, notificando periodicamente os clientes de andamento, resultados incrementais ou alterações de estado.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="4ebd4-124">Para obter mais informações sobre como decidir quando compatíveis com o padrão assíncrono baseado em evento, consulte [Decidindo quando implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="4ebd4-125">Métodos assíncronos de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="4ebd4-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="4ebd4-126">Para cada método síncrono *MethodName* para a qual você deseja fornecer uma cópia assíncrona:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="4ebd4-127">Definir um *MethodName* `Async` método que:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-127">Define a *MethodName*`Async` method that:</span></span>  
  
-   <span data-ttu-id="4ebd4-128">Retorna `void`.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="4ebd4-129">Usa os mesmos parâmetros como o *MethodName* método.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="4ebd4-130">Aceita várias invocações.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="4ebd4-131">Opcionalmente, definir um *MethodName* `Async` sobrecarga, idêntica ao *MethodName*`Async`, mas com um parâmetro adicional com valor de objeto chamado `userState`.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-131">Optionally define a *MethodName*`Async` overload, identical to *MethodName*`Async`, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="4ebd4-132">Faça isso se você está preparado para gerenciar várias chamadas simultâneas do seu método, caso em que o `userState` valor será entregue novamente para todos os manipuladores de eventos para distinguir invocações do método.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="4ebd4-133">Você também pode optar por fazer isso simplesmente como um local para armazenar o estado do usuário para recuperação posterior.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="4ebd4-134">Para cada separado *MethodName* `Async` assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-134">For each separate *MethodName*`Async` method signature:</span></span>  
  
1.  <span data-ttu-id="4ebd4-135">Defina o evento a seguir a mesma classe que o método:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="4ebd4-136">Definir o representante a seguir e <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="4ebd4-137">Eles provavelmente serão definidos fora de classe em si, mas no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
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
  
    -   <span data-ttu-id="4ebd4-138">Certifique-se de que o *MethodName* `CompletedEventArgs` classe expõe seus membros como propriedades somente leitura e não os campos, como campos de impedir que a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-138">Ensure that the *MethodName*`CompletedEventArgs` class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="4ebd4-139">Não definir qualquer <xref:System.ComponentModel.AsyncCompletedEventArgs>-derivadas de classes para métodos que não produzirá os resultados.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="4ebd4-140">Basta usar uma instância de <xref:System.ComponentModel.AsyncCompletedEventArgs> em si.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4ebd4-141">É perfeitamente aceitável, quando apropriado, a reutilização de representante e viável e <xref:System.ComponentModel.AsyncCompletedEventArgs> tipos.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="4ebd4-142">Nesse caso, o nome não será mais consistente com o nome do método, desde um determinado representante e <xref:System.ComponentModel.AsyncCompletedEventArgs> não seja vinculado a um único método.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="4ebd4-143">Se desejar oferecer suporte ao cancelamento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="4ebd4-144">Se sua classe oferecerão suporte a operações assíncronas de cancelamento, cancelamento deve ser exposto ao cliente, conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="4ebd4-145">Observe que há dois pontos de decisão que precisam ser alcançado antes de definir o suporte ao cancelamento de:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="4ebd4-146">Sua classe, incluindo futuros antecipados, tem apenas uma operação assíncrona que oferece suporte ao cancelamento?</span><span class="sxs-lookup"><span data-stu-id="4ebd4-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="4ebd4-147">É possível operações assíncronas que oferecem suporte a várias operações pendentes suporte ao cancelamento?</span><span class="sxs-lookup"><span data-stu-id="4ebd4-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="4ebd4-148">Ou seja, o *MethodName* `Async` método take um `userState` parâmetro, e permitir várias invocações antes de aguardar a conclusão?</span><span class="sxs-lookup"><span data-stu-id="4ebd4-148">That is, does the *MethodName*`Async` method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="4ebd4-149">Use as respostas a essas duas perguntas na tabela a seguir para determinar o que deve ser a assinatura para o método de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="4ebd4-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ebd4-150">Visual Basic</span></span>  
  
||<span data-ttu-id="4ebd4-151">Várias operações simultâneas com suporte</span><span class="sxs-lookup"><span data-stu-id="4ebd4-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="4ebd4-152">Apenas uma operação de cada vez</span><span class="sxs-lookup"><span data-stu-id="4ebd4-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="4ebd4-153">Uma operação assíncrona na classe inteira</span><span class="sxs-lookup"><span data-stu-id="4ebd4-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="4ebd4-154">Várias operações assíncronas em classe</span><span class="sxs-lookup"><span data-stu-id="4ebd4-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="4ebd4-155">C#</span><span class="sxs-lookup"><span data-stu-id="4ebd4-155">C#</span></span>  
  
||<span data-ttu-id="4ebd4-156">Várias operações simultâneas com suporte</span><span class="sxs-lookup"><span data-stu-id="4ebd4-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="4ebd4-157">Apenas uma operação de cada vez</span><span class="sxs-lookup"><span data-stu-id="4ebd4-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="4ebd4-158">Uma operação assíncrona na classe inteira</span><span class="sxs-lookup"><span data-stu-id="4ebd4-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="4ebd4-159">Várias operações assíncronas em classe</span><span class="sxs-lookup"><span data-stu-id="4ebd4-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="4ebd4-160">Se você definir o `CancelAsync(object userState)` método, os clientes devem ser cuidadoso ao escolher seus valores de estado para torná-los capaz de distinguir entre todos os métodos assíncronos chamados no objeto e não apenas entre todas as invocações de um único método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="4ebd4-161">A decisão para a versão de única AsyncOperation *MethodName* `AsyncCancel` baseia-se em ser capaz de descobrir mais facilmente o método em um ambiente de design como IntelliSense do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-161">The decision to name the single-async-operation version *MethodName*`AsyncCancel` is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="4ebd4-162">Isso agrupa os membros relacionados e distingue-los de outros membros que têm relação com funcionalidade assíncrona.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="4ebd4-163">Se você espera que pode haver mais operações assíncronas adicionados em versões subsequentes, é melhor definir `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="4ebd4-164">Não defina vários métodos da tabela acima na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="4ebd4-165">Que não faça sentido, ou ele será sobrecarregar a interface de classe com a proliferação de métodos.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="4ebd4-166">Esses métodos normalmente retornará imediatamente, e a operação pode ou não pode realmente cancelar.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="4ebd4-167">No manipulador de eventos para o *MethodName* `Completed` evento, o *MethodName* `CompletedEventArgs` objeto contém um `Cancelled` campo, o que os clientes podem usar para determinar se a cancelamento tenha ocorrido.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-167">In the event handler for the *MethodName*`Completed` event, the *MethodName*`CompletedEventArgs` object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="4ebd4-168">Obedecer a semântica de cancelamento descrita em [práticas recomendadas para implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="4ebd4-169">Opcionalmente, oferece suporte à propriedade IsBusy</span><span class="sxs-lookup"><span data-stu-id="4ebd4-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="4ebd4-170">Se sua classe não oferece suporte a várias chamadas simultâneas, considere a possibilidade de expor um `IsBusy` propriedade.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="4ebd4-171">Isso permite que desenvolvedores determinar se um *MethodName* `Async` método está sendo executado sem capturando uma exceção do *MethodName* `Async` método.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-171">This allows developers to determine whether a *MethodName*`Async` method is running without catching an exception from the *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="4ebd4-172">Obedecer a `IsBusy` semântica descrito em [práticas recomendadas para implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="4ebd4-173">Se desejar fornecer suporte para relatórios de andamento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="4ebd4-174">É recomendável com frequência para uma operação assíncrona para relatar o progresso durante sua operação.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="4ebd4-175">O padrão assíncrono baseado em evento fornece orientação para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="4ebd4-176">Opcionalmente, defina um evento a ser gerado pela operação assíncrona e invocado no thread apropriado.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="4ebd4-177">O <xref:System.ComponentModel.ProgressChangedEventArgs> objeto transporta um indicador de progresso com valor de inteiro deve estar entre 0 e 100.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="4ebd4-178">Nomeie esse evento da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="4ebd4-179">`ProgressChanged`Se a classe tem várias operações assíncronas (ou deve crescer para incluir várias operações assíncronas em versões futuras);</span><span class="sxs-lookup"><span data-stu-id="4ebd4-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="4ebd4-180">*MethodName* `ProgressChanged` se a classe tiver uma única operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-180">*MethodName* `ProgressChanged` if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="4ebd4-181">Essa opção de nomenclatura comparável ao que feitas para o método de cancelamento, conforme descrito na seção, opcionalmente, o suporte ao cancelamento.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="4ebd4-182">Esse evento deve usar o <xref:System.ComponentModel.ProgressChangedEventHandler> assinatura do delegado e o <xref:System.ComponentModel.ProgressChangedEventArgs> classe.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="4ebd4-183">Como alternativa, se um indicador de progresso mais específica de domínio pode ser fornecido (por instância, leitura de bytes e total de bytes para uma operação de download), em seguida, você deve definir uma classe derivada de <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="4ebd4-184">Observe que há apenas um `ProgressChanged` ou *MethodName* `ProgressChanged` evento para a classe, independentemente do número de métodos assíncronos que ele suporta.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-184">Note that there is only one `ProgressChanged` or *MethodName*`ProgressChanged` event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="4ebd4-185">Os clientes devem usar o `userState` objeto que é passado para o *MethodName* `Async` métodos para distinguir entre as atualizações de andamento em várias operações simultâneas.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-185">Clients are expected to use the `userState` object that is passed to the *MethodName*`Async` methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="4ebd4-186">Pode haver situações em que várias operações de suporte para progresso e cada retorna um indicador diferente para o andamento.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="4ebd4-187">Em um único caso, `ProgressChanged` evento não é apropriado, e você pode considerar o suporte a vários `ProgressChanged` eventos.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="4ebd4-188">Nesse caso, use um padrão de nomeação de *MethodName* `ProgressChanged` para cada *MethodName* `Async` método.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-188">In this case use a naming pattern of *MethodName*`ProgressChanged` for each *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="4ebd4-189">Obedecer a semântica de relatórios de progresso descrita [práticas recomendadas para implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="4ebd4-190">Opcionalmente, fornecer suporte para retornar resultados Incremental</span><span class="sxs-lookup"><span data-stu-id="4ebd4-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="4ebd4-191">Às vezes, uma operação assíncrona pode retornar resultados incrementais antes da conclusão.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="4ebd4-192">Há várias opções que podem ser usados para oferecer suporte a esse cenário.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="4ebd4-193">Seguem alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="4ebd4-194">Operação única classe</span><span class="sxs-lookup"><span data-stu-id="4ebd4-194">Single-operation Class</span></span>  
 <span data-ttu-id="4ebd4-195">Se sua classe só dá suporte a uma única operação assíncrona, e essa operação é capaz de retornar resultados incrementais, em seguida:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="4ebd4-196">Estender o <xref:System.ComponentModel.ProgressChangedEventArgs> digite para carregar os dados de resultado incremental e definir um *MethodName* `ProgressChanged` eventos com essa dados estendidos.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a *MethodName*`ProgressChanged` event with this extended data.</span></span>  
  
-   <span data-ttu-id="4ebd4-197">Gerar isso *MethodName* `ProgressChanged` eventos quando há um resultado incremental ao relatório.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-197">Raise this *MethodName*`ProgressChanged` event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="4ebd4-198">Essa solução se aplica especificamente para uma classe AsyncOperation único porque não há nenhum problema com o mesmo evento ocorrendo retornar resultados incrementais em "todas as operações", como o *MethodName* `ProgressChanged` does do evento.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the *MethodName*`ProgressChanged` event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="4ebd4-199">Classe de várias operações com resultados Incremental homogêneos</span><span class="sxs-lookup"><span data-stu-id="4ebd4-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="4ebd4-200">Nesse caso, sua classe oferece suporte a vários métodos assíncronos, cada capaz de retornar resultados incrementais, e esses resultados incrementais todos têm o mesmo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="4ebd4-201">Siga o modelo descrito acima para classes de operação única, como o mesmo <xref:System.EventArgs> estrutura funciona para todos os resultados incrementais.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="4ebd4-202">Definir um `ProgressChanged` eventos em vez de um *MethodName* `ProgressChanged` evento, desde que ela se aplica a vários métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-202">Define a `ProgressChanged` event instead of a *MethodName*`ProgressChanged` event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="4ebd4-203">Classe de várias operações com resultados Incremental heterogêneos</span><span class="sxs-lookup"><span data-stu-id="4ebd4-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="4ebd4-204">Se sua classe oferece suporte a vários métodos assíncronos, cada retornando um tipo diferente de dados, você deve:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="4ebd4-205">Separe o resultado incremental relatórios a partir de seu relatório de progresso.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="4ebd4-206">Definir um separado *MethodName* `ProgressChanged` evento com apropriado <xref:System.EventArgs> para cada método assíncrono manipular dados de resultado incremental desse método.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-206">Define a separate *MethodName*`ProgressChanged` event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="4ebd4-207">Invocar o manipulador de eventos no thread apropriada conforme descrito em [práticas recomendadas para implementar o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="4ebd4-208">Tratamento de Out e Ref parâmetros em métodos</span><span class="sxs-lookup"><span data-stu-id="4ebd4-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="4ebd4-209">Embora o uso de `out` e `ref` é, em geral, desencorajado no .NET Framework, aqui estão as regras a seguir quando elas estiverem presentes:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="4ebd4-210">Dado um método síncrono *MethodName*:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="4ebd4-211">`out`parâmetros para *MethodName* não deve fazer parte de *MethodName*`Async`.</span><span class="sxs-lookup"><span data-stu-id="4ebd4-211">`out` parameters to *MethodName* should not be part of *MethodName*`Async`.</span></span> <span data-ttu-id="4ebd4-212">Em vez disso, eles devem fazer parte de *MethodName* `CompletedEventArgs` com o mesmo nome como seu parâmetro equivalente em *MethodName* (a menos que haja um nome mais apropriado).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-212">Instead, they should be part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="4ebd4-213">`ref`parâmetros para *MethodName* devem aparecer como parte do *MethodName*`Async`e como parte do *MethodName* `CompletedEventArgs` com o mesmo nome de seu parâmetro equivalente em *MethodName* (a menos que haja um nome mais apropriado).</span><span class="sxs-lookup"><span data-stu-id="4ebd4-213">`ref` parameters to *MethodName* should appear as part of *MethodName*`Async`, and as part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="4ebd4-214">Por exemplo, dado:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-214">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="4ebd4-215">O método assíncrono e sua <xref:System.ComponentModel.AsyncCompletedEventArgs> classe teria esta aparência:</span><span class="sxs-lookup"><span data-stu-id="4ebd4-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ebd4-216">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ebd4-216">See Also</span></span>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [<span data-ttu-id="4ebd4-217">Como implementar um componente compatível com o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="4ebd4-218">Como executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="4ebd4-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="4ebd4-219">Como implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="4ebd4-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="4ebd4-220">Decidindo quando implementar o Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="4ebd4-221">Programação multi-threaded com o padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-221">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="4ebd4-222">Práticas recomendadas para a implementação do Padrão Assíncrono baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="4ebd4-222">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
