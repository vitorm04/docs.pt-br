---
title: Expedição por elemento Body
ms.date: 03/30/2017
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
ms.openlocfilehash: 754151f856dfe09b8fd12912ab06d1d8720be016
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183718"
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="3f69f-102">Expedição por elemento Body</span><span class="sxs-lookup"><span data-stu-id="3f69f-102">Dispatch by Body Element</span></span>
<span data-ttu-id="3f69f-103">Esta amostra demonstra como implementar um algoritmo alternativo para atribuir mensagens recebidas às operações.</span><span class="sxs-lookup"><span data-stu-id="3f69f-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="3f69f-104">Por padrão, o despachante do modelo de serviço seleciona o método de manuseio apropriado para uma mensagem recebida com base no cabeçalho "Action" da mensagem ou nas informações equivalentes na solicitação HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="3f69f-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="3f69f-105">Algumas pilhas de serviços DA SOAP 1.1 que não seguem as diretrizes do Perfil Básico WS-I 1.1 não despacham mensagens baseadas no URI de ação, mas sim com base no nome qualificado XML do primeiro elemento dentro do corpo SOAP.</span><span class="sxs-lookup"><span data-stu-id="3f69f-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="3f69f-106">Da mesma forma, o lado cliente dessas pilhas pode enviar mensagens com um cabeçalho HTTP SoapAction vazio ou arbitrário, o que foi permitido pela especificação SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="3f69f-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="3f69f-107">Para alterar a forma como as mensagens são enviadas <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> para métodos, `DispatchByBodyElementOperationSelector`a amostra implementa a interface de extensibilidade no .</span><span class="sxs-lookup"><span data-stu-id="3f69f-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="3f69f-108">Esta classe seleciona operações com base no primeiro elemento do corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="3f69f-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="3f69f-109">O construtor de classe espera um dicionário `XmlQualifiedName` preenchido com pares de e cordas, pelo qual os nomes qualificados indicam o nome do primeiro filho do corpo SOAP e as cordas indicam o nome da operação correspondente.</span><span class="sxs-lookup"><span data-stu-id="3f69f-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="3f69f-110">O `defaultOperationName` é o nome da operação que recebe todas as mensagens que não podem ser comparadas com este dicionário:</span><span class="sxs-lookup"><span data-stu-id="3f69f-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
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
  
 <span data-ttu-id="3f69f-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementações são muito simples de construir, pois há <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>apenas um método na interface: .</span><span class="sxs-lookup"><span data-stu-id="3f69f-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="3f69f-112">O trabalho deste método é inspecionar uma mensagem recebida e devolver uma seqüência que seja igual ao nome de um método no contrato de serviço para o ponto final atual.</span><span class="sxs-lookup"><span data-stu-id="3f69f-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="3f69f-113">Nesta amostra, o seletor <xref:System.Xml.XmlDictionaryReader> de operação adquire um <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>para o corpo da mensagem recebida usando .</span><span class="sxs-lookup"><span data-stu-id="3f69f-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="3f69f-114">Este método já posiciona o leitor sobre o primeiro filho do corpo da mensagem de modo que seja suficiente `XmlQualifiedName` para obter o nome do elemento atual e o espaço de nome URI e combiná-lo em um que é então usado para procurar a operação correspondente do dicionário mantido pelo seletor de operação.</span><span class="sxs-lookup"><span data-stu-id="3f69f-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
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
  
 <span data-ttu-id="3f69f-115">Acessar o corpo <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> da mensagem com ou qualquer outro método que forneça acesso ao conteúdo do corpo da mensagem faz com que a mensagem seja marcada como "leitura", o que significa que a mensagem é inválida para qualquer processamento adicional.</span><span class="sxs-lookup"><span data-stu-id="3f69f-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="3f69f-116">Portanto, o seletor de operação cria uma cópia da mensagem recebida com o método mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3f69f-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="3f69f-117">Como a posição do leitor não foi alterada durante a inspeção, ela pode ser referenciada pela mensagem recém-criada à qual as propriedades da mensagem e os cabeçalhos de mensagem também são copiados, o que resulta em um clone exato da mensagem original:</span><span class="sxs-lookup"><span data-stu-id="3f69f-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
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
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="3f69f-118">Adicionando um Seletor de Operação a um Serviço</span><span class="sxs-lookup"><span data-stu-id="3f69f-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="3f69f-119">Os seletores de operação de despacho de serviço são extensões para o despachante da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3f69f-119">Service dispatch operation selectors are extensions to the Windows Communication Foundation (WCF) dispatcher.</span></span> <span data-ttu-id="3f69f-120">Para selecionar métodos no canal de retorno de contratos duplex, há também seletores de operação do cliente, que funcionam muito parecidos com os seletores de operação de despacho descritos aqui, mas que não estão explicitamente cobertos nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="3f69f-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="3f69f-121">Como a maioria das extensões do modelo de serviço, os seletores de operação de despacho são adicionados ao despachante usando comportamentos.</span><span class="sxs-lookup"><span data-stu-id="3f69f-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="3f69f-122">Um *comportamento* é um objeto de configuração, que adiciona uma ou mais extensões ao tempo de execução do despacho (ou ao tempo de execução do cliente) ou altera suas configurações.</span><span class="sxs-lookup"><span data-stu-id="3f69f-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="3f69f-123">Como os seletores de operação têm escopo de <xref:System.ServiceModel.Description.IContractBehavior>contrato, o comportamento apropriado para implementar aqui é o .</span><span class="sxs-lookup"><span data-stu-id="3f69f-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="3f69f-124">Como a interface é <xref:System.Attribute> implementada em uma classe derivada, como mostrado no código a seguir, o comportamento pode ser declarativamente adicionado a qualquer contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="3f69f-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="3f69f-125">Sempre <xref:System.ServiceModel.ServiceHost> que um é aberto e o tempo de execução de despacho é construído, todos os comportamentos encontrados como atributos em contratos, operações e implementações de serviço ou como elemento na configuração do serviço são automaticamente adicionados e posteriormente solicitados a contribuir com extensões ou modificar a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="3f69f-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="3f69f-126">Para a brevidade, o trecho de código <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>a seguir mostra apenas a implementação do método , o que afeta as alterações de configuração para o despachante nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="3f69f-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="3f69f-127">Os outros métodos não são mostrados porque retornam ao chamador sem fazer qualquer trabalho.</span><span class="sxs-lookup"><span data-stu-id="3f69f-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```csharp
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="3f69f-128">Primeiro, <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> a implementação configura o dicionário de busca para o <xref:System.ServiceModel.Description.OperationDescription> seletor de <xref:System.ServiceModel.Description.ContractDescription>operação, iterando sobre os elementos no ponto final do serviço .</span><span class="sxs-lookup"><span data-stu-id="3f69f-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="3f69f-129">Em seguida, cada descrição da `DispatchBodyElementAttribute` <xref:System.ServiceModel.Description.IOperationBehavior> operação é inspecionada para a presença do comportamento, uma implementação que também é definida nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="3f69f-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="3f69f-130">Embora essa classe também seja um comportamento, ela é passiva e não contribui ativamente com nenhuma alteração de configuração no tempo de execução do despacho.</span><span class="sxs-lookup"><span data-stu-id="3f69f-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="3f69f-131">Todos os seus métodos retornam ao chamador sem tomar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="3f69f-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="3f69f-132">O comportamento de operação só existe para que os metadados necessários para o novo mecanismo de expedição, ou seja, o nome qualificado do elemento do corpo em cuja ocorrência uma operação é selecionada, possam ser associados às respectivas operações.</span><span class="sxs-lookup"><span data-stu-id="3f69f-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="3f69f-133">Se tal comportamento for encontrado, um par de valores`QName` criado a partir`Name` do nome qualificado XML (propriedade) e o nome da operação (propriedade) será adicionado ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="3f69f-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="3f69f-134">Uma vez preenchido o dicionário, um novo `DispatchByBodyElementOperationSelector` é construído com essas informações e definido como o seletor de operação do tempo de execução do despacho:</span><span class="sxs-lookup"><span data-stu-id="3f69f-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
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
  
## <a name="implementing-the-service"></a><span data-ttu-id="3f69f-135">Implementação do Serviço</span><span class="sxs-lookup"><span data-stu-id="3f69f-135">Implementing the Service</span></span>  
 <span data-ttu-id="3f69f-136">O comportamento implementado nesta amostra afeta diretamente a forma como as mensagens do fio são interpretadas e despachadas, o que é uma função do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="3f69f-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="3f69f-137">Consequentemente, o comportamento deve ser declarado no nível do contrato de serviço em qualquer implementação de serviço que optar por usá-lo.</span><span class="sxs-lookup"><span data-stu-id="3f69f-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="3f69f-138">O serviço de projeto `DispatchByBodyElementBehaviorAttribute` amostral `IDispatchedByBody` aplica o comportamento contratual ao `OperationForBodyA()` contrato `OperationForBodyB()` de `DispatchBodyElementAttribute` serviço e rotula cada uma das duas operações e com um comportamento operacional.</span><span class="sxs-lookup"><span data-stu-id="3f69f-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="3f69f-139">Quando um host de serviço para um serviço que implementa este contrato é aberto, esses metadados são captados pelo construtor de spaceiros como descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3f69f-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="3f69f-140">Como o seletor de operação despacha exclusivamente com base no elemento do corpo da mensagem e ignora a "Ação", é necessário dizer ao `ReplyAction` tempo <xref:System.ServiceModel.OperationContractAttribute>de execução para não verificar o cabeçalho "Ação" nas respostas devolvidas atribuindo o curinga "\*" à propriedade de .</span><span class="sxs-lookup"><span data-stu-id="3f69f-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "\*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="3f69f-141">Além disso, é necessário ter uma operação padrão que tenha a propriedade\*"Action" definida como curinga " ".</span><span class="sxs-lookup"><span data-stu-id="3f69f-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="3f69f-142">A operação padrão recebe todas as mensagens que `DispatchBodyElementAttribute`não podem ser despachadas e não têm:</span><span class="sxs-lookup"><span data-stu-id="3f69f-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
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
  
 <span data-ttu-id="3f69f-143">A implementação do serviço de amostra é simples.</span><span class="sxs-lookup"><span data-stu-id="3f69f-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="3f69f-144">Cada método envolve a mensagem recebida em uma mensagem de resposta e a ecoa de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3f69f-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="3f69f-145">Executando e construindo a amostra</span><span class="sxs-lookup"><span data-stu-id="3f69f-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="3f69f-146">Quando você executa a amostra, o conteúdo do corpo das respostas de operação é exibido na janela do console cliente semelhante à seguinte saída (formatada).</span><span class="sxs-lookup"><span data-stu-id="3f69f-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="3f69f-147">O cliente envia três mensagens para o `bodyA`serviço `bodyB`cujo `bodyX`elemento de conteúdo corporal é nomeado , e , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3f69f-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="3f69f-148">Como pode ser diferido a partir da descrição anterior e `bodyA` do contrato de `OperationForBodyA()` serviço mostrado, a mensagem recebida com o elemento é enviada para o método.</span><span class="sxs-lookup"><span data-stu-id="3f69f-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="3f69f-149">Como não há um alvo de `bodyX` despacho explícito para a mensagem `DefaultOperation()`com o elemento do corpo, a mensagem é enviada para o .</span><span class="sxs-lookup"><span data-stu-id="3f69f-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="3f69f-150">Cada uma das operações de serviço envolve o corpo de mensagem recebida em um elemento específico do método e o devolve, o que é feito para correlacionar mensagens de entrada e saída claramente para esta amostra:</span><span class="sxs-lookup"><span data-stu-id="3f69f-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3f69f-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3f69f-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3f69f-152">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f69f-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3f69f-153">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f69f-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3f69f-154">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3f69f-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3f69f-155">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3f69f-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3f69f-156">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3f69f-156">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3f69f-157">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="3f69f-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3f69f-158">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3f69f-158">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
