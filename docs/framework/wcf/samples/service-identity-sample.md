---
title: Exemplo de identidade de serviço
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 0d5fce313200cdfdb8007ceffe9ff97b033d9f82
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045515"
---
# <a name="service-identity-sample"></a><span data-ttu-id="20ddf-102">Exemplo de identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="20ddf-102">Service Identity Sample</span></span>
<span data-ttu-id="20ddf-103">Este exemplo de identidade de serviço demonstra como definir a identidade de um serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="20ddf-104">Em tempo de design, um cliente pode recuperar a identidade usando os metadados do serviço e, em seguida, em tempo de execução, o cliente pode autenticar a identidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="20ddf-105">O conceito de identidade de serviço é permitir que um cliente autentique um serviço antes de chamar qualquer uma de suas operações, protegendo assim o cliente contra chamadas não autenticadas.</span><span class="sxs-lookup"><span data-stu-id="20ddf-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="20ddf-106">Em uma conexão segura, o serviço também autentica as credenciais de um cliente antes de permitir o acesso, mas esse não é o foco deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="20ddf-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="20ddf-107">Consulte os exemplos no [cliente](../../../../docs/framework/wcf/samples/client.md) que mostram a autenticação do servidor.</span><span class="sxs-lookup"><span data-stu-id="20ddf-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="20ddf-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="20ddf-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="20ddf-109">Este exemplo ilustra os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="20ddf-109">This sample illustrates the following features:</span></span>

- <span data-ttu-id="20ddf-110">Como definir os diferentes tipos de identidade em pontos de extremidade diferentes para um serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="20ddf-111">Cada tipo de identidade tem recursos diferentes.</span><span class="sxs-lookup"><span data-stu-id="20ddf-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="20ddf-112">O tipo de identidade a ser usado depende do tipo de credenciais de segurança usadas na associação do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="20ddf-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>

- <span data-ttu-id="20ddf-113">A identidade pode ser definida declarativamente na configuração ou imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="20ddf-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="20ddf-114">Normalmente, tanto para o cliente quanto para o serviço, você deve usar a configuração para definir a identidade.</span><span class="sxs-lookup"><span data-stu-id="20ddf-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>

- <span data-ttu-id="20ddf-115">Como definir uma identidade personalizada no cliente.</span><span class="sxs-lookup"><span data-stu-id="20ddf-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="20ddf-116">Uma identidade personalizada normalmente é uma personalização de um tipo de identidade existente que permite ao cliente examinar outras informações de declaração fornecidas nas credenciais do serviço para tomar decisões de autorização antes de chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="20ddf-117">Este exemplo verifica a identidade de um certificado específico chamado identity.com e a chave RSA contida nesse certificado.</span><span class="sxs-lookup"><span data-stu-id="20ddf-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="20ddf-118">Ao usar o certificado e os tipos de identidade RSA na configuração no cliente, uma maneira fácil de obter esses valores é inspecionar o WSDL para o serviço em que esses valores são serializados.</span><span class="sxs-lookup"><span data-stu-id="20ddf-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>

 <span data-ttu-id="20ddf-119">O código de exemplo a seguir mostra como configurar a identidade de um ponto de extremidade de serviço com o DNS (servidor de nomes de domínio) de um certificado usando uma WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="20ddf-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 <span data-ttu-id="20ddf-120">A identidade também pode ser especificada na configuração no arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="20ddf-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="20ddf-121">O exemplo a seguir mostra como definir a identidade UPN (nome principal do usuário) para um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>

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

 <span data-ttu-id="20ddf-122">Uma identidade personalizada pode ser definida no cliente derivando das <xref:System.ServiceModel.EndpointIdentity> <xref:System.ServiceModel.Security.IdentityVerifier> classes e.</span><span class="sxs-lookup"><span data-stu-id="20ddf-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="20ddf-123">Conceitualmente, <xref:System.ServiceModel.Security.IdentityVerifier> a classe pode ser considerada como o equivalente do cliente da classe do `AuthorizationManager` serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="20ddf-124">O exemplo de código a seguir mostra uma `OrgEndpointIdentity`implementação de, que armazena um nome de organização para corresponder ao nome da entidade do certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="20ddf-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="20ddf-125">A verificação de autorização para o nome da organização ocorre `CheckAccess` no método `CustomIdentityVerifier` na classe.</span><span class="sxs-lookup"><span data-stu-id="20ddf-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>

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

 <span data-ttu-id="20ddf-126">Este exemplo usa um certificado chamado identity.com que está na pasta de solução de identidade específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="20ddf-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20ddf-127">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="20ddf-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="20ddf-128">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20ddf-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="20ddf-129">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20ddf-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="20ddf-130">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20ddf-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="20ddf-131">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="20ddf-131">To run the sample on the same computer</span></span>

