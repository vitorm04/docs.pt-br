---
title: Formatador de operação e seletor de operação
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 977a759b2c3f6d803879fc640439cd0b3465ffbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965583"
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="52743-102">Formatador de operação e seletor de operação</span><span class="sxs-lookup"><span data-stu-id="52743-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="52743-103">Este exemplo demonstra como os pontos de extensibilidade do Windows Communication Foundation (WCF) podem ser usados para permitir dados de mensagem em um formato diferente do esperado pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="52743-103">This sample demonstrates how Windows Communication Foundation (WCF) extensibility points can be used to allow message data in a different format from what WCF expects.</span></span> <span data-ttu-id="52743-104">Por padrão, os formatadores do WCF esperam que os `soap:body` parâmetros do método sejam incluídos no elemento.</span><span class="sxs-lookup"><span data-stu-id="52743-104">By default, WCF formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="52743-105">O exemplo mostra como implementar um formatador de operação personalizada que analisa dados de parâmetro de uma cadeia de caracteres de consulta HTTP GET e invoca métodos que usam esses dados.</span><span class="sxs-lookup"><span data-stu-id="52743-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="52743-106">O exemplo se baseia na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o contrato `ICalculator` de serviço.</span><span class="sxs-lookup"><span data-stu-id="52743-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="52743-107">Ele mostra como as mensagens adicionar, subtrair, multiplicar e dividir podem ser alteradas para usar HTTP GET para solicitações de cliente para servidor e HTTP POST com mensagens POX para respostas de servidor para cliente.</span><span class="sxs-lookup"><span data-stu-id="52743-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="52743-108">Para fazer isso, o exemplo fornece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="52743-108">To do so, the sample provides the following:</span></span>  
  
- <span data-ttu-id="52743-109">`QueryStringFormatter`, que implementa <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> e <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> para o cliente e servidor, respectivamente, e processa os dados na cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="52743-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
- <span data-ttu-id="52743-110">`UriOperationSelector`, que implementa <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> no servidor para executar a expedição de operação com base no nome da operação na solicitação get.</span><span class="sxs-lookup"><span data-stu-id="52743-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
- <span data-ttu-id="52743-111">`EnableHttpGetRequestsBehavior`comportamento do ponto de extremidade (e configuração correspondente), que adiciona o seletor de operação necessário ao tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="52743-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
- <span data-ttu-id="52743-112">Mostra como inserir um novo formatador de operação no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="52743-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
- <span data-ttu-id="52743-113">Neste exemplo, o cliente e o serviço são aplicativos de console (. exe).</span><span class="sxs-lookup"><span data-stu-id="52743-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52743-114">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="52743-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="52743-115">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="52743-115">Key Concepts</span></span>  
 <span data-ttu-id="52743-116">`QueryStringFormatter`-O formatador de operação é o componente no WCF que é responsável pela conversão de uma mensagem em uma matriz de objetos de parâmetro e uma matriz de objetos de parâmetro em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="52743-116">`QueryStringFormatter` - The operation formatter is the component in WCF that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="52743-117">Isso é feito no cliente usando a <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface e no servidor com a <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span><span class="sxs-lookup"><span data-stu-id="52743-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="52743-118">Essas interfaces permitem que os usuários obtenham as mensagens de solicitação e `Serialize` resposta `Deserialize` dos métodos e.</span><span class="sxs-lookup"><span data-stu-id="52743-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="52743-119">Neste exemplo, `QueryStringFormatter` implementa ambas as interfaces e é implementada no cliente e no servidor.</span><span class="sxs-lookup"><span data-stu-id="52743-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="52743-120">Quest</span><span class="sxs-lookup"><span data-stu-id="52743-120">Request:</span></span>  
  
- <span data-ttu-id="52743-121">O exemplo usa a <xref:System.ComponentModel.TypeConverter> classe para converter dados de parâmetro na mensagem de solicitação de e para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="52743-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="52743-122">Se um <xref:System.ComponentModel.TypeConverter> não estiver disponível para um tipo específico, o formatador de exemplo gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="52743-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
- <span data-ttu-id="52743-123">`IClientMessageFormatter.SerializeRequest` No método no cliente, o formatador cria um URI com o apropriado para endereçar e acrescentar o nome da operação como um sufixo.</span><span class="sxs-lookup"><span data-stu-id="52743-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="52743-124">Esse nome é usado para enviar para a operação apropriada no servidor.</span><span class="sxs-lookup"><span data-stu-id="52743-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="52743-125">Em seguida, ele pega a matriz de objetos de parâmetro e serializa os dados de parâmetro para a cadeia de caracteres de consulta de URI usando nomes <xref:System.ComponentModel.TypeConverter> de parâmetro e os valores convertidos pela classe.</span><span class="sxs-lookup"><span data-stu-id="52743-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="52743-126">As <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> propriedades <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> e são então definidas para esse URI.</span><span class="sxs-lookup"><span data-stu-id="52743-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="52743-127"><xref:System.ServiceModel.Channels.MessageProperties>é acessado <xref:System.ServiceModel.Channels.Message.Properties%2A> por meio da propriedade.</span><span class="sxs-lookup"><span data-stu-id="52743-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
- <span data-ttu-id="52743-128">No método no servidor, o formatador recupera o `Via` URI nas propriedades da mensagem de solicitação de entrada. `IDispatchMessageFormatter.DeserializeRequest`</span><span class="sxs-lookup"><span data-stu-id="52743-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="52743-129">Ele analisa os pares de nome-valor na cadeia de caracteres de consulta de URI em valores e nomes de parâmetros e usa os nomes e valores de parâmetro para preencher a matriz de parâmetros passada para o método.</span><span class="sxs-lookup"><span data-stu-id="52743-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="52743-130">Observe que a expedição da operação já ocorreu, portanto, o sufixo do nome da operação é ignorado nesse método.</span><span class="sxs-lookup"><span data-stu-id="52743-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="52743-131">Responde</span><span class="sxs-lookup"><span data-stu-id="52743-131">Response:</span></span>  
  
