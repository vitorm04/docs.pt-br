---
title: Formatador de operação e seletor de operação
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144273"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="cedeb-102">Formatador de operação e seletor de operação</span><span class="sxs-lookup"><span data-stu-id="cedeb-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="cedeb-103">Esta amostra demonstra como os pontos de extensibilidade da Windows Communication Foundation (WCF) podem ser usados para permitir dados de mensagens em um formato diferente do que o WCF espera.</span><span class="sxs-lookup"><span data-stu-id="cedeb-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="cedeb-104">Por padrão, os assuntos do WCF esperam `soap:body` que os parâmetros do método sejam incluídos o elemento.</span><span class="sxs-lookup"><span data-stu-id="cedeb-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="cedeb-105">A amostra mostra como implementar uma operação personalizada que analisa dados de parâmetros de uma seqüência de consultas HTTP GET e invoca métodos usando esses dados.</span><span class="sxs-lookup"><span data-stu-id="cedeb-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="cedeb-106">A amostra é baseada no [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md)Started `ICalculator` , que implementa o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="cedeb-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="cedeb-107">Ele mostra como as mensagens Add, Subtract, Multiply e Divide podem ser alteradas para usar http get para solicitações de cliente para servidor e POST HTTP com mensagens POX para respostas de servidor para cliente.</span><span class="sxs-lookup"><span data-stu-id="cedeb-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="cedeb-108">Para isso, a amostra fornece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cedeb-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="cedeb-109">`QueryStringFormatter`, que <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementa e <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> para o cliente e servidor, respectivamente, e processa os dados na cadeia de consulta.</span><span class="sxs-lookup"><span data-stu-id="cedeb-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="cedeb-110">`UriOperationSelector`, que <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementa no servidor para executar o envio de operação com base no nome da operação na solicitação GET.</span><span class="sxs-lookup"><span data-stu-id="cedeb-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="cedeb-111">`EnableHttpGetRequestsBehavior`comportamento de ponto final (e configuração correspondente), que adiciona o seletor de operação necessário ao tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cedeb-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="cedeb-112">Mostra como inserir uma nova operação no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cedeb-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="cedeb-113">Nesta amostra, tanto o cliente quanto o serviço são aplicativos de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="cedeb-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cedeb-114">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cedeb-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="cedeb-115">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="cedeb-115">Key Concepts</span></span>  
 <span data-ttu-id="cedeb-116">`QueryStringFormatter`- A matéria-atacante de operação é o componente no WCF que é responsável por converter uma mensagem em uma matriz de objetos de parâmetro e uma matriz de objetos de parâmetro em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="cedeb-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="cedeb-117">Isso é feito no <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> cliente usando a interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> e no servidor com a interface.</span><span class="sxs-lookup"><span data-stu-id="cedeb-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="cedeb-118">Essas interfaces permitem que os usuários obtenham `Serialize` `Deserialize` as mensagens de solicitação e resposta dos métodos e.</span><span class="sxs-lookup"><span data-stu-id="cedeb-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="cedeb-119">Nesta amostra, `QueryStringFormatter` implementa ambas as interfaces e é implementada no cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="cedeb-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="cedeb-120">Solicitação:</span><span class="sxs-lookup"><span data-stu-id="cedeb-120">Request:</span></span>  
  
- <span data-ttu-id="cedeb-121">A amostra <xref:System.ComponentModel.TypeConverter> usa a classe para converter dados de parâmetros na mensagem de solicitação para e a partir de strings.</span><span class="sxs-lookup"><span data-stu-id="cedeb-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="cedeb-122">Se <xref:System.ComponentModel.TypeConverter> a não estiver disponível para um tipo específico, a matéria-guia da amostra abre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="cedeb-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="cedeb-123">No `IClientMessageFormatter.SerializeRequest` método no cliente, o formatter cria um URI com o endereço apropriado e anexa o nome da operação como um sufixo.</span><span class="sxs-lookup"><span data-stu-id="cedeb-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="cedeb-124">Este nome é usado para despachar para a operação apropriada no servidor.</span><span class="sxs-lookup"><span data-stu-id="cedeb-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="cedeb-125">Em seguida, ele pega a matriz de objetos de parâmetro e serializa os dados de parâmetro <xref:System.ComponentModel.TypeConverter> para a seqüência de consulta uri usando nomes de parâmetros e os valores convertidos pela classe.</span><span class="sxs-lookup"><span data-stu-id="cedeb-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="cedeb-126">As <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> propriedades e propriedades são então definidas para este URI.</span><span class="sxs-lookup"><span data-stu-id="cedeb-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="cedeb-127"><xref:System.ServiceModel.Channels.MessageProperties>é acessado através <xref:System.ServiceModel.Channels.Message.Properties%2A> da propriedade.</span><span class="sxs-lookup"><span data-stu-id="cedeb-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="cedeb-128">No `IDispatchMessageFormatter.DeserializeRequest` método no servidor, o formatter `Via` recupera o URI nas propriedades de mensagem de solicitação recebidas.</span><span class="sxs-lookup"><span data-stu-id="cedeb-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="cedeb-129">Ele analisa os pares de valor de nome na seqüência de consulta uri em nomes e valores de parâmetros e usa os nomes e valores dos parâmetros para preencher a matriz de parâmetros passados para o método.</span><span class="sxs-lookup"><span data-stu-id="cedeb-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="cedeb-130">Observe que o despacho de operação já ocorreu, de modo que o sufixo nome da operação é ignorado neste método.</span><span class="sxs-lookup"><span data-stu-id="cedeb-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="cedeb-131">Resposta:</span><span class="sxs-lookup"><span data-stu-id="cedeb-131">Response:</span></span>  
  