1. <span data-ttu-id="20ddf-132">No [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou[!INCLUDE[wv](../../../../includes/wv-md.md)], importe o arquivo de certificado Identity. pfx na pasta de solução de identidade para o repositório de certificados LocalMachine/My (Personal) usando a ferramenta snap-in do MMC.</span><span class="sxs-lookup"><span data-stu-id="20ddf-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="20ddf-133">Esse arquivo é protegido por senha.</span><span class="sxs-lookup"><span data-stu-id="20ddf-133">This file is password protected.</span></span> <span data-ttu-id="20ddf-134">Durante a importação, você será solicitado a fornecer uma senha.</span><span class="sxs-lookup"><span data-stu-id="20ddf-134">During the import you are asked for a password.</span></span> <span data-ttu-id="20ddf-135">Digite `xyz` na caixa senha.</span><span class="sxs-lookup"><span data-stu-id="20ddf-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="20ddf-136">Para obter mais informações, confira a página [Como: Exiba os certificados com o tópico snap-](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) in do MMC.</span><span class="sxs-lookup"><span data-stu-id="20ddf-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="20ddf-137">Quando isso for feito, execute Setup. bat em um Prompt de Comando do Desenvolvedor para o Visual Studio com privilégios de administrador, que copia esse certificado para o repositório de pessoas CurrentUser/confiáveis para uso no cliente.</span><span class="sxs-lookup"><span data-stu-id="20ddf-137">Once this is done, run Setup.bat in a Developer Command Prompt for Visual Studio with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>

2. <span data-ttu-id="20ddf-138">Em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], execute Setup. bat na pasta de instalação de exemplo dentro de um prompt de comando do Visual Studio 2012 com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="20ddf-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt with administrator privileges.</span></span> <span data-ttu-id="20ddf-139">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="20ddf-139">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="20ddf-140">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="20ddf-140">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="20ddf-141">A variável de ambiente PATH definida no prompt de comando do Visual Studio 2012 aponta para o diretório que contém os executáveis exigidos pelo script setup. bat.</span><span class="sxs-lookup"><span data-stu-id="20ddf-141">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="20ddf-142">Certifique-se de remover os certificados executando Cleanup. bat quando tiver concluído o exemplo.</span><span class="sxs-lookup"><span data-stu-id="20ddf-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="20ddf-143">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="20ddf-143">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="20ddf-144">Inicie o Service. exe no diretório \service\bin</span><span class="sxs-lookup"><span data-stu-id="20ddf-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="20ddf-145">Verifique se o serviço indica que ele está pronto e exibe um prompt para pressionar \<Enter > para encerrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4. <span data-ttu-id="20ddf-146">Inicie o Client. exe no diretório \client\bin ou pressione F5 no Visual Studio para compilar e executar.</span><span class="sxs-lookup"><span data-stu-id="20ddf-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="20ddf-147">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="20ddf-147">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="20ddf-148">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="20ddf-148">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="20ddf-149">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="20ddf-149">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="20ddf-150">Antes de criar a parte cliente do exemplo, certifique-se de alterar o valor do endereço do ponto de extremidade do serviço no arquivo client.cs `CallServiceCustomClientIdentity` no método.</span><span class="sxs-lookup"><span data-stu-id="20ddf-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="20ddf-151">Em seguida, compile o exemplo.</span><span class="sxs-lookup"><span data-stu-id="20ddf-151">Then build the sample.</span></span>  
  
2. <span data-ttu-id="20ddf-152">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-152">Create a directory on the service computer.</span></span>  
  
3. <span data-ttu-id="20ddf-153">Copie os arquivos de programa do serviço de Service \Bin para o diretório no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="20ddf-154">Copie também os arquivos Setup. bat e Cleanup. bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4. <span data-ttu-id="20ddf-155">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="20ddf-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5. <span data-ttu-id="20ddf-156">Copie os arquivos de programa do cliente para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="20ddf-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="20ddf-157">Copie também os arquivos Setup. bat, Cleanup. bat e ImportServiceCert. bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="20ddf-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6. <span data-ttu-id="20ddf-158">No serviço, execute `setup.bat service` em um prompt de comando do desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="20ddf-158">On the service, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="20ddf-159">A `setup.bat` execução com `service` o argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service. cer.</span><span class="sxs-lookup"><span data-stu-id="20ddf-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7. <span data-ttu-id="20ddf-160">Copie o arquivo Service. cer do diretório de serviço para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="20ddf-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="20ddf-161">No arquivo client. exe. config no computador cliente, altere o valor de endereço do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="20ddf-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="20ddf-162">Há várias instâncias que devem ser alteradas.</span><span class="sxs-lookup"><span data-stu-id="20ddf-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="20ddf-163">No cliente, execute ImportServiceCert. bat em um Prompt de Comando do Desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="20ddf-163">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="20ddf-164">Isso importa o certificado de serviço do arquivo Service. cer para o repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="20ddf-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="20ddf-165">No computador do serviço, inicie o Service. exe no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="20ddf-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="20ddf-166">No computador cliente, inicie o Client. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="20ddf-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="20ddf-167">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="20ddf-167">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="20ddf-168">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="20ddf-168">To clean up after the sample</span></span>  
  
- <span data-ttu-id="20ddf-169">Execute o Cleanup. bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="20ddf-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="20ddf-170">Esse script não remove certificados de serviço em um cliente ao executar esse exemplo em computadores.</span><span class="sxs-lookup"><span data-stu-id="20ddf-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="20ddf-171">Se você tiver executado Windows Communication Foundation (WCF) exemplos que usam certificados entre computadores, certifique-se de limpar os certificados de serviço que foram instalados no repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="20ddf-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="20ddf-172">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="20ddf-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