- <span data-ttu-id="52743-132">Neste exemplo, HTTP GET é usado somente para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="52743-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="52743-133">O formatador delega o envio da resposta ao formatador original que teria sido usado para gerar uma mensagem XML.</span><span class="sxs-lookup"><span data-stu-id="52743-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="52743-134">Uma das metas deste exemplo é mostrar como esse formatador de delegação pode ser implementado.</span><span class="sxs-lookup"><span data-stu-id="52743-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="52743-135">Classe UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="52743-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="52743-136">A <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface permite que os usuários implementem sua própria lógica para a qual operação uma determinada mensagem deve ser expedida.</span><span class="sxs-lookup"><span data-stu-id="52743-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="52743-137">Neste exemplo, `UriPathSuffixOperationSelector` deve ser implementado no servidor para selecionar a operação apropriada porque o nome da operação está incluído no URI Get http em vez de um cabeçalho Action na mensagem.</span><span class="sxs-lookup"><span data-stu-id="52743-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="52743-138">O exemplo é configurado para permitir apenas nomes de operação que não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="52743-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="52743-139">O `SelectOperation` método usa a mensagem de entrada e pesquisa o `Via` URI em suas propriedades de mensagem.</span><span class="sxs-lookup"><span data-stu-id="52743-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="52743-140">Ele extrai o sufixo de nome de operação do URI, pesquisa uma tabela interna para obter o nome da operação para a qual a mensagem deve ser expedida e retorna esse nome de operação.</span><span class="sxs-lookup"><span data-stu-id="52743-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="52743-141">Classe EnableHttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="52743-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="52743-142">O `UriPathSuffixOperationSelector` componente pode ser configurado programaticamente ou por meio de um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="52743-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="52743-143">O exemplo implementa o `EnableHttpGetRequestsBehavior` comportamento, que é especificado no arquivo de configuração de aplicativo do serviço.</span><span class="sxs-lookup"><span data-stu-id="52743-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="52743-144">No servidor:</span><span class="sxs-lookup"><span data-stu-id="52743-144">On the server:</span></span>  
  
 <span data-ttu-id="52743-145">O <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> é definido para a <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementação.</span><span class="sxs-lookup"><span data-stu-id="52743-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="52743-146">Por padrão, o WCF usa um filtro de endereço de correspondência exata.</span><span class="sxs-lookup"><span data-stu-id="52743-146">By default, WCF uses an exact-match address filter.</span></span> <span data-ttu-id="52743-147">O URI na mensagem de entrada contém um sufixo de nome de operação seguido por uma cadeia de caracteres de consulta que contém dados de parâmetro, portanto, o comportamento do ponto de extremidade também altera o filtro de endereço para ser um filtro de correspondência de prefixo.</span><span class="sxs-lookup"><span data-stu-id="52743-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="52743-148">Ele usa o WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="52743-148">It uses the WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="52743-149">Instalando formatadores de operação</span><span class="sxs-lookup"><span data-stu-id="52743-149">Installing operation formatters</span></span>  
 <span data-ttu-id="52743-150">Comportamentos de operação que especificam formatadores são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="52743-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="52743-151">Um desses comportamentos é sempre implementado por padrão para cada operação para criar o formatador de operação necessário.</span><span class="sxs-lookup"><span data-stu-id="52743-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="52743-152">No entanto, esses comportamentos parecem apenas outro comportamento de operação; Eles não são identificáveis por nenhum outro atributo.</span><span class="sxs-lookup"><span data-stu-id="52743-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="52743-153">Para instalar um comportamento de substituição, a implementação deve procurar comportamentos de formatador específicos instalados pelo carregador do tipo WCF por padrão e substituí-lo ou adicionar um comportamento compatível para execução após o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="52743-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the WCF type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="52743-154">Esses comportamentos de formatadores de operação podem ser configurados programaticamente antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> ou especificando um comportamento de operação que é executado após o padrão.</span><span class="sxs-lookup"><span data-stu-id="52743-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="52743-155">No entanto, ele não pode ser facilmente configurado por um comportamento de ponto de extremidade (e, portanto, por configuração) porque o modelo de comportamento não permite que um comportamento substitua outros comportamentos ou, de outra forma, modifica a árvore de descrição.</span><span class="sxs-lookup"><span data-stu-id="52743-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="52743-156">No cliente:</span><span class="sxs-lookup"><span data-stu-id="52743-156">On the client:</span></span>  
  
 <span data-ttu-id="52743-157">A <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementação deve ser implementada para que possa converter as solicitações em solicitações HTTP Get e delegar para o formatador original para respostas.</span><span class="sxs-lookup"><span data-stu-id="52743-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="52743-158">Isso é feito chamando o `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="52743-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="52743-159">Isso deve ser feito antes de `CreateChannel`chamar.</span><span class="sxs-lookup"><span data-stu-id="52743-159">This must be done before calling `CreateChannel`.</span></span>  
  
