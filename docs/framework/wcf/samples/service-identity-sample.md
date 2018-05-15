---
title: Exemplo de identidade de serviço
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: d7eee6070956fb3b9a87a79d79040f94740ad2d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="service-identity-sample"></a><span data-ttu-id="ea798-102">Exemplo de identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="ea798-102">Service Identity Sample</span></span>
<span data-ttu-id="ea798-103">Este exemplo de identidade de serviço demonstra como definir a identidade de um serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="ea798-104">Em tempo de design, um cliente pode recuperar a identidade usando metadados do serviço e, em seguida, em tempo de execução, o cliente pode autenticar a identidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="ea798-105">O conceito de identidade de serviço é permitir que um cliente autenticar um serviço antes de chamar qualquer uma das suas operações, protegendo o cliente de chamadas não autenticadas.</span><span class="sxs-lookup"><span data-stu-id="ea798-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="ea798-106">Em uma conexão segura o serviço também autentica credenciais do cliente antes de permitir acesso ele, mas isso não é o foco deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea798-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="ea798-107">Consulte os exemplos em [cliente](../../../../docs/framework/wcf/samples/client.md) que mostram a autenticação do servidor.</span><span class="sxs-lookup"><span data-stu-id="ea798-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea798-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ea798-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ea798-109">Este exemplo ilustra os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="ea798-109">This sample illustrates the following features:</span></span>  
  
-   <span data-ttu-id="ea798-110">Como definir os diferentes tipos de identidade em diferentes pontos de extremidade para um serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="ea798-111">Cada tipo de identidade tem recursos diferentes.</span><span class="sxs-lookup"><span data-stu-id="ea798-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="ea798-112">O tipo de identidade deve ser usada depende do tipo de credenciais de segurança usadas na associação do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ea798-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>  
  
-   <span data-ttu-id="ea798-113">Identidade pode ser definida declarativamente na configuração ou imperativa no código.</span><span class="sxs-lookup"><span data-stu-id="ea798-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="ea798-114">Normalmente para o cliente e o serviço, você deve usar configuração para definir a identidade.</span><span class="sxs-lookup"><span data-stu-id="ea798-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>  
  
-   <span data-ttu-id="ea798-115">Como definir uma identidade personalizada no cliente.</span><span class="sxs-lookup"><span data-stu-id="ea798-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="ea798-116">Uma identidade personalizada é normalmente uma personalização de um tipo existente de identidade, que permite que o cliente examinar outras informações de declaração fornecidas nas credenciais do serviço para tomar decisões de autorização antes de chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ea798-117">Este exemplo verifica a identidade de um certificado específico chamado identity.com e a chave RSA contidos no certificado.</span><span class="sxs-lookup"><span data-stu-id="ea798-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="ea798-118">Ao usar os tipos de identidade do certificado e RSA na configuração no cliente, uma maneira fácil de obter esses valores é inspecionar o WSDL para o serviço em que esses valores são serializados.</span><span class="sxs-lookup"><span data-stu-id="ea798-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>  
  
 <span data-ttu-id="ea798-119">O código de exemplo a seguir mostra como configurar a identidade de um ponto de extremidade de serviço com o servidor DNS (Domain Name) de um certificado usando o WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="ea798-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 <span data-ttu-id="ea798-120">A identidade também pode ser especificada na configuração no arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="ea798-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="ea798-121">O exemplo a seguir mostra como definir a identidade UPN (Nome Principal do usuário) para um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>  
  
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
  
 <span data-ttu-id="ea798-122">Uma identidade personalizada pode ser definida no cliente, derivando o <xref:System.ServiceModel.EndpointIdentity> e <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span><span class="sxs-lookup"><span data-stu-id="ea798-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="ea798-123">Conceitualmente o <xref:System.ServiceModel.Security.IdentityVerifier> classe pode ser considerada como o cliente equivalente do serviço de `AuthorizationManager` classe.</span><span class="sxs-lookup"><span data-stu-id="ea798-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="ea798-124">O exemplo de código a seguir mostra uma implementação de `OrgEndpointIdentity`, que armazena um nome de organização para fazer a correspondência no nome da entidade do certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="ea798-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="ea798-125">A verificação de autorização para o nome da organização ocorre no `CheckAccess` método o `CustomIdentityVerifier` classe.</span><span class="sxs-lookup"><span data-stu-id="ea798-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>  
  
