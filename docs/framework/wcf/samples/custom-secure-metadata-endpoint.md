---
title: Ponto de extremidade de metadados seguros personalizados
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: d69bc43616ee54a06d5c8f61fbb0afd4618a0202
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676741"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="edec5-102">Ponto de extremidade de metadados seguros personalizados</span><span class="sxs-lookup"><span data-stu-id="edec5-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="edec5-103">Este exemplo demonstra como implementar um serviço com um ponto de extremidade de metadados seguros que usa uma das associações não-metadata exchange e como configurar [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou clientes para buscar o metadados de tal um ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="edec5-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="edec5-104">Há duas associações fornecidas pelo sistema disponíveis para expor pontos de extremidade de metadados: mexHttpBinding e mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="edec5-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="edec5-105">mexHttpBinding é usado para expor um ponto de extremidade de metadados sobre HTTP de forma não segura.</span><span class="sxs-lookup"><span data-stu-id="edec5-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="edec5-106">mexHttpsBinding é usado para expor um ponto de extremidade de metadados via HTTPS de uma maneira segura.</span><span class="sxs-lookup"><span data-stu-id="edec5-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="edec5-107">Este exemplo ilustra como expor um ponto de extremidade de metadados seguros usando o <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="edec5-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="edec5-108">Você pode querer fazer isso quando você deseja alterar as configurações de segurança na associação, mas você não deseja usar HTTPS.</span><span class="sxs-lookup"><span data-stu-id="edec5-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="edec5-109">Se você usar o mexHttpsBinding seu ponto de extremidade de metadados será seguro, mas não é possível modificar as configurações de associação.</span><span class="sxs-lookup"><span data-stu-id="edec5-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edec5-110">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="edec5-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="edec5-111">Serviço</span><span class="sxs-lookup"><span data-stu-id="edec5-111">Service</span></span>  
 <span data-ttu-id="edec5-112">O serviço neste exemplo tem dois pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="edec5-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="edec5-113">O ponto de extremidade do aplicativo serve os `ICalculator` contrato em um `WSHttpBinding` com `ReliableSession` habilitado e `Message` usando certificados de segurança.</span><span class="sxs-lookup"><span data-stu-id="edec5-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="edec5-114">Também usa o ponto de extremidade de metadados `WSHttpBinding`, com as mesmas configurações de segurança, mas sem nenhum `ReliableSession`.</span><span class="sxs-lookup"><span data-stu-id="edec5-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="edec5-115">Aqui está a configuração relevante:</span><span class="sxs-lookup"><span data-stu-id="edec5-115">Here is the relevant configuration:</span></span>  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="edec5-116">Em muitos outros exemplos, o ponto de extremidade de metadados usa o padrão `mexHttpBinding`, que não é seguro.</span><span class="sxs-lookup"><span data-stu-id="edec5-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="edec5-117">Aqui os metadados é protegido usando `WSHttpBinding` com `Message` segurança.</span><span class="sxs-lookup"><span data-stu-id="edec5-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="edec5-118">Em ordem para clientes de metadados recuperar esses metadados, eles devem ser configurados com uma associação correspondente.</span><span class="sxs-lookup"><span data-stu-id="edec5-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="edec5-119">Este exemplo demonstra duas tais clientes.</span><span class="sxs-lookup"><span data-stu-id="edec5-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="edec5-120">O primeiro cliente usa Svcutil.exe para buscar os metadados e gerar código de cliente e a configuração em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="edec5-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="edec5-121">Como o serviço usa uma associação não-padrão para os metadados, a ferramenta Svcutil.exe deve ser configurada especificamente para que ele possa obter os metadados do serviço usando o que a associação.</span><span class="sxs-lookup"><span data-stu-id="edec5-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="edec5-122">O segundo cliente usa o `MetadataResolver` para buscar dinamicamente os metadados para um contrato a conhecidas e, em seguida, chamar operações no cliente gerado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="edec5-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="edec5-123">Cliente de svcutil</span><span class="sxs-lookup"><span data-stu-id="edec5-123">Svcutil client</span></span>  
 <span data-ttu-id="edec5-124">Ao usar a associação padrão para hospedar seu `IMetadataExchange` ponto de extremidade, você pode executar Svcutil.exe com o endereço do ponto de extremidade:</span><span class="sxs-lookup"><span data-stu-id="edec5-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="edec5-125">e ele funciona.</span><span class="sxs-lookup"><span data-stu-id="edec5-125">and it works.</span></span> <span data-ttu-id="edec5-126">Mas, neste exemplo, o servidor usa um ponto de extremidade não padrão para hospedar os metadados.</span><span class="sxs-lookup"><span data-stu-id="edec5-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="edec5-127">Portanto, Svcutil.exe deve ser instruído a usar a associação correta.</span><span class="sxs-lookup"><span data-stu-id="edec5-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="edec5-128">Isso pode ser feito usando um arquivo de svcutil.</span><span class="sxs-lookup"><span data-stu-id="edec5-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="edec5-129">O arquivo de svcutil se parece com um arquivo de configuração do cliente normal.</span><span class="sxs-lookup"><span data-stu-id="edec5-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="edec5-130">Os aspectos apenas incomuns são o nome do ponto de extremidade de cliente e o contrato:</span><span class="sxs-lookup"><span data-stu-id="edec5-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="edec5-131">O nome do ponto de extremidade deve ser o nome do esquema do endereço no qual os metadados é hospedado e o contrato de ponto de extremidade deve ser `IMetadataExchange`.</span><span class="sxs-lookup"><span data-stu-id="edec5-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="edec5-132">Portanto, quando Svcutil.exe é executado com uma linha de comando, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="edec5-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="edec5-133">ele procura por um ponto de extremidade chamado "http" e o contrato `IMetadataExchange` para configurar a associação e o comportamento da troca de comunicação com o ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="edec5-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="edec5-134">O restante do arquivo svcutil no exemplo especifica a configuração de associação e a credenciais de comportamento para corresponder à configuração do servidor do ponto de extremidade de metadados.</span><span class="sxs-lookup"><span data-stu-id="edec5-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="edec5-135">Para Svcutil.exe escolher a configuração de svcutil, Svcutil.exe deve ser no mesmo diretório que o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="edec5-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="edec5-136">Como resultado, você deve copiar Svcutil.exe de seu local de instalação para o diretório que contém o arquivo de svcutil.</span><span class="sxs-lookup"><span data-stu-id="edec5-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="edec5-137">Em seguida, do diretório, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="edec5-137">Then from that directory, run the following command:</span></span>  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="edec5-138">O entrelinhamento ". \\"garante que a cópia do Svcutil.exe neste diretório (aquele que tem um svcutil correspondente) é executada.</span><span class="sxs-lookup"><span data-stu-id="edec5-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="edec5-139">Cliente MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="edec5-139">MetadataResolver client</span></span>  
 <span data-ttu-id="edec5-140">Se o cliente sabe o contrato e como se comunicar com os metadados em tempo de design, o cliente dinamicamente descobrir a associação e o endereço dos pontos de extremidade do aplicativo usando o `MetadataResolver`.</span><span class="sxs-lookup"><span data-stu-id="edec5-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="edec5-141">Esse cliente de exemplo demonstra isso, mostrando como configurar a associação e as credenciais usadas pelo `MetadataResolver` criando e configurando um `MetadataExchangeClient`.</span><span class="sxs-lookup"><span data-stu-id="edec5-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="edec5-142">As mesmas informações de associação e o certificado apareceram no svcutil podem ser especificadas no modo imperativo o `MetadataExchangeClient`:</span><span class="sxs-lookup"><span data-stu-id="edec5-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="edec5-143">Com o `mexClient` configurado, podemos pode enumerar os contratos que estamos interessados em e usar `MetadataResolver` para buscar uma lista de pontos de extremidade com esses contratos:</span><span class="sxs-lookup"><span data-stu-id="edec5-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="edec5-144">Por fim, podemos usar as informações a partir desses pontos de extremidade para inicializar a associação e o endereço de um `ChannelFactory` usado para criar canais para se comunicar com os pontos de extremidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="edec5-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="edec5-145">O ponto principal do cliente neste exemplo é demonstrar que, se você estiver usando `MetadataResolver`e você deve especificar ligações personalizadas ou comportamentos para a comunicação de troca de metadados, você pode usar um `MetadataExchangeClient` para especificar essas configurações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="edec5-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="edec5-146">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="edec5-146">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="edec5-147">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edec5-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="edec5-148">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edec5-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="edec5-149">Para executar o exemplo na mesma máquina</span><span class="sxs-lookup"><span data-stu-id="edec5-149">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="edec5-150">Execute Setup. bat da pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="edec5-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="edec5-151">Essa opção instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="edec5-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="edec5-152">Observe que o Setup. bat usa a ferramenta de FindPrivateKey.exe, que está instalada executando setupCertTool.bat partir [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edec5-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="edec5-153">Execute o aplicativo cliente de \MetadataResolverClient\bin ou \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="edec5-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="edec5-154">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="edec5-154">Client activity is displayed on the client console application.</span></span>  
  
3.  <span data-ttu-id="edec5-155">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="edec5-155">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
4.  <span data-ttu-id="edec5-156">Remova os certificados com a execução CleanUp quando você terminar com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="edec5-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="edec5-157">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="edec5-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="edec5-158">Para executar o exemplo entre máquinas</span><span class="sxs-lookup"><span data-stu-id="edec5-158">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="edec5-159">No servidor, execute `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="edec5-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="edec5-160">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="edec5-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2.  <span data-ttu-id="edec5-161">No servidor, edite o Web. config para refletir o novo nome do certificado.</span><span class="sxs-lookup"><span data-stu-id="edec5-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="edec5-162">Ou seja, alterar o `findValue` de atributo em de [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elemento para o nome de domínio totalmente qualificado da máquina.</span><span class="sxs-lookup"><span data-stu-id="edec5-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3.  <span data-ttu-id="edec5-163">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="edec5-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4.  <span data-ttu-id="edec5-164">No cliente, execute `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="edec5-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="edec5-165">Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado Client.com e exporta o certificado de cliente para um arquivo chamado da CER.</span><span class="sxs-lookup"><span data-stu-id="edec5-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5.  <span data-ttu-id="edec5-166">No arquivo App. config do `MetadataResolverClient` no computador cliente, altere o valor do endereço do ponto de extremidade mex para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="edec5-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="edec5-167">Você pode fazer isso substituindo o localhost com o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="edec5-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="edec5-168">Altere também a ocorrência de "localhost" no arquivo metadataResolverClient.cs para o novo nome de certificado de serviço (o nome de domínio totalmente qualificado do servidor).</span><span class="sxs-lookup"><span data-stu-id="edec5-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="edec5-169">Fazer a mesma coisa para o App. config do projeto SvcutilClient.</span><span class="sxs-lookup"><span data-stu-id="edec5-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6.  <span data-ttu-id="edec5-170">Copie o arquivo de Client. cer do diretório do cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="edec5-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7.  <span data-ttu-id="edec5-171">No cliente, execute `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="edec5-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="edec5-172">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="edec5-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8.  <span data-ttu-id="edec5-173">No servidor, execute `ImportClientCert.bat`, isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="edec5-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="edec5-174">No computador do serviço, compile o projeto de serviço no Visual Studio e selecione a página de Ajuda em um navegador da web para verificar se ele está em execução.</span><span class="sxs-lookup"><span data-stu-id="edec5-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="edec5-175">O computador cliente, execute o MetadataResolverClient ou o SvcutilClient do VS.</span><span class="sxs-lookup"><span data-stu-id="edec5-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1.  <span data-ttu-id="edec5-176">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="edec5-176">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="edec5-177">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="edec5-177">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="edec5-178">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="edec5-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="edec5-179">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas.</span><span class="sxs-lookup"><span data-stu-id="edec5-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="edec5-180">Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="edec5-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="edec5-181">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="edec5-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="edec5-182">Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="edec5-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="edec5-183">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="edec5-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="edec5-184">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="edec5-184">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="edec5-185">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="edec5-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="edec5-186">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="edec5-186">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a><span data-ttu-id="edec5-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edec5-187">See also</span></span>