```  
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
  
 <span data-ttu-id="52743-160">No servidor:</span><span class="sxs-lookup"><span data-stu-id="52743-160">On the server:</span></span>  
  
- <span data-ttu-id="52743-161">A <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface deve ser implementada para que possa ler solicitações HTTP Get e delegar ao formatador original para gravar respostas.</span><span class="sxs-lookup"><span data-stu-id="52743-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="52743-162">Isso é feito chamando o mesmo `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` método auxiliar que o cliente (consulte o exemplo de código anterior).</span><span class="sxs-lookup"><span data-stu-id="52743-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
- <span data-ttu-id="52743-163">Isso deve ser feito antes <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> de o ser chamado.</span><span class="sxs-lookup"><span data-stu-id="52743-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="52743-164">Neste exemplo, mostramos como o formatador é modificado manualmente antes de <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>chamar.</span><span class="sxs-lookup"><span data-stu-id="52743-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="52743-165">Outra maneira de obter a mesma coisa é derivar uma classe de <xref:System.ServiceModel.ServiceHost> que faça as `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` chamadas antes de abrir (consulte a documentação e os exemplos de hospedagem para obter exemplos).</span><span class="sxs-lookup"><span data-stu-id="52743-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="52743-166">Experiência do usuário</span><span class="sxs-lookup"><span data-stu-id="52743-166">User experience</span></span>  
 <span data-ttu-id="52743-167">No servidor:</span><span class="sxs-lookup"><span data-stu-id="52743-167">On the server:</span></span>  
  
- <span data-ttu-id="52743-168">A implementação `ICalculator` do servidor não precisa ser alterada.</span><span class="sxs-lookup"><span data-stu-id="52743-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
- <span data-ttu-id="52743-169">O app. config do serviço deve usar uma associação Pox personalizada que define o `messageVersion` atributo `textMessageEncoding` do elemento como `None`.</span><span class="sxs-lookup"><span data-stu-id="52743-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
- <span data-ttu-id="52743-170">O app. config para o serviço também deve especificar o personalizado `EnableHttpGetRequestsBehavior` adicionando-o à seção de extensões de comportamento e usando-o.</span><span class="sxs-lookup"><span data-stu-id="52743-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
- <span data-ttu-id="52743-171">Adicione os formatadores de operação <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>antes de chamar.</span><span class="sxs-lookup"><span data-stu-id="52743-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="52743-172">No cliente:</span><span class="sxs-lookup"><span data-stu-id="52743-172">On the client:</span></span>  
  
- <span data-ttu-id="52743-173">A implementação do cliente não precisa ser alterada.</span><span class="sxs-lookup"><span data-stu-id="52743-173">The client implementation does not need to change.</span></span>  
  
- <span data-ttu-id="52743-174">O app. config do cliente deve usar uma associação Pox personalizada que define o `messageVersion` atributo `textMessageEncoding` do elemento como `None`.</span><span class="sxs-lookup"><span data-stu-id="52743-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="52743-175">Uma diferença do serviço é que o cliente deve habilitar o endereçamento manual para que o endereço de saída possa ser modificado.</span><span class="sxs-lookup"><span data-stu-id="52743-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
- <span data-ttu-id="52743-176">O app. config do cliente deve especificar o mesmo personalizado `EnableHttpGetRequestsBehavior` que o servidor.</span><span class="sxs-lookup"><span data-stu-id="52743-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
- <span data-ttu-id="52743-177">Adicione os formatadores de operação <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>antes de chamar.</span><span class="sxs-lookup"><span data-stu-id="52743-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="52743-178">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="52743-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="52743-179">Todas as quatro operações (adicionar, subtrair, multiplicar e dividir) devem ter sucesso.</span><span class="sxs-lookup"><span data-stu-id="52743-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52743-180">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="52743-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52743-181">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="52743-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52743-182">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="52743-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52743-183">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="52743-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52743-184">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="52743-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="52743-185">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52743-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="52743-186">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52743-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="52743-187">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52743-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
