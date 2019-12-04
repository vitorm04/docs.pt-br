---
title: Expedição por elemento Body
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 307d6bbbab118392ef079942eae367a4c6792c22
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712026"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="4ba1e-102">Expedição por elemento Body</span><span class="sxs-lookup"><span data-stu-id="4ba1e-102">Dispatch by Body Element</span></span>
<span data-ttu-id="4ba1e-103">Este exemplo demonstra como implementar um algoritmo alternativo para atribuir mensagens de entrada a operações.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="4ba1e-104">Por padrão, o distribuidor do modelo de serviço seleciona o método de tratamento apropriado para uma mensagem de entrada com base no cabeçalho "ação" do WS-Addressing da mensagem ou nas informações equivalentes na solicitação HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="4ba1e-105">Algumas pilhas de serviços Web SOAP 1,1 que não seguem as diretrizes WS-I Basic Profile 1,1 não expedem mensagens com base no URI de ação, mas com base no nome qualificado XML do primeiro elemento dentro do corpo SOAP.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="4ba1e-106">Da mesma forma, o lado do cliente dessas pilhas pode enviar mensagens com um cabeçalho SOAPAction HTTP vazio ou arbitrário, que era permitido pela especificação SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="4ba1e-107">Para alterar a maneira como as mensagens são expedidas para métodos, o exemplo implementa a interface de extensibilidade do <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> no `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="4ba1e-108">Essa classe seleciona operações baseadas no primeiro elemento do corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="4ba1e-109">O construtor de classe espera que um dicionário seja preenchido com pares de `XmlQualifiedName` e cadeias de caracteres, no qual os nomes qualificados indicam o nome do primeiro filho do corpo SOAP e as cadeias de caracteres indicam o nome da operação correspondente.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="4ba1e-110">O `defaultOperationName` é o nome da operação que recebe todas as mensagens que não podem ser correspondidas em relação a este dicionário:</span><span class="sxs-lookup"><span data-stu-id="4ba1e-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="4ba1e-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementações são muito simples de criar, pois há apenas um método na interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="4ba1e-112">O trabalho desse método é inspecionar uma mensagem de entrada e retornar uma cadeia de caracteres que seja igual ao nome de um método no contrato de serviço para o ponto de extremidade atual.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="4ba1e-113">Neste exemplo, o seletor de operação adquire um <xref:System.Xml.XmlDictionaryReader> para o corpo da mensagem de entrada usando <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="4ba1e-114">Esse método já posiciona o leitor no primeiro filho do corpo da mensagem para que seja suficiente obter o nome do elemento atual e o URI do namespace e combiná-los em um `XmlQualifiedName` que, em seguida, é usado para pesquisar a operação correspondente do dicionário mantido pelo seletor de operação.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="4ba1e-115">Acessar o corpo da mensagem com <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> ou qualquer um dos outros métodos que fornecem acesso ao conteúdo do corpo da mensagem faz com que a mensagem seja marcada como "leitura", o que significa que a mensagem é inválida para qualquer processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="4ba1e-116">Portanto, o seletor de operação cria uma cópia da mensagem de entrada com o método mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="4ba1e-117">Como a posição do leitor não foi alterada durante a inspeção, ela pode ser referenciada pela mensagem recém-criada para a qual as propriedades de mensagem e os cabeçalhos de mensagem também são copiados, o que resulta em um clone exato da mensagem original:</span><span class="sxs-lookup"><span data-stu-id="4ba1e-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="4ba1e-118">Adicionando um seletor de operação a um serviço</span><span class="sxs-lookup"><span data-stu-id="4ba1e-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="4ba1e-119">Os seletores de operação de expedição de serviço são extensões para o Dispatcher do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4ba1e-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="4ba1e-120">Para selecionar métodos no canal de retorno de chamada de contratos duplex, também há seletores de operação do cliente, que funcionam muito como os seletores de operação de expedição descritos aqui, mas que não são explicitamente abordados neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="4ba1e-121">Assim como a maioria das extensões de modelo de serviço, os seletores de operação de expedição são adicionados ao dispatcher usando comportamentos.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="4ba1e-122">Um *comportamento* é um objeto de configuração, que adiciona uma ou mais extensões ao tempo de execução de expedição (ou ao tempo de execução do cliente) ou altera suas configurações.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="4ba1e-123">Como os seletores de operação têm o escopo do contrato, o comportamento apropriado a ser implementado aqui é o <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="4ba1e-124">Como a interface é implementada em uma classe derivada <xref:System.Attribute>, conforme mostrado no código a seguir, o comportamento pode ser adicionado declarativamente a qualquer contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="4ba1e-125">Sempre que um <xref:System.ServiceModel.ServiceHost> é aberto e o tempo de execução de expedição é criado, todos os comportamentos encontrados como atributos em contratos, operações e implementações de serviço ou como elemento na configuração do serviço são adicionados automaticamente e, posteriormente, solicitados a contribuir com as extensões ou modificar a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="4ba1e-126">Para resumir, o trecho de código a seguir mostra apenas a implementação do método <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, que afeta as alterações de configuração para o Dispatcher neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="4ba1e-127">Os outros métodos não são mostrados porque retornam ao chamador sem fazer nenhum trabalho.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="4ba1e-128">Primeiro, a implementação de <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> configura o dicionário de pesquisa para o seletor de operação Iterando sobre os elementos <xref:System.ServiceModel.Description.OperationDescription> na <xref:System.ServiceModel.Description.ContractDescription>do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="4ba1e-129">Em seguida, cada descrição de operação é inspecionada para a presença do comportamento de `DispatchBodyElementAttribute`, uma implementação de <xref:System.ServiceModel.Description.IOperationBehavior> que também está definida neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="4ba1e-130">Embora essa classe também seja um comportamento, ela é passiva e não contribui ativamente com nenhuma alteração de configuração no tempo de execução de expedição.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="4ba1e-131">Todos os seus métodos retornam ao chamador sem realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="4ba1e-132">O comportamento da operação existe apenas para que os metadados necessários para o novo mecanismo de expedição, ou seja, o nome qualificado do elemento body em cuja ocorrência de uma operação seja selecionada, possam ser associados às respectivas operações.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="4ba1e-133">Se esse comportamento for encontrado, um par de valores criado com base no nome qualificado XML (`QName` Propriedade) e o nome da operação (`Name` Propriedade) serão adicionados ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="4ba1e-134">Depois que o dicionário é populado, um novo `DispatchByBodyElementOperationSelector` é construído com essas informações e definido como o seletor de operação do tempo de execução de expedição:</span><span class="sxs-lookup"><span data-stu-id="4ba1e-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="4ba1e-135">Implementando o serviço</span><span class="sxs-lookup"><span data-stu-id="4ba1e-135">Implementing the Service</span></span>  
 <span data-ttu-id="4ba1e-136">O comportamento implementado neste exemplo afeta diretamente como as mensagens da transmissão são interpretadas e expedidas, que é uma função do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="4ba1e-137">Consequentemente, o comportamento deve ser declarado no nível de contrato de serviço em qualquer implementação de serviço que escolha usá-lo.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="4ba1e-138">O serviço de projeto de exemplo aplica o comportamento de contrato `DispatchByBodyElementBehaviorAttribute` ao contrato de serviço `IDispatchedByBody` e rotula cada uma das duas operações `OperationForBodyA()` e `OperationForBodyB()` com um comportamento de operação `DispatchBodyElementAttribute`.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="4ba1e-139">Quando um host de serviço para um serviço que implementa esse contrato é aberto, esses metadados são coletados pelo Dispatcher Builder conforme descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="4ba1e-140">Como o seletor de operação é expedido exclusivamente com base no elemento do corpo da mensagem e ignora a "ação", é necessário informar ao tempo de execução para não verificar o cabeçalho "ação" nas respostas retornadas atribuindo o curinga "\*" à propriedade `ReplyAction` de <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="4ba1e-141">Além disso, é necessário ter uma operação padrão que tenha a propriedade "Action" definida como o curinga "\*".</span><span class="sxs-lookup"><span data-stu-id="4ba1e-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="4ba1e-142">A operação padrão recebe todas as mensagens que não podem ser expedidas e não tem um `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="4ba1e-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="4ba1e-143">A implementação do serviço de exemplo é simples.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="4ba1e-144">Cada método encapsula a mensagem recebida em uma mensagem de resposta e a ecoa de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="4ba1e-145">Executando e compilando o exemplo</span><span class="sxs-lookup"><span data-stu-id="4ba1e-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="4ba1e-146">Quando você executa o exemplo, o conteúdo do corpo das respostas da operação é exibido na janela do console do cliente semelhante à saída (formatada) a seguir.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="4ba1e-147">O cliente envia três mensagens para o serviço cujo elemento de conteúdo do corpo é nomeado `bodyA`, `bodyB`e `bodyX`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="4ba1e-148">Como pode ser adiado da descrição anterior e do contrato de serviço mostrado, a mensagem de entrada com o elemento `bodyA` é expedida para o método `OperationForBodyA()`.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="4ba1e-149">Como não há nenhum destino de expedição explícito para a mensagem com o elemento de corpo `bodyX`, a mensagem é expedida para o `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="4ba1e-150">Cada uma das operações de serviço encapsula o corpo da mensagem recebida em um elemento específico do método e a retorna, o que é feito para correlacionar as mensagens de entrada e saída claramente para este exemplo:</span><span class="sxs-lookup"><span data-stu-id="4ba1e-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4ba1e-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4ba1e-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4ba1e-152">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ba1e-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4ba1e-153">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ba1e-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4ba1e-154">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ba1e-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4ba1e-155">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4ba1e-156">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-156">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4ba1e-157">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ba1e-158">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4ba1e-158">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
