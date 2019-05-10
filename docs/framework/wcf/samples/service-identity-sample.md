---
title: Exemplo de identidade de serviço
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 587c1b8f5cd509db343266f5903847d3b94b7460
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664688"
---
# <a name="service-identity-sample"></a><span data-ttu-id="92af0-102">Exemplo de identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="92af0-102">Service Identity Sample</span></span>
<span data-ttu-id="92af0-103">Este exemplo de identidade de serviço demonstra como definir a identidade de um serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="92af0-104">Em tempo de design, um cliente pode recuperar a identidade usando metadados do serviço e, em seguida, em tempo de execução, o cliente pode autenticar a identidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="92af0-105">O conceito de identidade de serviço é permitir que um cliente autenticar um serviço antes de chamar qualquer uma de suas operações, protegendo, assim, o cliente de chamadas não autenticadas.</span><span class="sxs-lookup"><span data-stu-id="92af0-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="92af0-106">Em uma conexão segura o serviço também autentica as credenciais de um cliente antes de permitir acesso ele, mas isso não é o foco deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="92af0-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="92af0-107">Consulte os exemplos na [cliente](../../../../docs/framework/wcf/samples/client.md) que mostram a autenticação do servidor.</span><span class="sxs-lookup"><span data-stu-id="92af0-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>

> [!NOTE]
>  <span data-ttu-id="92af0-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="92af0-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="92af0-109">Este exemplo ilustra os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="92af0-109">This sample illustrates the following features:</span></span>

- <span data-ttu-id="92af0-110">Como definir os diferentes tipos de identidade em diferentes pontos de extremidade para um serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="92af0-111">Cada tipo de identidade tem recursos diferentes.</span><span class="sxs-lookup"><span data-stu-id="92af0-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="92af0-112">O tipo de identidade deve ser usada é dependente do tipo de credenciais de segurança usado na associação do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="92af0-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>

- <span data-ttu-id="92af0-113">Identidade pode ser definida declarativamente na configuração ou imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="92af0-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="92af0-114">Normalmente para o cliente e o serviço, você deve usar configuração para definir a identidade.</span><span class="sxs-lookup"><span data-stu-id="92af0-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>

- <span data-ttu-id="92af0-115">Como definir uma identidade personalizada no cliente.</span><span class="sxs-lookup"><span data-stu-id="92af0-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="92af0-116">Normalmente, uma identidade personalizada é uma personalização de um tipo existente de identidade que permite que o cliente examinar outras informações de declaração fornecidas nas credenciais do serviço para tomar decisões de autorização antes de chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="92af0-117">Este exemplo verifica a identidade de um certificado específico chamado identity.com e a chave RSA contido dentro deste certificado.</span><span class="sxs-lookup"><span data-stu-id="92af0-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="92af0-118">Ao usar os tipos de identidade do certificado e RSA em configuração no cliente, uma maneira fácil de obter esses valores é inspecionar o WSDL para o serviço em que esses valores são serializados.</span><span class="sxs-lookup"><span data-stu-id="92af0-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>

 <span data-ttu-id="92af0-119">O código de exemplo a seguir mostra como configurar a identidade de um ponto de extremidade de serviço com o servidor de nome de domínio (DNS) de um certificado usando um WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="92af0-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 <span data-ttu-id="92af0-120">A identidade também pode ser especificada na configuração no arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="92af0-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="92af0-121">O exemplo a seguir mostra como definir a identidade do UPN (Nome Principal do usuário) para um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>

```xml
<endpoint address="upnidentity"
        behaviorConfiguration=""
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_Windows"
        name="WSHttpBinding_ICalculator_Windows"
        contract="Microsoft.ServiceModel.Samples.ICalculator">
  <!-- Set the UPN identity for this endpoint -->
  <identity>
      <userPrincipalName value="host\myservice.com" />
  </identity >
</endpoint>
```

 <span data-ttu-id="92af0-122">Uma identidade personalizada pode ser definida no cliente derivando de <xref:System.ServiceModel.EndpointIdentity> e o <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span><span class="sxs-lookup"><span data-stu-id="92af0-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="92af0-123">Conceitualmente o <xref:System.ServiceModel.Security.IdentityVerifier> classe pode ser considerado como o cliente equivalente do serviço de `AuthorizationManager` classe.</span><span class="sxs-lookup"><span data-stu-id="92af0-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="92af0-124">O exemplo de código a seguir mostra uma implementação de `OrgEndpointIdentity`, que armazena o nome de uma organização a ser correspondido em nome do assunto do certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="92af0-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="92af0-125">A verificação de autorização para o nome da organização ocorre na `CheckAccess` método no `CustomIdentityVerifier` classe.</span><span class="sxs-lookup"><span data-stu-id="92af0-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>

