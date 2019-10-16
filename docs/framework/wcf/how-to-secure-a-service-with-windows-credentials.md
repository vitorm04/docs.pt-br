---
title: Como proteger um serviço com credenciais Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: d02e697b23b6c745a59f3c9c37dd9c565f2f710e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320929"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="2b04f-102">Como proteger um serviço com credenciais Windows</span><span class="sxs-lookup"><span data-stu-id="2b04f-102">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="2b04f-103">Este tópico mostra como habilitar a segurança de transporte em um serviço de Windows Communication Foundation (WCF) que reside em um domínio do Windows e é chamado por clientes no mesmo domínio.</span><span class="sxs-lookup"><span data-stu-id="2b04f-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="2b04f-104">Para obter mais informações sobre esse cenário, consulte [segurança de transporte com autenticação do Windows](./feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2b04f-104">For more information about this scenario, see [Transport Security with Windows Authentication](./feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="2b04f-105">Para um aplicativo de exemplo, consulte o exemplo de [WSHttpBinding](./samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2b04f-105">For a sample application, see the [WSHttpBinding](./samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="2b04f-106">Este tópico pressupõe que você tenha uma interface de contrato e implementação existentes já definidos e que o adicione a isso.</span><span class="sxs-lookup"><span data-stu-id="2b04f-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="2b04f-107">Você também pode modificar um serviço e cliente existentes.</span><span class="sxs-lookup"><span data-stu-id="2b04f-107">You can also modify an existing service and client.</span></span>

<span data-ttu-id="2b04f-108">Você pode proteger um serviço com as credenciais do Windows completamente no código.</span><span class="sxs-lookup"><span data-stu-id="2b04f-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="2b04f-109">Como alternativa, você pode omitir parte do código usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b04f-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="2b04f-110">Este tópico mostra as duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="2b04f-110">This topic shows both ways.</span></span> <span data-ttu-id="2b04f-111">Certifique-se de usar apenas uma das maneiras, não ambas.</span><span class="sxs-lookup"><span data-stu-id="2b04f-111">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="2b04f-112">Os três primeiros procedimentos mostram como proteger o serviço usando código.</span><span class="sxs-lookup"><span data-stu-id="2b04f-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="2b04f-113">O quarto e o quinto procedimento mostram como fazer isso com um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b04f-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="2b04f-114">Usando código</span><span class="sxs-lookup"><span data-stu-id="2b04f-114">Using Code</span></span>

<span data-ttu-id="2b04f-115">O código completo para o serviço e o cliente está na seção de exemplo no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2b04f-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="2b04f-116">O primeiro procedimento percorre a criação e a configuração de uma classe <xref:System.ServiceModel.WSHttpBinding> no código.</span><span class="sxs-lookup"><span data-stu-id="2b04f-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="2b04f-117">A associação usa o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="2b04f-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="2b04f-118">A mesma associação é usada no cliente.</span><span class="sxs-lookup"><span data-stu-id="2b04f-118">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="2b04f-119">Para criar uma WSHttpBinding que usa as credenciais do Windows e a segurança da mensagem</span><span class="sxs-lookup"><span data-stu-id="2b04f-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="2b04f-120">O código desse procedimento é inserido no início do método `Run` da classe `Test` no código do serviço na seção de exemplo.</span><span class="sxs-lookup"><span data-stu-id="2b04f-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="2b04f-121">Crie uma instância da classe <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="2b04f-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="2b04f-122">Defina a propriedade <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> da classe <xref:System.ServiceModel.WSHttpSecurity> como <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="2b04f-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="2b04f-123">Defina a propriedade <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> da classe <xref:System.ServiceModel.MessageSecurityOverHttp> como <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="2b04f-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="2b04f-124">O código para esse procedimento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2b04f-124">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="2b04f-125">Usando a associação em um serviço</span><span class="sxs-lookup"><span data-stu-id="2b04f-125">Using the Binding in a Service</span></span>

<span data-ttu-id="2b04f-126">Este é o segundo procedimento, que mostra como usar a associação em um serviço hospedado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2b04f-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="2b04f-127">Para obter mais informações sobre serviços de hospedagem, consulte [serviços de hospedagem](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="2b04f-127">For more information about hosting services see [Hosting Services](hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="2b04f-128">Para usar uma associação em um serviço</span><span class="sxs-lookup"><span data-stu-id="2b04f-128">To use a binding in a service</span></span>

1. <span data-ttu-id="2b04f-129">Insira o código deste procedimento após o código do procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="2b04f-129">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="2b04f-130">Crie uma variável <xref:System.Type> chamada `contractType` e atribua-a ao tipo da interface (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="2b04f-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="2b04f-131">Ao usar Visual Basic, use o operador `GetType`; ao usar C#, use a palavra-chave `typeof`.</span><span class="sxs-lookup"><span data-stu-id="2b04f-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="2b04f-132">Crie uma segunda variável <xref:System.Type> chamada `serviceType` e atribua a ela o tipo do contrato implementado (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="2b04f-132">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="2b04f-133">Crie uma instância da classe <xref:System.Uri> denominada `baseAddress` com o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="2b04f-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="2b04f-134">O endereço base deve ter um esquema que corresponda ao transporte.</span><span class="sxs-lookup"><span data-stu-id="2b04f-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="2b04f-135">Nesse caso, o esquema de transporte é HTTP e o endereço inclui o Uniform Resource Identifier especial (URI) "localhost" e um número de porta (8036), bem como um endereço de ponto de extremidade base ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span><span class="sxs-lookup"><span data-stu-id="2b04f-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="2b04f-136">Crie uma instância da classe <xref:System.ServiceModel.ServiceHost> com as variáveis `serviceType` e `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="2b04f-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="2b04f-137">Adicione um ponto de extremidade ao serviço usando o `contractType`, a associação e um nome de ponto de extremidade (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="2b04f-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="2b04f-138">Um cliente deve concatenar o endereço base e o nome do ponto de extremidade ao iniciar uma chamada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="2b04f-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="2b04f-139">Chame o método <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="2b04f-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="2b04f-140">O código para esse procedimento é mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="2b04f-140">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="2b04f-141">Usando a associação em um cliente</span><span class="sxs-lookup"><span data-stu-id="2b04f-141">Using the Binding in a Client</span></span>

<span data-ttu-id="2b04f-142">Este procedimento mostra como gerar um proxy que se comunica com o serviço.</span><span class="sxs-lookup"><span data-stu-id="2b04f-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="2b04f-143">O proxy é gerado com a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) que usa os metadados de serviço para criar o proxy.</span><span class="sxs-lookup"><span data-stu-id="2b04f-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="2b04f-144">Esse procedimento também cria uma instância da classe <xref:System.ServiceModel.WSHttpBinding> para se comunicar com o serviço e, em seguida, chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="2b04f-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="2b04f-145">Este exemplo usa apenas o código para criar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2b04f-145">This example uses only code to create the client.</span></span> <span data-ttu-id="2b04f-146">Como alternativa, você pode usar um arquivo de configuração, que é mostrado na seção após este procedimento.</span><span class="sxs-lookup"><span data-stu-id="2b04f-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="2b04f-147">Para usar uma associação em um cliente com código</span><span class="sxs-lookup"><span data-stu-id="2b04f-147">To use a binding in a client with code</span></span>

1. <span data-ttu-id="2b04f-148">Use a ferramenta SvcUtil. exe para gerar o código de proxy a partir dos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="2b04f-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="2b04f-149">Para obter mais informações, consulte [como: criar um cliente](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="2b04f-149">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="2b04f-150">O código de proxy gerado herda da classe <xref:System.ServiceModel.ClientBase%601>, que garante que cada cliente tenha os construtores, métodos e propriedades necessários para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="2b04f-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="2b04f-151">Neste exemplo, o código gerado inclui a classe `CalculatorClient`, que implementa a interface `ICalculator`, permitindo a compatibilidade com o código do serviço.</span><span class="sxs-lookup"><span data-stu-id="2b04f-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="2b04f-152">O código deste procedimento é inserido no início do método `Main` do programa cliente.</span><span class="sxs-lookup"><span data-stu-id="2b04f-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="2b04f-153">Crie uma instância da classe <xref:System.ServiceModel.WSHttpBinding> e defina seu modo de segurança como `Message` e seu tipo de credencial de cliente como `Windows`.</span><span class="sxs-lookup"><span data-stu-id="2b04f-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="2b04f-154">O exemplo nomeia a variável `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="2b04f-154">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="2b04f-155">Crie uma instância da classe <xref:System.ServiceModel.EndpointAddress> denominada `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="2b04f-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="2b04f-156">Inicialize a instância com o endereço base concatenado com o nome do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2b04f-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="2b04f-157">Crie uma instância da classe de cliente gerada com as variáveis `serviceAddress` e `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="2b04f-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="2b04f-158">Chame o método <xref:System.ServiceModel.ClientBase%601.Open%2A>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b04f-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="2b04f-159">Chame o serviço e exiba os resultados.</span><span class="sxs-lookup"><span data-stu-id="2b04f-159">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="2b04f-160">Usando o arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="2b04f-160">Using the Configuration File</span></span>

<span data-ttu-id="2b04f-161">Em vez de criar a associação com código de procedimento, você pode usar o código a seguir mostrado para a seção de associações do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b04f-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="2b04f-162">Se você ainda não tiver um serviço definido, consulte [projetando e implementando serviços](designing-and-implementing-services.md)e [Configurando serviços](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="2b04f-162">If you do not already have a service defined, see [Designing and Implementing Services](designing-and-implementing-services.md), and [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2b04f-163">Esse código de configuração é usado nos arquivos de configuração do serviço e do cliente.</span><span class="sxs-lookup"><span data-stu-id="2b04f-163">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="2b04f-164">Para habilitar a segurança de transferência em um serviço em um domínio do Windows usando a configuração</span><span class="sxs-lookup"><span data-stu-id="2b04f-164">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="2b04f-165">Adicione um elemento de [> de \<wsHttpBinding](../configure-apps/file-schema/wcf/wshttpbinding.md) à seção de elemento [> do \<bindings](../configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b04f-165">Add a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="2b04f-166">Adicione um elemento < `binding` > ao elemento < `WSHttpBinding` > e defina o atributo `configurationName` como um valor apropriado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2b04f-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="2b04f-167">Adicione um elemento < `security` > e defina o atributo `mode` como mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b04f-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="2b04f-168">Adicione um elemento < `message` > e defina o atributo `clientCredentialType` para o Windows.</span><span class="sxs-lookup"><span data-stu-id="2b04f-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="2b04f-169">No arquivo de configuração do serviço, substitua a seção `<bindings>` pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b04f-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="2b04f-170">Se você ainda não tiver um arquivo de configuração de serviço, consulte [usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="2b04f-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="2b04f-171">Usando a associação em um cliente</span><span class="sxs-lookup"><span data-stu-id="2b04f-171">Using the Binding in a Client</span></span>

<span data-ttu-id="2b04f-172">Este procedimento mostra como gerar dois arquivos: um proxy que se comunica com o serviço e um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b04f-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="2b04f-173">Ele também descreve as alterações no programa cliente, que é o terceiro arquivo usado no cliente.</span><span class="sxs-lookup"><span data-stu-id="2b04f-173">It also describes changes to the client program, which is the third file used on the client.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="2b04f-174">Para usar uma associação em um cliente com configuração</span><span class="sxs-lookup"><span data-stu-id="2b04f-174">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="2b04f-175">Use a ferramenta SvcUtil. exe para gerar o código de proxy e o arquivo de configuração dos metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="2b04f-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="2b04f-176">Para obter mais informações, consulte [como: criar um cliente](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="2b04f-176">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="2b04f-177">Substitua a seção [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração gerado pelo código de configuração da seção anterior.</span><span class="sxs-lookup"><span data-stu-id="2b04f-177">Replace the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="2b04f-178">O código de procedimento é inserido no início do método `Main` do programa cliente.</span><span class="sxs-lookup"><span data-stu-id="2b04f-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="2b04f-179">Crie uma instância da classe de cliente gerada passando o nome da associação no arquivo de configuração como um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="2b04f-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="2b04f-180">Chame o método <xref:System.ServiceModel.ClientBase%601.Open%2A>, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2b04f-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="2b04f-181">Chame o serviço e exiba os resultados.</span><span class="sxs-lookup"><span data-stu-id="2b04f-181">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="2b04f-182">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b04f-182">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="2b04f-183">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b04f-183">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="2b04f-184">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="2b04f-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="2b04f-185">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="2b04f-185">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="2b04f-186">Protegendo serviços</span><span class="sxs-lookup"><span data-stu-id="2b04f-186">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="2b04f-187">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="2b04f-187">Security Overview</span></span>](./feature-details/security-overview.md)