```  
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
  
 <span data-ttu-id="ea798-126">Este exemplo usa um certificado chamado identity.com que está na pasta de solução de identidade específico do idioma.</span><span class="sxs-lookup"><span data-stu-id="ea798-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ea798-127">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="ea798-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ea798-128">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea798-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ea798-129">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea798-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ea798-130">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ea798-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ea798-131">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="ea798-131">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="ea798-132">Em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou [!INCLUDE[wv](../../../../includes/wv-md.md)], importe o arquivo de certificado Identity.pfx na pasta de solução de identidade para o repositório de LocalMachine/meu certificado (pessoal) usando a ferramenta snap-in do MMC.</span><span class="sxs-lookup"><span data-stu-id="ea798-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="ea798-133">Esse arquivo é protegido por senha.</span><span class="sxs-lookup"><span data-stu-id="ea798-133">This file is password protected.</span></span> <span data-ttu-id="ea798-134">Durante a importação, você será solicitado para uma senha.</span><span class="sxs-lookup"><span data-stu-id="ea798-134">During the import you are asked for a password.</span></span> <span data-ttu-id="ea798-135">Tipo `xyz` na caixa de senha.</span><span class="sxs-lookup"><span data-stu-id="ea798-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="ea798-136">Para obter mais informações, consulte o [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="ea798-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="ea798-137">Depois que isso for feito, execute bat em um prompt de comando Visual Studio com privilégios de administrador, que copia o certificado no armazenamento de pessoas confiáveis CurrentUser para uso no cliente.</span><span class="sxs-lookup"><span data-stu-id="ea798-137">Once this is done, run Setup.bat in a Visual Studio command prompt with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>  
  
2.  <span data-ttu-id="ea798-138">Em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="ea798-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt with administrator privileges.</span></span> <span data-ttu-id="ea798-139">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea798-139">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ea798-140">O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ea798-140">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="ea798-141">Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.</span><span class="sxs-lookup"><span data-stu-id="ea798-141">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="ea798-142">Certifique-se de que você remova os certificados executando Cleanup.bat quando você tiver terminado com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea798-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="ea798-143">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="ea798-143">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="ea798-144">Inicie Service.exe do diretório \service\bin.</span><span class="sxs-lookup"><span data-stu-id="ea798-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="ea798-145">Certifique-se de que o serviço indica que ele está pronto e exibe um prompt para pressionar \<Enter > para encerrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4.  <span data-ttu-id="ea798-146">Inicie o Client.exe do diretório \Client\Bin. ou pressionando F5 no Visual Studio para criar e executar.</span><span class="sxs-lookup"><span data-stu-id="ea798-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="ea798-147">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="ea798-147">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="ea798-148">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ea798-148">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ea798-149">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="ea798-149">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="ea798-150">Antes de criar a parte cliente de exemplo, certifique-se de alterar o valor para o endereço de ponto de extremidade do serviço no arquivo de Client.cs o `CallServiceCustomClientIdentity` método.</span><span class="sxs-lookup"><span data-stu-id="ea798-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="ea798-151">Em seguida, crie o exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea798-151">Then build the sample.</span></span>  
  
2.  <span data-ttu-id="ea798-152">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-152">Create a directory on the service computer.</span></span>  
  
3.  <span data-ttu-id="ea798-153">Copie os arquivos de programa do serviço de service\bin para o diretório no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="ea798-154">Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4.  <span data-ttu-id="ea798-155">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="ea798-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5.  <span data-ttu-id="ea798-156">Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="ea798-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="ea798-157">Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ea798-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6.  <span data-ttu-id="ea798-158">Sobre o serviço, execute `setup.bat service` em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="ea798-158">On the service, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="ea798-159">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="ea798-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7.  <span data-ttu-id="ea798-160">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="ea798-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="ea798-161">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ea798-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="ea798-162">Há várias instâncias que devem ser alteradas.</span><span class="sxs-lookup"><span data-stu-id="ea798-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="ea798-163">No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="ea798-163">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="ea798-164">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="ea798-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="ea798-165">No computador do serviço, inicie o Service.exe do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ea798-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="ea798-166">No computador cliente, inicie o Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ea798-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="ea798-167">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="ea798-167">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ea798-168">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="ea798-168">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="ea798-169">Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="ea798-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ea798-170">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="ea798-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="ea798-171">Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="ea798-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="ea798-172">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="ea798-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea798-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea798-173">See Also</span></span>
