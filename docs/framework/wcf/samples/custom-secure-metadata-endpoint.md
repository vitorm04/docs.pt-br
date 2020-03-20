---
title: Ponto de extremidade de metadados seguros personalizados
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 89f12b4490d556884aaa15dcb102b5ad876707ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183842"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="359ea-102">Ponto de extremidade de metadados seguros personalizados</span><span class="sxs-lookup"><span data-stu-id="359ea-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="359ea-103">Esta amostra demonstra como implementar um serviço com um ponto final de metadados seguro que usa uma das vinculações de troca de metadados e como configurar [o ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou os clientes para buscar os metadados a partir de um ponto final de metadados.</span><span class="sxs-lookup"><span data-stu-id="359ea-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="359ea-104">Existem duas vinculações fornecidas pelo sistema disponíveis para expor pontos finais de metadados: mexHttpBinding e mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="359ea-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="359ea-105">mexHttpBinding é usado para expor um ponto final de metadados sobre HTTP de forma não segura.</span><span class="sxs-lookup"><span data-stu-id="359ea-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="359ea-106">mexHttpsBinding é usado para expor um ponto final de metadados sobre HTTPS de forma segura.</span><span class="sxs-lookup"><span data-stu-id="359ea-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="359ea-107">Esta amostra ilustra como expor um ponto final <xref:System.ServiceModel.WSHttpBinding>de metadados seguro usando o .</span><span class="sxs-lookup"><span data-stu-id="359ea-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="359ea-108">Você gostaria de fazer isso quando quiser alterar as configurações de segurança na vinculação, mas não deseja usar HTTPS.</span><span class="sxs-lookup"><span data-stu-id="359ea-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="359ea-109">Se você usar o mexHttpsBinding seu ponto final de metadados será seguro, mas não há como modificar as configurações de vinculação.</span><span class="sxs-lookup"><span data-stu-id="359ea-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="359ea-110">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="359ea-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="359ea-111">Serviço</span><span class="sxs-lookup"><span data-stu-id="359ea-111">Service</span></span>  
 <span data-ttu-id="359ea-112">O serviço nesta amostra tem dois pontos finais.</span><span class="sxs-lookup"><span data-stu-id="359ea-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="359ea-113">O ponto final `ICalculator` do aplicativo `WSHttpBinding` `ReliableSession` atende ao `Message` contrato em um com habilitação e segurança usando certificados.</span><span class="sxs-lookup"><span data-stu-id="359ea-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="359ea-114">O ponto final de `WSHttpBinding`metadados também usa , `ReliableSession`com as mesmas configurações de segurança, mas sem .</span><span class="sxs-lookup"><span data-stu-id="359ea-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="359ea-115">Aqui está a configuração relevante:</span><span class="sxs-lookup"><span data-stu-id="359ea-115">Here is the relevant configuration:</span></span>  
  
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
  
 <span data-ttu-id="359ea-116">Em muitas das outras amostras, o ponto `mexHttpBinding`final de metadados usa o padrão , que não é seguro.</span><span class="sxs-lookup"><span data-stu-id="359ea-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="359ea-117">Aqui os metadados `WSHttpBinding` são `Message` protegidos usando com segurança.</span><span class="sxs-lookup"><span data-stu-id="359ea-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="359ea-118">Para que os clientes de metadados recuperem esses metadados, eles devem ser configurados com uma vinculação correspondente.</span><span class="sxs-lookup"><span data-stu-id="359ea-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="359ea-119">Esta amostra demonstra dois desses clientes.</span><span class="sxs-lookup"><span data-stu-id="359ea-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="359ea-120">O primeiro cliente usa o Svcutil.exe para buscar os metadados e gerar código e configuração do cliente na hora do projeto.</span><span class="sxs-lookup"><span data-stu-id="359ea-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="359ea-121">Como o serviço usa uma vinculação não padrão para os metadados, a ferramenta Svcutil.exe deve ser configurada especificamente para que possa obter os metadados do serviço usando essa vinculação.</span><span class="sxs-lookup"><span data-stu-id="359ea-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="359ea-122">O segundo cliente `MetadataResolver` usa o para buscar dinamicamente os metadados para um contrato conhecido e, em seguida, invocar operações no cliente gerado dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="359ea-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="359ea-123">Cliente Svcutil</span><span class="sxs-lookup"><span data-stu-id="359ea-123">Svcutil client</span></span>  
 <span data-ttu-id="359ea-124">Ao usar a vinculação `IMetadataExchange` padrão para hospedar seu ponto final, você pode executar Svcutil.exe com o endereço desse ponto final:</span><span class="sxs-lookup"><span data-stu-id="359ea-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="359ea-125">e funciona.</span><span class="sxs-lookup"><span data-stu-id="359ea-125">and it works.</span></span> <span data-ttu-id="359ea-126">Mas nesta amostra, o servidor usa um ponto final não padrão para hospedar os metadados.</span><span class="sxs-lookup"><span data-stu-id="359ea-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="359ea-127">Então Svcutil.exe deve ser instruído a usar a ligação correta.</span><span class="sxs-lookup"><span data-stu-id="359ea-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="359ea-128">Isso pode ser feito usando um arquivo Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="359ea-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="359ea-129">O arquivo Svcutil.exe.config parece um arquivo de configuração normal do cliente.</span><span class="sxs-lookup"><span data-stu-id="359ea-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="359ea-130">Os únicos aspectos incomuns são o nome e o contrato do ponto final do cliente:</span><span class="sxs-lookup"><span data-stu-id="359ea-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="359ea-131">O nome do ponto final deve ser o nome do esquema do endereço onde `IMetadataExchange`os metadados estão hospedados e o contrato de ponto final deve ser .</span><span class="sxs-lookup"><span data-stu-id="359ea-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="359ea-132">Assim, quando Svcutil.exe é executado com uma linha de comando como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="359ea-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="359ea-133">ele procura o ponto final chamado `IMetadataExchange` "http" e contrato para configurar a vinculação e o comportamento da troca de comunicação com o ponto final de metadados.</span><span class="sxs-lookup"><span data-stu-id="359ea-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="359ea-134">O resto do arquivo Svcutil.exe.config na amostra especifica as credenciais de configuração e comportamento de vinculação para corresponder à configuração do ponto final do ponto final do ponto final do servidor.</span><span class="sxs-lookup"><span data-stu-id="359ea-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="359ea-135">Para que o Svcutil.exe pegue a configuração em Svcutil.exe.config, o Svcutil.exe deve estar no mesmo diretório que o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="359ea-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="359ea-136">Como resultado, você deve copiar Svcutil.exe de seu local de instalação para o diretório que contém o arquivo Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="359ea-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="359ea-137">Em seguida, a partir desse diretório, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="359ea-137">Then from that directory, run the following command:</span></span>  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="359ea-138">O protagonista". \\" garante que a cópia de Svcutil.exe neste diretório (aquela que tem um Svcutil.exe.config correspondente) seja executada.</span><span class="sxs-lookup"><span data-stu-id="359ea-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="359ea-139">Cliente MetadataResolver</span><span class="sxs-lookup"><span data-stu-id="359ea-139">MetadataResolver client</span></span>  
 <span data-ttu-id="359ea-140">Se o cliente souber o contrato e como falar com os metadados na hora do projeto, o `MetadataResolver`cliente poderá descobrir dinamicamente a vinculação e o endereço dos pontos finais do aplicativo usando o .</span><span class="sxs-lookup"><span data-stu-id="359ea-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="359ea-141">Este cliente de amostra demonstra isso, mostrando como `MetadataResolver` configurar a vinculação e as credenciais usadas pela criação e configuração de um `MetadataExchangeClient`.</span><span class="sxs-lookup"><span data-stu-id="359ea-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="359ea-142">As mesmas informações de vinculação e certificado sumidas em Svcutil.exe.config podem ser especificadas imperativamente no: `MetadataExchangeClient`</span><span class="sxs-lookup"><span data-stu-id="359ea-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="359ea-143">Com `mexClient` o configurado, podemos enumerar os contratos que `MetadataResolver` nos interessam, e usar para buscar uma lista de pontos finais com esses contratos:</span><span class="sxs-lookup"><span data-stu-id="359ea-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="359ea-144">Finalmente, podemos usar as informações desses pontos finais para `ChannelFactory` inicializar a vinculação e o endereço de um usado para criar canais para se comunicar com os pontos finais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="359ea-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="359ea-145">O ponto chave deste cliente de amostra é `MetadataResolver`demonstrar que, se você estiver usando , e você deve especificar vinculações ou comportamentos personalizados para a comunicação de troca de metadados, você pode usar um `MetadataExchangeClient` para especificar essas configurações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="359ea-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="359ea-146">Para configurar e construir a amostra</span><span class="sxs-lookup"><span data-stu-id="359ea-146">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="359ea-147">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="359ea-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="359ea-148">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="359ea-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="359ea-149">Para executar a amostra na mesma máquina</span><span class="sxs-lookup"><span data-stu-id="359ea-149">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="359ea-150">Executar Setup.bat da pasta de instalação de amostra.</span><span class="sxs-lookup"><span data-stu-id="359ea-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="359ea-151">Isso instala todos os certificados necessários para a execução da amostra.</span><span class="sxs-lookup"><span data-stu-id="359ea-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="359ea-152">Observe que o Setup.bat usa a ferramenta FindPrivateKey.exe, que é instalada executando a configuraçãoCertTool.bat do [Procedimento de Configuração Única para amostras da Fundação de Comunicação do Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="359ea-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="359ea-153">Execute o aplicativo cliente de \MetadataResolverClient\bin ou \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="359ea-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="359ea-154">A atividade do cliente é exibida no aplicativo do console cliente.</span><span class="sxs-lookup"><span data-stu-id="359ea-154">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="359ea-155">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="359ea-155">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="359ea-156">Remova os certificados executando Cleanup.bat quando terminar com a amostra.</span><span class="sxs-lookup"><span data-stu-id="359ea-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="359ea-157">Outras amostras de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="359ea-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="359ea-158">Para executar a amostra através de máquinas</span><span class="sxs-lookup"><span data-stu-id="359ea-158">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="359ea-159">No servidor, `setup.bat service`execute.</span><span class="sxs-lookup"><span data-stu-id="359ea-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="359ea-160">A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado da máquina e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="359ea-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="359ea-161">No servidor, edite Web.config para refletir o novo nome do certificado.</span><span class="sxs-lookup"><span data-stu-id="359ea-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="359ea-162">Ou seja, `findValue` alterar o atributo no [ \<elemento serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) para o nome de domínio totalmente qualificado da máquina.</span><span class="sxs-lookup"><span data-stu-id="359ea-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="359ea-163">Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente na máquina cliente.</span><span class="sxs-lookup"><span data-stu-id="359ea-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="359ea-164">No cliente, `setup.bat client`corra.</span><span class="sxs-lookup"><span data-stu-id="359ea-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="359ea-165">A `setup.bat` execução com o `client` argumento cria um certificado de cliente chamado Client.com e exporta o certificado do cliente para um arquivo chamado Client.cer.</span><span class="sxs-lookup"><span data-stu-id="359ea-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="359ea-166">No arquivo App.config `MetadataResolverClient` da máquina cliente, altere o valor do endereço do ponto final do mex para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="359ea-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="359ea-167">Você faz isso substituindo o localhost pelo nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="359ea-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="359ea-168">Altere também a ocorrência de "localhost" no arquivo metadataResolverClient.cs para o novo nome do certificado de serviço (o nome de domínio totalmente qualificado do servidor).</span><span class="sxs-lookup"><span data-stu-id="359ea-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="359ea-169">Faça a mesma coisa para o App.config do projeto SvcutilClient.</span><span class="sxs-lookup"><span data-stu-id="359ea-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="359ea-170">Copie o arquivo Client.cer do diretório do cliente para o diretório de serviço situado no servidor.</span><span class="sxs-lookup"><span data-stu-id="359ea-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="359ea-171">No cliente, `ImportServiceCert.bat`corra.</span><span class="sxs-lookup"><span data-stu-id="359ea-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="359ea-172">Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="359ea-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="359ea-173">No servidor, `ImportClientCert.bat`execute , Isso importa o certificado do cliente do arquivo Client.cer para a loja LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="359ea-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="359ea-174">Na máquina de serviço, construa o projeto de serviço no Visual Studio e selecione a página de ajuda em um navegador da Web para verificar se ele está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="359ea-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="359ea-175">Na máquina cliente, execute o MetadataResolverClient ou o SvcutilClient do VS.</span><span class="sxs-lookup"><span data-stu-id="359ea-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="359ea-176">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="359ea-176">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="359ea-177">Para limpar depois da amostra</span><span class="sxs-lookup"><span data-stu-id="359ea-177">To clean up after the sample</span></span>  
  
- <span data-ttu-id="359ea-178">Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="359ea-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="359ea-179">Este script não remove certificados de serviço em um cliente ao executar esta amostra em máquinas.</span><span class="sxs-lookup"><span data-stu-id="359ea-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="359ea-180">Se você tiver executado amostras de Windows Communication Foundation (WCF) que usam certificados em máquinas, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="359ea-180">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="359ea-181">Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`seguinte comando: .</span><span class="sxs-lookup"><span data-stu-id="359ea-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="359ea-182">Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="359ea-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="359ea-183">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="359ea-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="359ea-184">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="359ea-184">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="359ea-185">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="359ea-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="359ea-186">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="359ea-186">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