```csharp
// This custom EndpointIdentity stores an organization name
public class OrgEndpointIdentity : EndpointIdentity
{
    private string orgClaim;
    public OrgEndpointIdentity(string orgName)
    {
        orgClaim = orgName;
    }
    public string OrganizationClaim
    {
        get { return orgClaim; }
        set { orgClaim = value; }
    }
}

//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to
//check that X.509 certificate's distinguished name claim contains
//the organization name e.g. the string value "O=Contoso"
class CustomIdentityVerifier : IdentityVerifier
{
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)
    {
        bool returnvalue = false;
        foreach (ClaimSet claimset in authContext.ClaimSets)
        {
            foreach (Claim claim in claimset)
            {
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")
                {
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))
                    {
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);
                        Console.WriteLine("Right: {0}", claim.Right);
                        Console.WriteLine("Resource: {0}",claim.Resource);
                        Console.WriteLine();
                        returnvalue = true;
                    }
                }
            }
        }
        return returnvalue;
    }
}
```

 <span data-ttu-id="92af0-126">Este exemplo usa um certificado chamado identity.com que está na pasta da solução de identidade específicas de idioma.</span><span class="sxs-lookup"><span data-stu-id="92af0-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="92af0-127">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="92af0-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="92af0-128">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92af0-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="92af0-129">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92af0-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="92af0-130">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92af0-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="92af0-131">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="92af0-131">To run the sample on the same computer</span></span>

1. <span data-ttu-id="92af0-132">Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou [!INCLUDE[wv](../../../../includes/wv-md.md)], importar o arquivo de certificado Identity.pfx na pasta da solução de identidade para o repositório de LocalMachine/meu certificado (pessoal) usando a ferramenta de snap-in do MMC.</span><span class="sxs-lookup"><span data-stu-id="92af0-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="92af0-133">Esse arquivo é protegido por senha.</span><span class="sxs-lookup"><span data-stu-id="92af0-133">This file is password protected.</span></span> <span data-ttu-id="92af0-134">Durante a importação, você será solicitado para uma senha.</span><span class="sxs-lookup"><span data-stu-id="92af0-134">During the import you are asked for a password.</span></span> <span data-ttu-id="92af0-135">Tipo `xyz` na caixa de senha.</span><span class="sxs-lookup"><span data-stu-id="92af0-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="92af0-136">Para obter mais informações, confira a página [Como: Exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="92af0-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="92af0-137">Depois que isso for feito, execute Setup. bat em um Prompt de comando do desenvolvedor para Visual Studio com privilégios de administrador, que copia esse certificado no repositório de pessoas confiáveis CurrentUser para uso no cliente.</span><span class="sxs-lookup"><span data-stu-id="92af0-137">Once this is done, run Setup.bat in a Developer Command Prompt for Visual Studio with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>

2. <span data-ttu-id="92af0-138">Em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], execute Setup. bat a partir da pasta de instalação de exemplo dentro de um prompt de comando do Visual Studio 2012 com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="92af0-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt with administrator privileges.</span></span> <span data-ttu-id="92af0-139">Essa opção instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="92af0-139">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="92af0-140">O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2012 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="92af0-140">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="92af0-141">A variável de ambiente PATH definido dentro de pontos de Prompt de comando do Visual Studio 2012 para o diretório que contém executáveis exigido pelo script de Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="92af0-141">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="92af0-142">Certifique-se de que você remova os certificados com a execução CleanUp quando você terminar com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="92af0-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="92af0-143">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="92af0-143">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="92af0-144">Inicie o Service.exe do diretório \service\bin.</span><span class="sxs-lookup"><span data-stu-id="92af0-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="92af0-145">Certifique-se de que o serviço indica que ele está pronto e exibe um prompt para pressionar \<Enter > para encerrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4. <span data-ttu-id="92af0-146">Inicie o Client.exe do diretório \Client\Bin. ou pressionando F5 no Visual Studio para compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="92af0-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="92af0-147">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="92af0-147">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="92af0-148">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="92af0-148">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="92af0-149">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="92af0-149">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="92af0-150">Antes de compilar a parte cliente de exemplo, certifique-se de alterar o valor para o endereço do ponto de extremidade do serviço no arquivo Client.cs no `CallServiceCustomClientIdentity` método.</span><span class="sxs-lookup"><span data-stu-id="92af0-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="92af0-151">Em seguida, crie o exemplo.</span><span class="sxs-lookup"><span data-stu-id="92af0-151">Then build the sample.</span></span>  
  
2. <span data-ttu-id="92af0-152">Crie um diretório no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-152">Create a directory on the service computer.</span></span>  
  
3. <span data-ttu-id="92af0-153">Copie os arquivos de programa do serviço de service\bin para o diretório no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="92af0-154">Também copie os arquivos Setup. bat e Cleanup para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4. <span data-ttu-id="92af0-155">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="92af0-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5. <span data-ttu-id="92af0-156">Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="92af0-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="92af0-157">Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="92af0-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6. <span data-ttu-id="92af0-158">No serviço, executar `setup.bat service` em um Prompt de comando do desenvolvedor para Visual Studio é aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="92af0-158">On the service, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92af0-159">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="92af0-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7. <span data-ttu-id="92af0-160">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="92af0-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="92af0-161">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="92af0-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="92af0-162">Há várias instâncias que devem ser alteradas.</span><span class="sxs-lookup"><span data-stu-id="92af0-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="92af0-163">No cliente, execute ImportServiceCert.bat em um Prompt de comando do desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="92af0-163">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="92af0-164">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="92af0-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="92af0-165">No computador do serviço, inicie o Service.exe do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="92af0-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="92af0-166">No computador cliente, inicie Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="92af0-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="92af0-167">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="92af0-167">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="92af0-168">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="92af0-168">To clean up after the sample</span></span>  
  
- <span data-ttu-id="92af0-169">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="92af0-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92af0-170">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="92af0-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="92af0-171">Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="92af0-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="92af0-172">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="92af0-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
