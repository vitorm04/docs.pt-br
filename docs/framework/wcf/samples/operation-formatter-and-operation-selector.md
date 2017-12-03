---
title: "Formatador de operação e seletor de operação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3fd8b59cd69807928b1a441d1bfb57f82d072288
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="operation-formatter-and-operation-selector"></a><span data-ttu-id="d8556-102">Formatador de operação e seletor de operação</span><span class="sxs-lookup"><span data-stu-id="d8556-102">Operation Formatter and Operation Selector</span></span>
<span data-ttu-id="d8556-103">Este exemplo demonstra como [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pontos de extensibilidade podem ser usados para permitir que os dados de mensagem em um formato diferente daquele que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] espera.</span><span class="sxs-lookup"><span data-stu-id="d8556-103">This sample demonstrates how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extensibility points can be used to allow message data in a different format from what [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects.</span></span> <span data-ttu-id="d8556-104">Por padrão, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] formatadores esperam parâmetros do método a ser incluído no `soap:body` elemento.</span><span class="sxs-lookup"><span data-stu-id="d8556-104">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] formatters expect method parameters to be included under the `soap:body` element.</span></span> <span data-ttu-id="d8556-105">O exemplo mostra como implementar um formatador de operação personalizada que analisa dados de parâmetro de uma cadeia de caracteres de consulta HTTP GET em vez disso e invoca métodos usando esses dados.</span><span class="sxs-lookup"><span data-stu-id="d8556-105">The sample shows how to implement a custom operation formatter that parses parameter data from an HTTP GET query string instead and invokes methods using that data.</span></span>  
  
 <span data-ttu-id="d8556-106">O exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="d8556-106">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="d8556-107">Ele mostra como adicionar, subtrair, multiplicar e mensagens de divisão podem ser alteradas para usar o HTTP GET para solicitações de cliente para servidor e HTTP POST com POX mensagens de respostas do servidor para cliente.</span><span class="sxs-lookup"><span data-stu-id="d8556-107">It shows how Add, Subtract, Multiply, and Divide messages can be changed to use HTTP GET for client-to-server requests and HTTP POST with POX messages for server-to-client responses.</span></span>  
  
 <span data-ttu-id="d8556-108">Para fazer isso, o exemplo fornece o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d8556-108">To do so, the sample provides the following:</span></span>  
  
-   <span data-ttu-id="d8556-109">`QueryStringFormatter`, que implementa <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> e <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> para o cliente e servidor, respectivamente e processa os dados na cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="d8556-109">`QueryStringFormatter`, which implements <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> for the client and server, respectively, and processes the data in the query string.</span></span>  
  
-   <span data-ttu-id="d8556-110">`UriOperationSelector`, que implementa <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> no servidor para executar com base no nome de operação em que a solicitação de obtenção de expedição de operação.</span><span class="sxs-lookup"><span data-stu-id="d8556-110">`UriOperationSelector`, which implements <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> on the server to perform operation dispatch based on the operation name in the GET request.</span></span>  
  
-   <span data-ttu-id="d8556-111">`EnableHttpGetRequestsBehavior`ponto de extremidade comportamento (e a configuração correspondente), que adiciona o seletor de operação necessária para o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d8556-111">`EnableHttpGetRequestsBehavior` endpoint behavior (and corresponding configuration), which adds the necessary operation selector to the runtime.</span></span>  
  
-   <span data-ttu-id="d8556-112">Mostra como inserir um novo formatador de operação no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d8556-112">Shows how to insert a new operation formatter into the runtime.</span></span>  
  