- <span data-ttu-id="cedeb-132">Nesta amostra, HTTP GET é usado apenas para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="cedeb-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="cedeb-133">A matéria-geral delega o envio da resposta ao formatter original que teria sido usado para gerar uma mensagem XML.</span><span class="sxs-lookup"><span data-stu-id="cedeb-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="cedeb-134">Um dos objetivos desta amostra é mostrar como essa matéria delegante pode ser implementada.</span><span class="sxs-lookup"><span data-stu-id="cedeb-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="cedeb-135">UriPathSuffixClasseClasseClasseSelector</span><span class="sxs-lookup"><span data-stu-id="cedeb-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="cedeb-136">A <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface permite que os usuários implementem sua própria lógica para a qual operação uma determinada mensagem deve ser enviada.</span><span class="sxs-lookup"><span data-stu-id="cedeb-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="cedeb-137">Nesta amostra, `UriPathSuffixOperationSelector` deve ser implementado no servidor para selecionar a operação apropriada porque o nome da operação está incluído no HTTP GET URI em vez de um cabeçalho de ação na mensagem.</span><span class="sxs-lookup"><span data-stu-id="cedeb-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="cedeb-138">A amostra é configurada para permitir apenas nomes de operação insensíveis a casos.</span><span class="sxs-lookup"><span data-stu-id="cedeb-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="cedeb-139">O `SelectOperation` método pega a mensagem `Via` recebida e procura o URI em suas propriedades de mensagem.</span><span class="sxs-lookup"><span data-stu-id="cedeb-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="cedeb-140">Ele extrai o sufixo de nome de operação do URI, procura uma tabela interna para obter o nome da operação para o qual a mensagem deve ser enviada e retorna o nome da operação.</span><span class="sxs-lookup"><span data-stu-id="cedeb-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="cedeb-141">AtivarhttpGetRequestsClasse de comportamento</span><span class="sxs-lookup"><span data-stu-id="cedeb-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="cedeb-142">O `UriPathSuffixOperationSelector` componente pode ser configurado programáticamente ou através de um comportamento de ponto final.</span><span class="sxs-lookup"><span data-stu-id="cedeb-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="cedeb-143">A amostra implementa o `EnableHttpGetRequestsBehavior` comportamento, que é especificado no arquivo de configuração do aplicativo do serviço.</span><span class="sxs-lookup"><span data-stu-id="cedeb-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="cedeb-144">No servidor:</span><span class="sxs-lookup"><span data-stu-id="cedeb-144">On the server:</span></span>  
  
 <span data-ttu-id="cedeb-145">O <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> está definido <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> para a implementação.</span><span class="sxs-lookup"><span data-stu-id="cedeb-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="cedeb-146">Por padrão, o WCF usa um filtro de endereço de correspondência exata.</span><span class="sxs-lookup"><span data-stu-id="cedeb-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="cedeb-147">O URI na mensagem recebida contém um sufixo de nome de operação seguido de uma seqüência de consultas que contém dados de parâmetros, de modo que o comportamento do ponto final também altera o filtro de endereço para ser um filtro de correspondência de prefixo.</span><span class="sxs-lookup"><span data-stu-id="cedeb-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="cedeb-148">Ele usa o<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> WCF para este fim.</span><span class="sxs-lookup"><span data-stu-id="cedeb-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="cedeb-149">Instalação de operações formatters</span><span class="sxs-lookup"><span data-stu-id="cedeb-149">Installing operation formatters</span></span>  
 <span data-ttu-id="cedeb-150">Os comportamentos de operação que especificam assuntos formais são únicos.</span><span class="sxs-lookup"><span data-stu-id="cedeb-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="cedeb-151">Um desses comportamentos é sempre implementado por padrão para cada operação para criar a operação necessária.</span><span class="sxs-lookup"><span data-stu-id="cedeb-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="cedeb-152">No entanto, esses comportamentos parecem apenas mais um comportamento de operação; eles não são identificáveis por qualquer outro atributo.</span><span class="sxs-lookup"><span data-stu-id="cedeb-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="cedeb-153">Para instalar um comportamento de substituição, a implementação deve procurar comportamentos específicos de matéria que são instalados pelo carregador de tipo WCF por padrão e substituí-lo ou adicionar um comportamento compatível para executar após o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="cedeb-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="cedeb-154">Esses comportamentos de operações podem ser configurados <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> programáticamente antes de ligar ou especificando um comportamento de operação que é executado após o padrão.</span><span class="sxs-lookup"><span data-stu-id="cedeb-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="cedeb-155">No entanto, ele não pode ser facilmente configurado por um comportamento de ponto final (e, portanto, por configuração) porque o modelo de comportamento não permite que um comportamento substitua outros comportamentos ou modifique a árvore de descrição.</span><span class="sxs-lookup"><span data-stu-id="cedeb-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="cedeb-156">No cliente:</span><span class="sxs-lookup"><span data-stu-id="cedeb-156">On the client:</span></span>  
  
 <span data-ttu-id="cedeb-157">A <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementação deve ser implementada para que possa converter as solicitações em solicitações HTTP GET e delegar ao formatter original para respostas.</span><span class="sxs-lookup"><span data-stu-id="cedeb-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="cedeb-158">Isso é feito `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` chamando o método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="cedeb-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="cedeb-159">Isso deve ser `CreateChannel`feito antes de chamar.</span><span class="sxs-lookup"><span data-stu-id="cedeb-159">This must be done before calling `CreateChannel`.</span></span>  
  
