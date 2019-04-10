---
title: Expedição por elemento Body
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: ff82ab027ff66b1c4c7433ea77efa6c34ccae088
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330188"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="15b64-102">Expedição por elemento Body</span><span class="sxs-lookup"><span data-stu-id="15b64-102">Dispatch by Body Element</span></span>
<span data-ttu-id="15b64-103">Este exemplo demonstra como implementar um algoritmo alternativo para a atribuição de mensagens de entrada para operações.</span><span class="sxs-lookup"><span data-stu-id="15b64-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="15b64-104">Por padrão, o dispatcher do modelo de serviço seleciona o método de tratamento apropriado para uma mensagem de entrada com base no WS-Addressing da mensagem "Action" informação de cabeçalho ou a equivalente na solicitação HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="15b64-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="15b64-105">Serviços de algumas Web SOAP 1.1 pilhas que não seguem o WS-I Basic Profile 1.1 diretrizes não expedir mensagens com base no URI de ação, mas em vez disso, com base no nome qualificado XML do primeiro elemento no corpo SOAP.</span><span class="sxs-lookup"><span data-stu-id="15b64-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="15b64-106">Da mesma forma, o lado do cliente dessas pilhas pode enviar mensagens com um cabeçalho de HTTP SoapAction vazio ou arbitrário, que era permitido pela especificação SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="15b64-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="15b64-107">Para alterar a maneira como as mensagens são expedidas para métodos, a amostra implementa o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface de extensibilidade no `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="15b64-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="15b64-108">Essa classe seleciona operações com base no primeiro elemento do corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="15b64-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="15b64-109">O construtor da classe espera que um dicionário preenchido com pares de `XmlQualifiedName` e cadeias de caracteres, na qual os nomes qualificados indicam o nome do primeiro filho do corpo SOAP e as cadeias de caracteres indicam o nome da operação correspondente.</span><span class="sxs-lookup"><span data-stu-id="15b64-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="15b64-110">O `defaultOperationName` é o nome da operação que recebe todas as mensagens que não podem ser comparadas com este dicionário:</span><span class="sxs-lookup"><span data-stu-id="15b64-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```csharp
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
}
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> <span data-ttu-id="15b64-111">as implementações são muito simples compilar, pois não há apenas um método na interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="15b64-111">implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="15b64-112">O trabalho desse método é para inspecionar uma mensagem de entrada e retornar uma cadeia de caracteres que é igual ao nome de um método no contrato de serviço para o ponto de extremidade atual.</span><span class="sxs-lookup"><span data-stu-id="15b64-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="15b64-113">Neste exemplo, o seletor de operação adquire uma <xref:System.Xml.XmlDictionaryReader> para a mensagem de entrada do corpo usando <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="15b64-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="15b64-114">Esse método já posiciona o leitor no primeiro filho do corpo da mensagem, para que ele seja suficiente obter o nome do elemento atual e o URI de namespace e combiná-los em um `XmlQualifiedName` que é usada para pesquisar a operação correspondente das dicionário mantido pelo seletor de operação.</span><span class="sxs-lookup"><span data-stu-id="15b64-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```csharp
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 <span data-ttu-id="15b64-115">Acessando o corpo da mensagem com <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> ou qualquer um dos outros métodos que fornecem acesso ao conteúdo do corpo da mensagem faz com que a mensagem a ser marcado como "leitura", o que significa que a mensagem é inválida para qualquer processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="15b64-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="15b64-116">Portanto, o seletor de operação cria uma cópia da mensagem de entrada com o método mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="15b64-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="15b64-117">Porque a posição do leitor não tiver sido alterada durante a inspeção, ele pode ser referenciado pela mensagem recém-criado para o qual as propriedades da mensagem e os cabeçalhos da mensagem também são copiados, que resulta em um clone exato da mensagem original:</span><span class="sxs-lookup"><span data-stu-id="15b64-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```csharp
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="15b64-118">Adicionando um seletor de operação para um serviço</span><span class="sxs-lookup"><span data-stu-id="15b64-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="15b64-119">Seletores de operação de expedição do serviço são extensões para o dispatcher do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="15b64-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="15b64-120">Para selecionar os métodos no canal de retorno de chamada de contratos duplex, também há seletores de operação do cliente, que funciona muito como os seletores de operação de expedição descrito aqui, mas que não é abordado neste exemplo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="15b64-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="15b64-121">Como a maioria das extensões do modelo de serviço, expedir seletores são adicionados ao dispatcher usando comportamentos de operação.</span><span class="sxs-lookup"><span data-stu-id="15b64-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="15b64-122">Um *comportamento* é um objeto de configuração, que adiciona uma ou mais extensões para o tempo de execução de expedição (ou para o tempo de execução do cliente) ou caso contrário, altera suas configurações.</span><span class="sxs-lookup"><span data-stu-id="15b64-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="15b64-123">Como os seletores de operação têm escopo de contrato, o comportamento apropriado implementar aqui é o <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="15b64-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="15b64-124">Porque a interface é implementada em uma <xref:System.Attribute> classe derivada conforme mostrado no código a seguir, o comportamento pode ser adicionado declarativamente a qualquer contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="15b64-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="15b64-125">Sempre que um <xref:System.ServiceModel.ServiceHost> é aberto e o tempo de execução de expedição é criado, todos os comportamentos encontrados como atributos em contratos, operações e implementações de serviço ou como o elemento na configuração do serviço são adicionados automaticamente e subsequentemente solicitado contribuir com extensões ou modifique a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="15b64-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="15b64-126">Para resumir, o trecho de código a seguir mostra apenas a implementação do método <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, que afeta as alterações de configuração para o dispatcher neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="15b64-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="15b64-127">Os outros métodos não são mostrados porque eles retornarem ao chamador sem fazer qualquer trabalho.</span><span class="sxs-lookup"><span data-stu-id="15b64-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="15b64-128">Primeiro, o <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementação define o dicionário de pesquisa para o seletor de operação iterando sobre a <xref:System.ServiceModel.Description.OperationDescription> elementos em um ponto de extremidade de serviço <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="15b64-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="15b64-129">Em seguida, a descrição de cada operação é inspecionada para a presença do `DispatchBodyElementAttribute` comportamento, uma implementação de <xref:System.ServiceModel.Description.IOperationBehavior> que também é definido neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="15b64-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="15b64-130">Embora essa classe também é um comportamento, é passiva e não contribui ativamente alterações de configuração para o tempo de execução de expedição.</span><span class="sxs-lookup"><span data-stu-id="15b64-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="15b64-131">Todos os seus métodos retornam ao chamador sem realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="15b64-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="15b64-132">O comportamento da operação só existe para que os metadados necessários para o novo expedição mecanismo, ou seja, o nome qualificado do elemento body no cuja ocorrência de uma operação for selecionada, pode ser associado com as respectivas operações.</span><span class="sxs-lookup"><span data-stu-id="15b64-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="15b64-133">Se esse comportamento for encontrado, um par de valor criado do nome qualificado XML (`QName` propriedade) e o nome da operação (`Name` propriedade) é adicionada ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="15b64-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="15b64-134">Depois que o dicionário é preenchido, um novo `DispatchByBodyElementOperationSelector` é construído com essas informações e definido como o seletor de operação do tempo de execução de expedição:</span><span class="sxs-lookup"><span data-stu-id="15b64-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =   
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in   
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =   
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,   
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =   
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,   
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a><span data-ttu-id="15b64-135">Implementando o serviço</span><span class="sxs-lookup"><span data-stu-id="15b64-135">Implementing the Service</span></span>  
 <span data-ttu-id="15b64-136">O comportamento implementado nesse exemplo diretamente afeta como mensagens de transmissão são interpretadas e expedidas, que é uma função do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="15b64-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="15b64-137">Consequentemente, o comportamento deve ser declarado no nível do contrato de serviço em qualquer implementação de serviço que escolhe para usá-lo.</span><span class="sxs-lookup"><span data-stu-id="15b64-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="15b64-138">O serviço de projeto de exemplo se aplica a `DispatchByBodyElementBehaviorAttribute` comportamento de contrato a `IDispatchedByBody` contrato e rótulos as duas operações de serviço `OperationForBodyA()` e `OperationForBodyB()` com um `DispatchBodyElementAttribute` comportamento da operação.</span><span class="sxs-lookup"><span data-stu-id="15b64-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="15b64-139">Quando um host de serviço para um serviço que implementa esse contrato é aberto, esses metadados é captado pelo construtor de dispatcher conforme descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="15b64-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="15b64-140">Como o seletor de operação expede exclusivamente com base no elemento de corpo de mensagem e ignora a "ação", é necessário informar o tempo de execução para não verificar o cabeçalho de "Ação" nas respostas retornadas por meio da atribuição o curinga "\*" para o `ReplyAction` propriedade de <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="15b64-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="15b64-141">Além disso, é necessário ter uma operação de padrão que tem a propriedade "Ação" definida como o curinga "\*".</span><span class="sxs-lookup"><span data-stu-id="15b64-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="15b64-142">A operação padrão recebe todas as mensagens que não podem ser expedidas e não tem um `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="15b64-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),   
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),   
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 <span data-ttu-id="15b64-143">A implementação do serviço de exemplo é simples.</span><span class="sxs-lookup"><span data-stu-id="15b64-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="15b64-144">Cada método encapsula a mensagem recebida em uma mensagem de resposta e ecoa-lo de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="15b64-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="15b64-145">Executando e compilando o exemplo</span><span class="sxs-lookup"><span data-stu-id="15b64-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="15b64-146">Quando você executar o exemplo, o conteúdo do corpo das respostas de operação são exibidas na janela do console cliente semelhante à seguinte saída (formatada).</span><span class="sxs-lookup"><span data-stu-id="15b64-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="15b64-147">O cliente envia três mensagens para o serviço cujo corpo de conteúdo de elemento é nomeado `bodyA`, `bodyB`, e `bodyX`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="15b64-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="15b64-148">Como podem ser adiadas de descrição anterior e o contrato de serviço mostrado, a mensagem de entrada com o `bodyA` elemento é expedido para o `OperationForBodyA()` método.</span><span class="sxs-lookup"><span data-stu-id="15b64-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="15b64-149">Porque não há nenhum destino de envio explícito para a mensagem com o `bodyX` elemento body, a mensagem é enviada para o `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="15b64-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="15b64-150">Cada uma das operações de serviço encapsula o corpo da mensagem recebida em um elemento específico para o método e retorna-a, que é feito para correlacionar a entrada e saída mensagens claramente para este exemplo:</span><span class="sxs-lookup"><span data-stu-id="15b64-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="15b64-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="15b64-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="15b64-152">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15b64-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="15b64-153">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15b64-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="15b64-154">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15b64-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="15b64-155">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="15b64-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="15b64-156">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="15b64-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="15b64-157">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="15b64-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15b64-158">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="15b64-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