-   <span data-ttu-id="d8556-113">Neste exemplo, o cliente e o serviço são aplicativos de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="d8556-113">In this sample, both the client and the service are console applications (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8556-114">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="d8556-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="key-concepts"></a><span data-ttu-id="d8556-115">Conceitos Principais</span><span class="sxs-lookup"><span data-stu-id="d8556-115">Key Concepts</span></span>  
 <span data-ttu-id="d8556-116">`QueryStringFormatter`-O formatador de operação é o componente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que é responsável por converter uma mensagem em uma matriz de objetos de parâmetro e uma matriz de objetos de parâmetro em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="d8556-116">`QueryStringFormatter` - The operation formatter is the component in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that is responsible for converting a message into an array of parameter objects and an array of parameter objects into a message.</span></span> <span data-ttu-id="d8556-117">Isso é feito no cliente usando o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface e no servidor com o <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span><span class="sxs-lookup"><span data-stu-id="d8556-117">This is done on the client using the <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface and on the server with the <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface.</span></span> <span data-ttu-id="d8556-118">Essas interfaces permitem que os usuários obtenham as mensagens de solicitação e resposta do `Serialize` e `Deserialize` métodos.</span><span class="sxs-lookup"><span data-stu-id="d8556-118">These interfaces enable users to get the request and response messages from the `Serialize` and `Deserialize` methods.</span></span>  
  
 <span data-ttu-id="d8556-119">Neste exemplo, `QueryStringFormatter` implementa duas interfaces e é implementado no cliente e no servidor.</span><span class="sxs-lookup"><span data-stu-id="d8556-119">In this sample, `QueryStringFormatter` implements both of these interfaces and is implemented on the client and server.</span></span>  
  
 <span data-ttu-id="d8556-120">Solicitação:</span><span class="sxs-lookup"><span data-stu-id="d8556-120">Request:</span></span>  
  
-   <span data-ttu-id="d8556-121">O exemplo usa o <xref:System.ComponentModel.TypeConverter> classe para converter dados de parâmetro na mensagem de solicitação de e para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d8556-121">The sample uses the <xref:System.ComponentModel.TypeConverter> class to convert parameter data in the request message to and from strings.</span></span> <span data-ttu-id="d8556-122">Se um <xref:System.ComponentModel.TypeConverter> não está disponível para um tipo específico, o lance formatador de exemplo uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d8556-122">If a <xref:System.ComponentModel.TypeConverter> is not available for a specific type, the sample formatter throws an exception.</span></span>  
  
-   <span data-ttu-id="d8556-123">No `IClientMessageFormatter.SerializeRequest` método no cliente, o formatador cria um URI com o endereço apropriado e anexa o nome da operação como um sufixo.</span><span class="sxs-lookup"><span data-stu-id="d8556-123">In the `IClientMessageFormatter.SerializeRequest` method on the client, the formatter creates a URI with the appropriate To address and appends the operation name as a suffix.</span></span> <span data-ttu-id="d8556-124">Esse nome é usado para o qual expedir a operação apropriada no servidor.</span><span class="sxs-lookup"><span data-stu-id="d8556-124">This name is used to dispatch to the appropriate operation on the server.</span></span> <span data-ttu-id="d8556-125">Em seguida, usa a matriz de objetos de parâmetro e serializa os dados de parâmetro para a cadeia de caracteres de consulta URI usando nomes de parâmetro e os valores convertidos pelo <xref:System.ComponentModel.TypeConverter> classe.</span><span class="sxs-lookup"><span data-stu-id="d8556-125">It then takes the array of parameter objects and serializes the parameter data to the URI query string using parameter names and the values converted by the <xref:System.ComponentModel.TypeConverter> class.</span></span> <span data-ttu-id="d8556-126">O <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> e <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> propriedades são definidas para esse URI.</span><span class="sxs-lookup"><span data-stu-id="d8556-126">The <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> and <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> properties are then set to this URI.</span></span> <span data-ttu-id="d8556-127"><xref:System.ServiceModel.Channels.MessageProperties>é acessada por meio de <xref:System.ServiceModel.Channels.Message.Properties%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d8556-127"><xref:System.ServiceModel.Channels.MessageProperties> is accessed through the <xref:System.ServiceModel.Channels.Message.Properties%2A> property.</span></span>  
  
-   <span data-ttu-id="d8556-128">No `IDispatchMessageFormatter.DeserializeRequest` método no servidor, o formatador recupera o `Via` URI nas propriedades de mensagem de solicitação de entrada.</span><span class="sxs-lookup"><span data-stu-id="d8556-128">In the `IDispatchMessageFormatter.DeserializeRequest` method on the server, the formatter retrieves the `Via` URI in the incoming request message properties.</span></span> <span data-ttu-id="d8556-129">Ele analisa os pares nome-valor na cadeia de caracteres de consulta URI em valores e nomes de parâmetro e usa os nomes de parâmetro e valores para preencher a matriz de parâmetros passados para o método.</span><span class="sxs-lookup"><span data-stu-id="d8556-129">It parses the name-value pairs in the URI query string into parameter names and values and uses the parameter names and values to populate the array of parameters passed into the method.</span></span> <span data-ttu-id="d8556-130">Observe que a expedição de operação já ocorreu, portanto, o sufixo de nome de operação é ignorado nesse método.</span><span class="sxs-lookup"><span data-stu-id="d8556-130">Note that operation dispatch has already occurred, so the operation name suffix is ignored in this method.</span></span>  
  
 <span data-ttu-id="d8556-131">Resposta:</span><span class="sxs-lookup"><span data-stu-id="d8556-131">Response:</span></span>  
  
-   <span data-ttu-id="d8556-132">Neste exemplo, HTTP GET é usado apenas para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="d8556-132">In this sample, HTTP GET is used only for the request.</span></span> <span data-ttu-id="d8556-133">O formatador delega o envio da resposta para o formatador original que seria usado para gerar uma mensagem XML.</span><span class="sxs-lookup"><span data-stu-id="d8556-133">The formatter delegates the sending of the response to the original formatter that would have been used to generate an XML message.</span></span> <span data-ttu-id="d8556-134">Um dos objetivos deste exemplo é mostrar como tal um formatador de delegação pode ser implementado.</span><span class="sxs-lookup"><span data-stu-id="d8556-134">One of the goals of this sample is to show how such a delegating formatter can be implemented.</span></span>  
  
### <a name="uripathsuffixoperationselector-class"></a><span data-ttu-id="d8556-135">Classe UriPathSuffixOperationSelector</span><span class="sxs-lookup"><span data-stu-id="d8556-135">UriPathSuffixOperationSelector Class</span></span>  
 <span data-ttu-id="d8556-136">O <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface permite que os usuários implementar sua própria lógica para operação de que uma mensagem específica deve ser distribuída.</span><span class="sxs-lookup"><span data-stu-id="d8556-136">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface enables users to implement their own logic for which operation a particular message should be dispatched.</span></span>  
  
 <span data-ttu-id="d8556-137">Neste exemplo, `UriPathSuffixOperationSelector` devem ser implementados no servidor para selecionar a operação apropriada, como o nome da operação está incluído no URI GET HTTP em vez de um cabeçalho de ação na mensagem.</span><span class="sxs-lookup"><span data-stu-id="d8556-137">In this sample, `UriPathSuffixOperationSelector` must be implemented on the server to select the appropriate operation because the operation name is included in the HTTP GET URI rather than an action header in the message.</span></span> <span data-ttu-id="d8556-138">O exemplo é configurado para permitir que os nomes de operação somente maiusculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d8556-138">The sample is set up to allow only case-insensitive operation names.</span></span>  
  
 <span data-ttu-id="d8556-139">O `SelectOperation` método recebe a mensagem de entrada e procura o `Via` URI em suas propriedades de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d8556-139">The `SelectOperation` method takes the incoming message and looks up the `Via` URI in its message properties.</span></span> <span data-ttu-id="d8556-140">Extrai o sufixo de nome de operação do URI, pesquise uma tabela interna para obter o nome da operação que a mensagem deve ser distribuída para e retorna esse nome de operação.</span><span class="sxs-lookup"><span data-stu-id="d8556-140">It extracts the operation name suffix from the URI, looks up an internal table to get the operation name that the message should be dispatched to, and returns that operation name.</span></span>  
  
### <a name="enablehttpgetrequestsbehavior-class"></a><span data-ttu-id="d8556-141">Classe EnableHttpGetRequestsBehavior</span><span class="sxs-lookup"><span data-stu-id="d8556-141">EnableHttpGetRequestsBehavior Class</span></span>  
 <span data-ttu-id="d8556-142">O `UriPathSuffixOperationSelector` componente pode ser configurado programaticamente ou por meio de um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d8556-142">The `UriPathSuffixOperationSelector` component can be set up programmatically or through an endpoint behavior.</span></span> <span data-ttu-id="d8556-143">O exemplo implementa o `EnableHttpGetRequestsBehavior` comportamento, que é especificado no arquivo de configuração de aplicativo do serviço.</span><span class="sxs-lookup"><span data-stu-id="d8556-143">The sample implements the `EnableHttpGetRequestsBehavior` behavior, which is specified in service’s application configuration file.</span></span>  
  
 <span data-ttu-id="d8556-144">No servidor:</span><span class="sxs-lookup"><span data-stu-id="d8556-144">On the server:</span></span>  
  
 <span data-ttu-id="d8556-145">O <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> é definido como o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementação.</span><span class="sxs-lookup"><span data-stu-id="d8556-145">The <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> is set to the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementation.</span></span>  
  
 <span data-ttu-id="d8556-146">Por padrão, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa um filtro de endereço de correspondência exata.</span><span class="sxs-lookup"><span data-stu-id="d8556-146">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses an exact-match address filter.</span></span> <span data-ttu-id="d8556-147">O URI na mensagem de entrada contém um sufixo de nome de operação seguido por uma cadeia de caracteres de consulta que contém os dados de parâmetro, portanto o comportamento de ponto de extremidade também altera o filtro de endereço para ser um prefixo correspondem ao filtro.</span><span class="sxs-lookup"><span data-stu-id="d8556-147">The URI on the incoming message contains an operation name suffix followed by a query string that contains parameter data, so the endpoint behavior also changes the address filter to be a prefix match filter.</span></span> <span data-ttu-id="d8556-148">Ele usa o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="d8556-148">It uses the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> for this purpose.</span></span>  
  
### <a name="installing-operation-formatters"></a><span data-ttu-id="d8556-149">Instalando os formatadores de operação</span><span class="sxs-lookup"><span data-stu-id="d8556-149">Installing operation formatters</span></span>  
 <span data-ttu-id="d8556-150">Comportamentos de operação que especificam os formatadores são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="d8556-150">Operation behaviors that specify formatters are unique.</span></span> <span data-ttu-id="d8556-151">Um tal comportamento sempre é implementado por padrão para cada operação para criar o formatador de operação necessária.</span><span class="sxs-lookup"><span data-stu-id="d8556-151">One such behavior is always implemented by default for every operation to create the necessary operation formatter.</span></span> <span data-ttu-id="d8556-152">No entanto, esses comportamentos se parecer com o comportamento de qualquer outra operação; eles não são identificados por qualquer outro atributo.</span><span class="sxs-lookup"><span data-stu-id="d8556-152">However, these behaviors look like just another operation behavior; they are not identifiable by any other attribute.</span></span> <span data-ttu-id="d8556-153">Para instalar um comportamento de substituição, a implementação deve procurar comportamentos de formatador específicos que são instalados pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] carregador de tipo por padrão e substituí-lo ou adicionar um comportamento compatível para ser executada após o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="d8556-153">To install a replacement behavior, the implementation must look for specific formatter behaviors that are installed by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] type loader by default and either replace it or add a compatible behavior to run after the default behavior.</span></span>  
  
 <span data-ttu-id="d8556-154">Esses comportamentos de formatadores de operação podem ser configurados por meio de programação antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> ou especificando um comportamento de operação que é executado após o padrão.</span><span class="sxs-lookup"><span data-stu-id="d8556-154">These operation formatters behaviors can be set up programmatically prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> or by specifying an operation behavior that is executed after the default one.</span></span> <span data-ttu-id="d8556-155">No entanto, ele não pode ser facilmente configurado por um comportamento de ponto de extremidade (e, portanto, pela configuração) porque o modelo de comportamento não permite um comportamento substituir outros comportamentos ou modificar a árvore de descrição.</span><span class="sxs-lookup"><span data-stu-id="d8556-155">However, it cannot easily be set up by an endpoint behavior (and therefore by configuration) because the behavior model does not allow a behavior to replace other behaviors or otherwise modify the description tree.</span></span>  
  
 <span data-ttu-id="d8556-156">No cliente:</span><span class="sxs-lookup"><span data-stu-id="d8556-156">On the client:</span></span>  
  
 <span data-ttu-id="d8556-157">O <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementação deve ser implementada para que ele possa converter as solicitações em solicitações HTTP GET e delegar para o formatador original para respostas.</span><span class="sxs-lookup"><span data-stu-id="d8556-157">The <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementation must be implemented so that it can convert the requests into HTTP GET requests and delegate to the original formatter for responses.</span></span> <span data-ttu-id="d8556-158">Isso é feito chamando a `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` método auxiliar.</span><span class="sxs-lookup"><span data-stu-id="d8556-158">This is done by calling the `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method.</span></span>  
  
 <span data-ttu-id="d8556-159">Isso deve ser feito antes de chamar `CreateChannel`.</span><span class="sxs-lookup"><span data-stu-id="d8556-159">This must be done before calling `CreateChannel`.</span></span>  
  
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
  
 <span data-ttu-id="d8556-160">No servidor:</span><span class="sxs-lookup"><span data-stu-id="d8556-160">On the server:</span></span>  
  
-   <span data-ttu-id="d8556-161">O <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface deve ser implementada para que ele possa ler solicitações HTTP GET e delegar para o formatador original para gravação de respostas.</span><span class="sxs-lookup"><span data-stu-id="d8556-161">The <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface must be implemented so that it can read HTTP GET requests and delegate to the original formatter for writing responses.</span></span> <span data-ttu-id="d8556-162">Isso é feito chamando a mesma `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` o método auxiliar do cliente (consulte o exemplo de código anterior).</span><span class="sxs-lookup"><span data-stu-id="d8556-162">This is done by calling the same `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` helper method as the client (see the previous code sample).</span></span>  
  
-   <span data-ttu-id="d8556-163">Isso deve ser feito antes de <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="d8556-163">This must be done before <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="d8556-164">Neste exemplo, mostramos como o formatador manualmente é modificado antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8556-164">In this sample, we show how the formatter is manually modified before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="d8556-165">É outra maneira de fazer a mesma coisa derivar uma classe de <xref:System.ServiceModel.ServiceHost> que faz as chamadas para `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` antes de abertura (consulte documentação e exemplos para obter exemplos de hospedagem).</span><span class="sxs-lookup"><span data-stu-id="d8556-165">Another way to achieve the same thing is to derive a class from <xref:System.ServiceModel.ServiceHost> that makes the calls to `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` before opening (please see hosting documentation and samples for examples).</span></span>  
  
### <a name="user-experience"></a><span data-ttu-id="d8556-166">Experiência do usuário</span><span class="sxs-lookup"><span data-stu-id="d8556-166">User experience</span></span>  
 <span data-ttu-id="d8556-167">No servidor:</span><span class="sxs-lookup"><span data-stu-id="d8556-167">On the server:</span></span>  
  
-   <span data-ttu-id="d8556-168">O servidor `ICalculator` implementação não precisa alterar.</span><span class="sxs-lookup"><span data-stu-id="d8556-168">The server `ICalculator` implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="d8556-169">O App. config para o serviço deve usar uma associação personalizada POX que define o `messageVersion` atributo do `textMessageEncoding` elemento `None`.</span><span class="sxs-lookup"><span data-stu-id="d8556-169">The App.config for the service must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span>  
  
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
  
-   <span data-ttu-id="d8556-170">O App. config para o serviço também deve especificar personalizado `EnableHttpGetRequestsBehavior` adicionando-o para a seção de extensões de comportamento e usá-lo.</span><span class="sxs-lookup"><span data-stu-id="d8556-170">The App.config for the service also must specify the custom `EnableHttpGetRequestsBehavior` by adding it to the behavior extensions section and using it.</span></span>  
  
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
  
-   <span data-ttu-id="d8556-171">Adicionar formatadores de operação antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8556-171">Add operation formatters before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
 <span data-ttu-id="d8556-172">No cliente:</span><span class="sxs-lookup"><span data-stu-id="d8556-172">On the client:</span></span>  
  
-   <span data-ttu-id="d8556-173">A implementação do cliente não precisa alterar.</span><span class="sxs-lookup"><span data-stu-id="d8556-173">The client implementation does not need to change.</span></span>  
  
-   <span data-ttu-id="d8556-174">O App. config para o cliente deve usar uma associação personalizada POX que define o `messageVersion` atributo do `textMessageEncoding` elemento `None`.</span><span class="sxs-lookup"><span data-stu-id="d8556-174">The App.config for the client must use a custom POX binding that sets the `messageVersion` attribute of the `textMessageEncoding` element to `None`.</span></span> <span data-ttu-id="d8556-175">Uma diferença entre o serviço é que o cliente deve habilitar o endereçamento manual para que a saída para o endereço pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="d8556-175">One difference from the service is that the client must enable manual addressing so that the outgoing To address can be modified.</span></span>  
  
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
  
-   <span data-ttu-id="d8556-176">O App. config para o cliente deve especificar o mesmo personalizado `EnableHttpGetRequestsBehavior` como o servidor.</span><span class="sxs-lookup"><span data-stu-id="d8556-176">The App.config for the client must specify the same custom `EnableHttpGetRequestsBehavior` as the server.</span></span>  
  
-   <span data-ttu-id="d8556-177">Adicionar formatadores de operação antes de chamar <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span><span class="sxs-lookup"><span data-stu-id="d8556-177">Add operation formatters before calling <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.</span></span>  
  
 <span data-ttu-id="d8556-178">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="d8556-178">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d8556-179">Todas as quatro operações (Adicionar, subtrair, multiplicar e dividir) deve ter êxito.</span><span class="sxs-lookup"><span data-stu-id="d8556-179">All four operations (Add, Subtract, Multiply, and Divide) must succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d8556-180">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d8556-180">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d8556-181">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d8556-181">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d8556-182">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d8556-182">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8556-183">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d8556-183">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d8556-184">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d8556-184">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d8556-185">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d8556-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d8556-186">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d8556-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d8556-187">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d8556-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8556-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8556-188">See Also</span></span>