```csharp  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 <span data-ttu-id="cedeb-160">No servidor:</span><span class="sxs-lookup"><span data-stu-id="cedeb-160">On the server:</span></span>  
  
- <span data-ttu-id="cedeb-161">A <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface deve ser implementada para que possa ler as solicitações HTTP GET e delegar ao formatter original para escrever respostas.</span><span class="sxs-lookup"><span data-stu-id="cedeb-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="cedeb-162">Isso é feito chamando o mesmo `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` método auxiliar que o cliente (veja a amostra de código anterior).</span><span class="sxs-lookup"><span data-stu-id="cedeb-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="cedeb-163">Isso deve ser <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> feito antes que seja chamado.</span><span class="sxs-lookup"><span data-stu-id="cedeb-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="cedeb-164">Nesta amostra, mostramos como a matéria formatéria <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>é modificada manualmente antes de chamar .</span><span class="sxs-lookup"><span data-stu-id="cedeb-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="cedeb-165">Outra maneira de conseguir a mesma coisa <xref:System.ServiceModel.ServiceHost> é obter `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` uma classe que faz as chamadas para antes de abrir (consulte documentação de hospedagem e amostras por exemplo).</span><span class="sxs-lookup"><span data-stu-id="cedeb-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="cedeb-166">Experiência do usuário</span><span class="sxs-lookup"><span data-stu-id="cedeb-166">User experience</span></span>  
 <span data-ttu-id="cedeb-167">No servidor:</span><span class="sxs-lookup"><span data-stu-id="cedeb-167">On the server:</span></span>  
  
- <span data-ttu-id="cedeb-168">A `ICalculator` implementação do servidor não precisa ser mudada.</span><span class="sxs-lookup"><span data-stu-id="cedeb-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="cedeb-169">O App.config para o serviço deve usar `messageVersion` uma vinculação POX personalizada que define o atributo `textMessageEncoding` do elemento como `None`.</span><span class="sxs-lookup"><span data-stu-id="cedeb-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- <span data-ttu-id="cedeb-170">O App.config para o serviço `EnableHttpGetRequestsBehavior` também deve especificar o costume adicionando-o à seção de extensões de comportamento e usando-o.</span><span class="sxs-lookup"><span data-stu-id="cedeb-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
- <span data-ttu-id="cedeb-171">Adicione a operação <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>para assuntos antes de chamar .</span><span class="sxs-lookup"><span data-stu-id="cedeb-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="cedeb-172">No cliente:</span><span class="sxs-lookup"><span data-stu-id="cedeb-172">On the client:</span></span>  
  
- <span data-ttu-id="cedeb-173">A implementação do cliente não precisa mudar.</span><span class="sxs-lookup"><span data-stu-id="cedeb-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="cedeb-174">O App.config para o cliente deve usar `messageVersion` uma vinculação POX personalizada que define o atributo `textMessageEncoding` do elemento para `None`.</span><span class="sxs-lookup"><span data-stu-id="cedeb-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="cedeb-175">Uma diferença em relação ao serviço é que o cliente deve habilitar endereçamento manual para que o endereço de saída para ser modificado.</span><span class="sxs-lookup"><span data-stu-id="cedeb-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- <span data-ttu-id="cedeb-176">O App.config para o cliente `EnableHttpGetRequestsBehavior` deve especificar o mesmo costume que o servidor.</span><span class="sxs-lookup"><span data-stu-id="cedeb-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="cedeb-177">Adicione a operação <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>para assuntos antes de chamar .</span><span class="sxs-lookup"><span data-stu-id="cedeb-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="cedeb-178">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="cedeb-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="cedeb-179">Todas as quatro operações (Adicionar, Subtrair, Multiplicar e Dividir) devem ter sucesso.</span><span class="sxs-lookup"><span data-stu-id="cedeb-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cedeb-180">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="cedeb-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cedeb-181">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cedeb-181">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cedeb-182">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="cedeb-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cedeb-183">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="cedeb-183">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cedeb-184">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="cedeb-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cedeb-185">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cedeb-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cedeb-186">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cedeb-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cedeb-187">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cedeb-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
