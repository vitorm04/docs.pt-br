---
title: Operações síncronas e assíncronas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 3f76d51ce5cc167e71e2f3f5e7944dae2e3265d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645192"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="fe927-102">Operações síncronas e assíncronas</span><span class="sxs-lookup"><span data-stu-id="fe927-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="fe927-103">Este tópico discute como implementar e chamar as operações de serviço assíncronas.</span><span class="sxs-lookup"><span data-stu-id="fe927-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="fe927-104">Muitos aplicativos chamam métodos de forma assíncrona porque isso permite que o aplicativo continue a fazer trabalho útil enquanto a chamada do método é executada.</span><span class="sxs-lookup"><span data-stu-id="fe927-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="fe927-105">Os serviços e clientes do Windows Communication Foundation (WCF) podem participar de chamadas de operações assíncronas em dois níveis diferentes do aplicativo, o que fornece aos aplicativos do WCF ainda mais flexibilidade para maximizar a taxa de transferência balanceada contra interatividade.</span><span class="sxs-lookup"><span data-stu-id="fe927-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="fe927-106">Tipos de operações assíncronas</span><span class="sxs-lookup"><span data-stu-id="fe927-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="fe927-107">Todos os contratos de serviço WCF, independentemente dos tipos de parâmetros e valores retornados, usam os atributos do WCF para especificar um padrão de troca de mensagens específico entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="fe927-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="fe927-108">O WCF roteia automaticamente mensagens de entrada e de saída para a operação de serviço apropriada ou o código cliente em execução.</span><span class="sxs-lookup"><span data-stu-id="fe927-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="fe927-109">O cliente possui apenas o contrato de serviço, que especifica o padrão de troca de mensagens para uma operação específica.</span><span class="sxs-lookup"><span data-stu-id="fe927-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="fe927-110">Os clientes podem oferecer ao desenvolvedor qualquer modelo de programação que escolherem, desde que o padrão subjacente de troca de mensagens seja observado.</span><span class="sxs-lookup"><span data-stu-id="fe927-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="fe927-111">Portanto, os serviços também podem implementar operações de qualquer maneira, desde que o padrão de mensagem especificado seja observado.</span><span class="sxs-lookup"><span data-stu-id="fe927-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="fe927-112">A independência do contrato de serviço na implementação do serviço ou do cliente permite os seguintes formulários de execução assíncrona em aplicativos do WCF:</span><span class="sxs-lookup"><span data-stu-id="fe927-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="fe927-113">Os clientes podem chamar operações de solicitação/resposta de forma assíncrona usando uma troca de mensagens síncrona.</span><span class="sxs-lookup"><span data-stu-id="fe927-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="fe927-114">Os serviços podem implementar uma operação de solicitação/resposta de forma assíncrona usando uma troca de mensagens síncrona.</span><span class="sxs-lookup"><span data-stu-id="fe927-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="fe927-115">As trocas de mensagens podem ser unidirecionais, independentemente da implementação do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="fe927-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="fe927-116">Cenários assíncronos sugeridos</span><span class="sxs-lookup"><span data-stu-id="fe927-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="fe927-117">Use uma abordagem assíncrona em uma implementação de operação do serviço se a implementação do serviço da operação fizer uma chamada de bloqueio, como ao executar trabalho de E/S.</span><span class="sxs-lookup"><span data-stu-id="fe927-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="fe927-118">Quando você estiver em uma implementação de operação assíncrona, tente chamar operações e métodos assíncronos para estender ao máximo o caminho da chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="fe927-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="fe927-119">Por exemplo, chame um `BeginOperationTwo()` de dentro de `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="fe927-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="fe927-120">Use uma abordagem assíncrona em um aplicativo cliente ou de chamada nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="fe927-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="fe927-121">Se você estiver chamando operações em um aplicativo de camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="fe927-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="fe927-122">(Para saber mais sobre esses cenários, confira [Aplicativos cliente de camada intermediária](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="fe927-122">(For more information about such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="fe927-123">Se você estiver chamando operações em uma página do ASP.NET, use páginas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="fe927-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="fe927-124">Se você estiver chamando operações em qualquer aplicativo que seja single-threaded, como o Windows Forms ou o Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="fe927-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="fe927-125">Ao usar o modelo de chamada assíncrona com base em eventos, o evento resultante é gerado no thread da interface do usuário, adicionando capacidade de resposta ao aplicativo sem exigir que você mesmo manipule vários threads.</span><span class="sxs-lookup"><span data-stu-id="fe927-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="fe927-126">Em geral, se você puder escolher entre uma chamada síncrona e uma chamada assíncrona, escolha a chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="fe927-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="fe927-127">Implementando uma operação de serviço assíncrona</span><span class="sxs-lookup"><span data-stu-id="fe927-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="fe927-128">As operações assíncronas podem ser implementadas usando um dos três métodos a seguir:</span><span class="sxs-lookup"><span data-stu-id="fe927-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="fe927-129">O padrão assíncrono baseado em tarefas</span><span class="sxs-lookup"><span data-stu-id="fe927-129">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="fe927-130">O padrão assíncrono baseado em eventos</span><span class="sxs-lookup"><span data-stu-id="fe927-130">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="fe927-131">O padrão assíncrono IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="fe927-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="fe927-132">O padrão assíncrono baseado em tarefas</span><span class="sxs-lookup"><span data-stu-id="fe927-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="fe927-133">O padrão assíncrono baseado em tarefas é o modo preferido de implementar operações assíncronas porque é mais fácil e mais simples.</span><span class="sxs-lookup"><span data-stu-id="fe927-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="fe927-134">Para usar esse método, basta implementar a operação de seu serviço e especificar um tipo de retorno de Task\<T>, em que T é o tipo retornado pela operação lógica.</span><span class="sxs-lookup"><span data-stu-id="fe927-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="fe927-135">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fe927-135">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="fe927-136">A operação SampleMethodTaskAsync retorna Task\<string> porque a operação lógica retorna uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fe927-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="fe927-137">Para saber mais sobre o padrão assíncrono baseado em tarefas, confira [O padrão assíncrono baseado em tarefas](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="fe927-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="fe927-138">Ao usar o padrão assíncrono baseado em tarefas, uma T: System.AggregateException pode ser gerada se uma exceção ocorrer ao aguardar a conclusão da operação.</span><span class="sxs-lookup"><span data-stu-id="fe927-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="fe927-139">Esta exceção pode ocorrer no cliente ou nos serviços</span><span class="sxs-lookup"><span data-stu-id="fe927-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="fe927-140">O padrão assíncrono baseado em eventos</span><span class="sxs-lookup"><span data-stu-id="fe927-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="fe927-141">Um serviço que dá suporte ao padrão assíncrono baseada em eventos terá uma ou mais operações chamadas MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="fe927-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="fe927-142">Esses métodos podem espelhar versões síncronas, que realizam a mesma operação no thread atual.</span><span class="sxs-lookup"><span data-stu-id="fe927-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="fe927-143">A classe também pode ter um evento MethodNameCompleted e pode ter um método MethodNameAsyncCancel (ou simplesmente CancelAsync).</span><span class="sxs-lookup"><span data-stu-id="fe927-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="fe927-144">Um cliente que deseja chamar a operação definirá um manipulador de eventos para ser chamado quando a operação for concluída,</span><span class="sxs-lookup"><span data-stu-id="fe927-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="fe927-145">O snippet de código a seguir ilustra como declarar operações assíncronas usando o padrão assíncrono baseado em eventos.</span><span class="sxs-lookup"><span data-stu-id="fe927-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="fe927-146">Para saber mais sobre o padrão assíncrono baseado em eventos, confira [O padrão assíncrono baseado em eventos](https://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="fe927-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="fe927-147">O padrão assíncrono IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="fe927-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="fe927-148">Uma operação de serviço pode ser implementada de uma forma assíncrona usando o padrão e a marcação de programação assíncrona do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] e marcando o método `<Begin>` com a propriedade <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="fe927-148">A service operation can be implemented in an asynchronous fashion using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="fe927-149">Nesse caso, a operação assíncrona é exposta nos metadados da mesma forma que uma operação síncrona: Ele é exposto como uma única operação com uma mensagem de solicitação e uma mensagem de resposta correlacionada.</span><span class="sxs-lookup"><span data-stu-id="fe927-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="fe927-150">Os modelos de programação do cliente têm uma opção.</span><span class="sxs-lookup"><span data-stu-id="fe927-150">Client programming models then have a choice.</span></span> <span data-ttu-id="fe927-151">Podem representar esse padrão como uma operação síncrona ou assíncrona, desde que, quando o serviço for chamado, ocorra uma troca de mensagens de solicitação de resposta.</span><span class="sxs-lookup"><span data-stu-id="fe927-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="fe927-152">Em geral, com a natureza assíncrona dos sistemas, você não deve usar uma dependência nos threads.</span><span class="sxs-lookup"><span data-stu-id="fe927-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="fe927-153">A maneira mais confiável de transmitir dados para vários estágios do processamento da expedição da operação é usar extensões.</span><span class="sxs-lookup"><span data-stu-id="fe927-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="fe927-154">Para obter um exemplo, consulte [ Implementar uma operação de serviço assíncrona](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="fe927-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="fe927-155">Para definir uma operação `X` do contrato que é executada de forma assíncrona independentemente de como é chamada no aplicativo cliente:</span><span class="sxs-lookup"><span data-stu-id="fe927-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="fe927-156">Defina dois métodos usando o padrão `BeginOperation` e `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="fe927-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="fe927-157">O método `BeginOperation` inclui os parâmetros `in` e `ref` para a operação e retorna um tipo <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="fe927-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="fe927-158">O método `EndOperation` inclui um parâmetro <xref:System.IAsyncResult> e também os parâmetros `out` e `ref` e retorna o tipo de retorno das operações.</span><span class="sxs-lookup"><span data-stu-id="fe927-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="fe927-159">Por exemplo, consulte o seguinte método.</span><span class="sxs-lookup"><span data-stu-id="fe927-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="fe927-160">Para criar uma operação assíncrona, os dois métodos seriam:</span><span class="sxs-lookup"><span data-stu-id="fe927-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
>  <span data-ttu-id="fe927-161">O atributo <xref:System.ServiceModel.OperationContractAttribute> é aplicado apenas ao método `BeginDoWork`.</span><span class="sxs-lookup"><span data-stu-id="fe927-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="fe927-162">O contrato resultante tem uma operação WSDL denominada `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="fe927-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="fe927-163">Chamadas assíncronas do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="fe927-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="fe927-164">Um aplicativo cliente do WCF pode usar qualquer um dos três modelos de chamada assíncrona descritos anteriormente</span><span class="sxs-lookup"><span data-stu-id="fe927-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="fe927-165">Ao usar o modelo baseado em tarefas, basta chamar a operação usando a palavra-chave de espera conforme mostrado no snippet de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="fe927-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="fe927-166">Usar o padrão assíncrono baseado em eventos requer apenas adicionar um manipulador de eventos para receber uma notificação da resposta -- e o evento resultante é gerado automaticamente no thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="fe927-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="fe927-167">Para usar essa abordagem, especifique as opções de comando **/async** e **/tcv:Version35** com a [Ferramenta Utilitário de Metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fe927-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="fe927-168">Quando isso é feito, Svcutil.exe gera uma classe de cliente do WCF com a infraestrutura do evento que permite que o aplicativo de chamada implemente e atribua um manipulador de eventos para receber a resposta e executar a ação apropriada.</span><span class="sxs-lookup"><span data-stu-id="fe927-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="fe927-169">Para obter um exemplo completo, confira [Como: Chamar operações de serviço de forma assíncrona](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="fe927-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="fe927-170">O modelo assíncrono baseado em eventos, no entanto, está disponível apenas no [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe927-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="fe927-171">Além disso, não é suportado nem no [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] quando um canal de cliente do WCF é criado usando <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe927-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fe927-172">Com objetos de canal de cliente do WCF, você deve usar objetos <xref:System.IAsyncResult?displayProperty=nameWithType> para chamar suas operações de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="fe927-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="fe927-173">Para usar essa abordagem, especifique a opção de comando **/async** com a [Ferramenta Utilitário de Metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fe927-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="fe927-174">Isso gera um contrato de serviço no qual cada operação é modelada como um método `<Begin>` com a propriedade <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> definida como `true` e um método `<End>` correspondente.</span><span class="sxs-lookup"><span data-stu-id="fe927-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="fe927-175">Para obter um exemplo completo usando um <xref:System.ServiceModel.ChannelFactory%601>, consulte [como: Chamar operações assíncronas usando uma fábrica de canais](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="fe927-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="fe927-176">Em ambos os casos, os aplicativos podem chamar uma operação de forma assíncrona mesmo que o serviço seja implementado de forma síncrona, da mesma forma que um aplicativo pode usar o mesmo padrão para chamar de forma assíncrona um método síncrono local.</span><span class="sxs-lookup"><span data-stu-id="fe927-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="fe927-177">Como a operação é implementada não é significativo para o cliente. Quando a mensagem de resposta chega, seu conteúdo é expedido para o método <`End`> assíncrono do cliente e o cliente recupera as informações.</span><span class="sxs-lookup"><span data-stu-id="fe927-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="fe927-178">Padrões de troca de mensagens unidirecional</span><span class="sxs-lookup"><span data-stu-id="fe927-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="fe927-179">Você também pode criar um padrão de troca de mensagens assíncronas no qual as operações unidirecionais (operações na quais <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> é `true` não têm resposta correlacionada) podem ser enviadas em qualquer direção pelo cliente ou pelo serviço independentemente do outro lado.</span><span class="sxs-lookup"><span data-stu-id="fe927-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="fe927-180">Isso usa o padrão de troca de mensagens dúplex com mensagens unidirecionais. Nesse caso, o contrato de serviço especifica uma troca de mensagens unidirecional, que qualquer um dos lados pode implementar como chamadas ou implementações assíncronas, ou não, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="fe927-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="fe927-181">Em geral, quando o contrato é uma troca de mensagens unidirecional, as implementações podem ser amplamente assíncronas porque, depois que uma mensagem é enviada, o aplicativo não espera uma resposta e pode continuar a fazer outro trabalho.</span><span class="sxs-lookup"><span data-stu-id="fe927-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="fe927-182">Clientes e contratos de mensagens assíncronas com base em eventos</span><span class="sxs-lookup"><span data-stu-id="fe927-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="fe927-183">As diretrizes de design do modelo assíncrono baseado em eventos declaram que, se mais de um valor for retornado, um valor será retornado como a propriedade `Result` e os outros serão retornados como propriedades no objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="fe927-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="fe927-184">Um resultado é que, se um cliente importar metadados usando as opções de comando assíncrono com base em eventos, e a operação retornar mais de um valor, o objeto padrão <xref:System.EventArgs> retornará um valor como a propriedade `Result` e os restantes serão propriedades do objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="fe927-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="fe927-185">Se você desejar receber o objeto de mensagem como a propriedade `Result` e ter valores retornados como propriedades nesse objeto, use a opção de comando **/messageContract**.</span><span class="sxs-lookup"><span data-stu-id="fe927-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="fe927-186">Isso gera uma assinatura que retorna a mensagem de resposta como a propriedade `Result` no objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="fe927-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="fe927-187">Todos os valores de retorno internos são propriedades do objeto da mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="fe927-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe927-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe927-188">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
