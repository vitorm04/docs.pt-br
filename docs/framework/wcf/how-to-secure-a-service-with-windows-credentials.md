---
title: Como proteger um serviço com credenciais Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2fa8d753d5fb168c14ee71cbbf6de62e0e4aff9e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="e2aa7-102">Como proteger um serviço com credenciais Windows</span><span class="sxs-lookup"><span data-stu-id="e2aa7-102">How to: Secure a Service with Windows Credentials</span></span>
<span data-ttu-id="e2aa7-103">Este tópico mostra como habilitar a segurança de transporte em um serviço do Windows Communication Foundation (WCF) que reside em um domínio do Windows e é chamado pelos clientes no mesmo domínio.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="e2aa7-104">Para obter mais informações sobre esse cenário, consulte [segurança de transporte com autenticação do Windows](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="e2aa7-105">Para um aplicativo de exemplo, consulte o [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
 <span data-ttu-id="e2aa7-106">Este tópico pressupõe que você tem uma interface de contrato existente e implementação já definida e adiciona o logon que.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="e2aa7-107">Você também pode modificar um cliente e serviço existente.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-107">You can also modify an existing service and client.</span></span>  
  
 <span data-ttu-id="e2aa7-108">Você pode proteger um serviço com credenciais do Windows completamente no código.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="e2aa7-109">Como alternativa, você pode omitir parte do código usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="e2aa7-110">Este tópico mostra duas formas.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-110">This topic shows both ways.</span></span> <span data-ttu-id="e2aa7-111">Certifique-se de que você usar apenas uma das maneiras, não ambos.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-111">Be sure you only use one of the ways, not both.</span></span>  
  
 <span data-ttu-id="e2aa7-112">Os três primeiros procedimentos mostram como proteger o serviço usando o código.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="e2aa7-113">O quarto e quinto procedimento mostra como fazer isso com um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>  
  
## <a name="using-code"></a><span data-ttu-id="e2aa7-114">Usando código</span><span class="sxs-lookup"><span data-stu-id="e2aa7-114">Using Code</span></span>  
 <span data-ttu-id="e2aa7-115">O código completo para o serviço e o cliente está na seção de exemplo no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>  
  
 <span data-ttu-id="e2aa7-116">O primeiro procedimento orienta a criação e configuração de um <xref:System.ServiceModel.WSHttpBinding> classe no código.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="e2aa7-117">A associação usa o transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="e2aa7-118">A mesma associação é usada no cliente.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-118">The same binding is used on the client.</span></span>  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="e2aa7-119">Para criar um WSHttpBinding que usa credenciais do Windows e segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="e2aa7-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>  
  
1.  <span data-ttu-id="e2aa7-120">Esse código de procedimento é inserido no início do `Run` método o `Test` classe no código de serviço na seção de exemplo.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>  
  
2.  <span data-ttu-id="e2aa7-121">Crie uma instância da classe <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
3.  <span data-ttu-id="e2aa7-122">Definir o <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> propriedade o <xref:System.ServiceModel.WSHttpSecurity> de classe para <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
4.  <span data-ttu-id="e2aa7-123">Definir o <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> propriedade o <xref:System.ServiceModel.MessageSecurityOverHttp> de classe para <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>  
  
5.  <span data-ttu-id="e2aa7-124">O código para esse procedimento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e2aa7-124">The code for this procedure is as follows:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="e2aa7-125">Usando a associação em um serviço</span><span class="sxs-lookup"><span data-stu-id="e2aa7-125">Using the Binding in a Service</span></span>  
 <span data-ttu-id="e2aa7-126">Este é o segundo procedimento que mostra como usar a associação em um serviço auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="e2aa7-127">Para obter mais informações sobre hospedagem de serviços, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="e2aa7-128">Para usar uma associação em um serviço</span><span class="sxs-lookup"><span data-stu-id="e2aa7-128">To use a binding in a service</span></span>  
  
1.  <span data-ttu-id="e2aa7-129">Inserir este código de procedimento após o código do procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-129">Insert this procedure's code after the code from the preceding procedure.</span></span>  
  
2.  <span data-ttu-id="e2aa7-130">Criar um <xref:System.Type> variável chamada `contractType` e atribua-o tipo da interface (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="e2aa7-131">Ao usar o Visual Basic, use o `GetType` operador; ao usar o c#, use o `typeof` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>  
  
3.  <span data-ttu-id="e2aa7-132">Crie um segundo `Type` variável chamada `serviceType` e atribua-o tipo do contrato implementado (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-132">Create a second `Type` variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>  
  
4.  <span data-ttu-id="e2aa7-133">Criar uma instância do <xref:System.Uri> classe denominada `baseAddress` com o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="e2aa7-134">O endereço base deve ter um esquema que corresponde o transporte.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="e2aa7-135">Nesse caso, o esquema de transporte é HTTP, e o endereço inclui especiais "Localhost" identificador de recurso uniforme (URI) e uma porta de número (8036), bem como um endereço base do ponto de extremidade ("serviceModelSamples /): http://localhost:8036/serviceModelSamples/.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): http://localhost:8036/serviceModelSamples/.</span></span>  
  
5.  <span data-ttu-id="e2aa7-136">Criar uma instância do <xref:System.ServiceModel.ServiceHost> classe com o `serviceType` e `baseAddress` variáveis.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>  
  
6.  <span data-ttu-id="e2aa7-137">Adicionar um ponto de extremidade para o serviço usando o `contractType`, associação e um nome de ponto de extremidade (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="e2aa7-138">Um cliente deverá concatenar o endereço base e o nome do ponto de extremidade ao iniciar uma chamada para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>  
  
7.  <span data-ttu-id="e2aa7-139">Chamar o <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> método para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="e2aa7-140">O código para esse procedimento é mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="e2aa7-140">The code for this procedure is shown here:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="e2aa7-141">Usando a associação em um cliente</span><span class="sxs-lookup"><span data-stu-id="e2aa7-141">Using the Binding in a Client</span></span>  
 <span data-ttu-id="e2aa7-142">Este procedimento mostra como gerar um proxy que se comunica com o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="e2aa7-143">O proxy será gerado com o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) que usa os metadados de serviço para criar o proxy.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>  
  
 <span data-ttu-id="e2aa7-144">Esse procedimento também cria uma instância do <xref:System.ServiceModel.WSHttpBinding> de classe para se comunicar com o serviço e, em seguida, chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>  
  
 <span data-ttu-id="e2aa7-145">Este exemplo usa apenas o código para criar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-145">This example uses only code to create the client.</span></span> <span data-ttu-id="e2aa7-146">Como alternativa, você pode usar um arquivo de configuração, que é mostrado na seção a seguir esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="e2aa7-147">Para usar uma associação em um cliente com o código</span><span class="sxs-lookup"><span data-stu-id="e2aa7-147">To use a binding in a client with code</span></span>  
  
1.  <span data-ttu-id="e2aa7-148">Use a ferramenta SvcUtil.exe para gerar o código de proxy de metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="e2aa7-149">Para obter mais informações, consulte [como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="e2aa7-150">O código de proxy gerado herda o <xref:System.ServiceModel.ClientBase%601> classe, que garante que cada cliente tem a necessário construtores, métodos e propriedades para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="e2aa7-151">Neste exemplo, o código gerado inclui o `CalculatorClient` de classe que implementa o `ICalculator` interface, habilitando a compatibilidade com o código de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>  
  
2.  <span data-ttu-id="e2aa7-152">Esse código de procedimento é inserido no início de `Main` método do programa cliente.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
3.  <span data-ttu-id="e2aa7-153">Criar uma instância do <xref:System.ServiceModel.WSHttpBinding> de classe e defina o modo de segurança `Message` e seu tipo de credencial de cliente `Windows`.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="e2aa7-154">O exemplo de nomes de variável `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-154">The example names the variable `clientBinding`.</span></span>  
  
4.  <span data-ttu-id="e2aa7-155">Criar uma instância do <xref:System.ServiceModel.EndpointAddress> classe denominada `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="e2aa7-156">Inicialize a instância com o endereço base concatenado com o nome do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>  
  
5.  <span data-ttu-id="e2aa7-157">Criar uma instância da classe cliente gerada com o `serviceAddress` e `clientBinding` variáveis.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>  
  
6.  <span data-ttu-id="e2aa7-158">Chamar o <xref:System.ServiceModel.ClientBase%601.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
7.  <span data-ttu-id="e2aa7-159">Chamar o serviço e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-159">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a><span data-ttu-id="e2aa7-160">Usando o arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="e2aa7-160">Using the Configuration File</span></span>  
 <span data-ttu-id="e2aa7-161">Em vez de criar a associação com o código de procedimento, você pode usar o seguinte código mostrado na seção de associações de arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>  
  
 <span data-ttu-id="e2aa7-162">Se você ainda não tiver um serviço definido, consulte [Projetando e Implementando serviços](../../../docs/framework/wcf/designing-and-implementing-services.md), e [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
 <span data-ttu-id="e2aa7-163">**Observação** este código de configuração é usado em arquivos de configuração do serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-163">**Note** This configuration code is used in both the service and client configuration files.</span></span>  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="e2aa7-164">Para ativar a segurança de transferência em um serviço em um domínio do Windows usando a configuração</span><span class="sxs-lookup"><span data-stu-id="e2aa7-164">To enable transfer security on a service in a Windows domain using configuration</span></span>  
  
1.  <span data-ttu-id="e2aa7-165">Adicionar um [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento para o [ \<associações >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) seção do elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="e2aa7-166">Adicionar um <`binding`> elemento para o <`WSHttpBinding`> elemento e defina o `configurationName` de atributo para um valor apropriado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>  
  
3.  <span data-ttu-id="e2aa7-167">Adicionar um <`security`> elemento e defina o `mode` a mensagem de atributo.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>  
  
4.  <span data-ttu-id="e2aa7-168">Adicionar um <`message`> elemento e defina o `clientCredentialType` atributo Windows.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>  
  
5.  <span data-ttu-id="e2aa7-169">No arquivo de configuração do serviço, substitua o `<bindings>` seção com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="e2aa7-170">Se você não tiver um arquivo de configuração de serviço, consulte [usando associações para configurar os serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
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
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="e2aa7-171">Usando a associação em um cliente</span><span class="sxs-lookup"><span data-stu-id="e2aa7-171">Using the Binding in a Client</span></span>  
 <span data-ttu-id="e2aa7-172">Este procedimento mostra como gerar dois arquivos: um proxy que se comunica com o serviço e um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="e2aa7-173">Ele também descreve alterações para o programa cliente, que é o terceiro arquivo usado no cliente.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-173">It also describes changes to the client program, which is the third file used on the client.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="e2aa7-174">Para usar uma associação em um cliente com a configuração</span><span class="sxs-lookup"><span data-stu-id="e2aa7-174">To use a binding in a client with configuration</span></span>  
  
1.  <span data-ttu-id="e2aa7-175">Use a ferramenta SvcUtil.exe para gerar o arquivo de código e configuração de proxy de metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="e2aa7-176">Para obter mais informações, consulte [como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="e2aa7-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="e2aa7-177">Substitua o [ \<associações >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) seção do arquivo de configuração gerado com o código de configuração da seção anterior.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>  
  
3.  <span data-ttu-id="e2aa7-178">Código procedural é inserido no início de `Main` método do programa cliente.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
4.  <span data-ttu-id="e2aa7-179">Crie uma instância da classe cliente gerada passando o nome da associação no arquivo de configuração como um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>  
  
5.  <span data-ttu-id="e2aa7-180">Chamar o <xref:System.ServiceModel.ClientBase%601.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
6.  <span data-ttu-id="e2aa7-181">Chamar o serviço e exibir os resultados.</span><span class="sxs-lookup"><span data-stu-id="e2aa7-181">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="e2aa7-182">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2aa7-182">Example</span></span>  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a><span data-ttu-id="e2aa7-183">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2aa7-183">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 [<span data-ttu-id="e2aa7-184">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="e2aa7-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="e2aa7-185">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="e2aa7-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="e2aa7-186">Protegendo serviços</span><span class="sxs-lookup"><span data-stu-id="e2aa7-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="e2aa7-187">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="e2aa7-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
