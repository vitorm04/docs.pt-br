---
title: Certificado de mensagem de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: eea5317cbd3a41ba90c9d9d0f2a890dee5e9124b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930571"
---
# <a name="message-security-certificate"></a><span data-ttu-id="5bebe-102">Certificado de mensagem de segurança</span><span class="sxs-lookup"><span data-stu-id="5bebe-102">Message Security Certificate</span></span>
<span data-ttu-id="5bebe-103">Este exemplo demonstra como implementar um aplicativo que usa o WS-Security com a autenticação de certificado X. 509 v3 para o cliente e requer autenticação de servidor usando o certificado X. 509 v3 do servidor.</span><span class="sxs-lookup"><span data-stu-id="5bebe-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="5bebe-104">Este exemplo usa configurações padrão, de modo que todas as mensagens de aplicativo entre o cliente e o servidor sejam assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="5bebe-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="5bebe-105">Este exemplo se baseia na [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) e consiste em um programa de console do cliente e uma biblioteca de serviços hospedada pelo serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="5bebe-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="5bebe-106">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="5bebe-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bebe-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5bebe-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5bebe-108">O exemplo demonstra como controlar a autenticação usando a configuração e como obter a identidade do chamador do contexto de segurança, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5bebe-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="5bebe-109">O serviço expõe um ponto de extremidade para se comunicar com o serviço e um ponto de extremidade para expor o documento WSDL do serviço usando o protocolo WS-MetadataExchange, definido usando o arquivo de configuração (Web. config).</span><span class="sxs-lookup"><span data-stu-id="5bebe-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="5bebe-110">O ponto de extremidade consiste em um endereço, uma associação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="5bebe-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="5bebe-111">A associação é configurada com um elemento de [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) padrão, que usa a segurança da mensagem como padrão.</span><span class="sxs-lookup"><span data-stu-id="5bebe-111">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="5bebe-112">Este exemplo define o `clientCredentialType` atributo como certificado para exigir autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="5bebe-113">O comportamento especifica as credenciais do serviço que são usadas quando o cliente autentica o serviço.</span><span class="sxs-lookup"><span data-stu-id="5bebe-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="5bebe-114">O nome da entidade do certificado do servidor é `findValue` especificado no atributo [ \<do elemento ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="5bebe-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="5bebe-115">A configuração de ponto de extremidade do cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="5bebe-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="5bebe-116">A associação de cliente é configurada com o modo de segurança e o modos de autenticação apropriados.</span><span class="sxs-lookup"><span data-stu-id="5bebe-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="5bebe-117">Ao executar em um cenário entre computadores, verifique se o endereço do ponto de extremidade de serviço foi alterado de acordo.</span><span class="sxs-lookup"><span data-stu-id="5bebe-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5bebe-118">A implementação do cliente pode definir o certificado a ser usado, seja pelo arquivo de configuração ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="5bebe-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="5bebe-119">O exemplo a seguir mostra como definir o certificado a ser usado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5bebe-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5bebe-120">O exemplo a seguir mostra como chamar o serviço em seu programa.</span><span class="sxs-lookup"><span data-stu-id="5bebe-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="5bebe-121">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5bebe-122">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="5bebe-123">O arquivo em lotes setup. bat incluído com os exemplos de segurança de mensagem permite que você configure o cliente e o servidor com certificados relevantes para executar um aplicativo hospedado que requer segurança baseada em certificado.</span><span class="sxs-lookup"><span data-stu-id="5bebe-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="5bebe-124">O arquivo em lotes pode ser executado em três modos.</span><span class="sxs-lookup"><span data-stu-id="5bebe-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="5bebe-125">Para executar em modo de computador único, digite **Setup. bat** em um prompt de comando do desenvolvedor para o Visual Studio; para o tipo de modo de serviço **Setup. bat Service**; e, para o modo de cliente, digite **Setup. bat cliente**.</span><span class="sxs-lookup"><span data-stu-id="5bebe-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="5bebe-126">Use o modo de cliente e servidor ao executar o exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="5bebe-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="5bebe-127">Consulte o procedimento de instalação no final deste tópico para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="5bebe-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="5bebe-128">Veja a seguir uma breve visão geral das diferentes seções dos arquivos em lotes para que eles possam ser modificados para serem executados na configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="5bebe-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
- <span data-ttu-id="5bebe-129">Criando o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="5bebe-130">A linha a seguir no arquivo em lotes cria o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="5bebe-131">O nome do cliente especificado é usado no nome da entidade do certificado criado.</span><span class="sxs-lookup"><span data-stu-id="5bebe-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="5bebe-132">O certificado é armazenado no `My` repositório no local `CurrentUser` da loja.</span><span class="sxs-lookup"><span data-stu-id="5bebe-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="5bebe-133">Instalar o certificado do cliente no repositório de certificados confiáveis do servidor.</span><span class="sxs-lookup"><span data-stu-id="5bebe-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="5bebe-134">A linha a seguir no arquivo em lotes copia o certificado do cliente no repositório TrustedPeople do servidor para que o servidor possa fazer as decisões relevantes de confiança ou sem confiança.</span><span class="sxs-lookup"><span data-stu-id="5bebe-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="5bebe-135">Para que um certificado instalado no repositório TrustedPeople seja confiável por um serviço Windows Communication Foundation (WCF), o modo de validação de certificado do cliente deve ser definido como `PeerOrChainTrust` ou `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="5bebe-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="5bebe-136">Consulte o exemplo de configuração de serviço anterior para saber como isso pode ser feito usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5bebe-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople   
    ```  
  
- <span data-ttu-id="5bebe-137">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="5bebe-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="5bebe-138">As linhas a seguir do arquivo em lotes setup. bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="5bebe-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="5bebe-139">A variável% SERVER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="5bebe-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="5bebe-140">O certificado é armazenado no armazenamento LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5bebe-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="5bebe-141">Se o arquivo em lotes setup. bat for executado com um argumento de serviço (como o **serviço setup. bat**), o% server_name% conterá o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="5bebe-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="5bebe-142">Caso contrário, o padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="5bebe-142">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="5bebe-143">Instalar o certificado do servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="5bebe-144">A linha a seguir copia o certificado do servidor no repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="5bebe-145">Essa etapa é necessária porque os certificados gerados pelo MakeCert. exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="5bebe-146">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="5bebe-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="5bebe-147">Concedendo permissões na chave privada do certificado.</span><span class="sxs-lookup"><span data-stu-id="5bebe-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="5bebe-148">As linhas a seguir no arquivo setup. bat tornam o certificado do servidor armazenado no repositório LocalMachine acessível para a conta de processo de trabalho do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5bebe-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5bebe-149">Se você estiver usando um que não seja U. S. Edição em inglês do Windows, você deve editar o arquivo setup. bat e substituir o nome da conta "NT AUTHORITY\NETWORK SERVICE" pelo equivalente regional.</span><span class="sxs-lookup"><span data-stu-id="5bebe-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bebe-150">As ferramentas usadas neste arquivo em lotes estão localizadas em C:\Arquivos de Programas\microsoft Visual Studio 8 \ Common7\tools ou C:\Arquivos de Programas\microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="5bebe-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="5bebe-151">Um desses diretórios deve estar no caminho do sistema.</span><span class="sxs-lookup"><span data-stu-id="5bebe-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="5bebe-152">Se você tiver o Visual Studio instalado, a maneira mais fácil de obter esse diretório em seu caminho é abrir o Prompt de Comando do Desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5bebe-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="5bebe-153">Clique em **Iniciar**e selecione **todos os programas**, **Visual Studio 2012**, **ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5bebe-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="5bebe-154">Esse prompt de comando tem os caminhos apropriados já configurados.</span><span class="sxs-lookup"><span data-stu-id="5bebe-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="5bebe-155">Caso contrário, você deve adicionar o diretório apropriado ao caminho manualmente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5bebe-156">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5bebe-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5bebe-157">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="5bebe-157">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5bebe-158">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="5bebe-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5bebe-159">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="5bebe-159">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5bebe-160">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5bebe-160">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5bebe-161">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5bebe-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5bebe-162">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5bebe-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5bebe-163">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="5bebe-163">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="5bebe-164">Abra um Prompt de Comando do Desenvolvedor para o Visual Studio com privilégios de administrador e execute Setup. bat na pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="5bebe-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="5bebe-165">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="5bebe-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5bebe-166">O arquivo em lotes setup. bat foi projetado para ser executado de um Prompt de Comando do Desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5bebe-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="5bebe-167">Ele requer que a variável de ambiente Path aponte para o diretório em que o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="5bebe-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="5bebe-168">Essa variável de ambiente é definida automaticamente dentro de um Prompt de Comando do Desenvolvedor para o Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="5bebe-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="5bebe-169">Verifique o acesso ao serviço usando um navegador inserindo o endereço `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="5bebe-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="5bebe-170">Inicie o Client.exe no \client\bin.</span><span class="sxs-lookup"><span data-stu-id="5bebe-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="5bebe-171">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-171">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="5bebe-172">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5bebe-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5bebe-173">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="5bebe-173">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="5bebe-174">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="5bebe-174">Create a directory on the service computer.</span></span> <span data-ttu-id="5bebe-175">Crie um aplicativo virtual chamado servicemodelsamples para esse diretório usando a ferramenta de gerenciamento do Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="5bebe-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="5bebe-176">Copie os arquivos de programa do serviço do \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="5bebe-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="5bebe-177">Certifique-se de copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="5bebe-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="5bebe-178">Copie também os arquivos Setup. bat, Cleanup. bat e ImportClientCert. bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="5bebe-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="5bebe-179">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="5bebe-180">Copie os arquivos de programa do cliente para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="5bebe-181">Copie também os arquivos Setup. bat, Cleanup. bat e ImportServiceCert. bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="5bebe-182">No servidor, execute o **serviço setup. bat** em um prompt de comando do desenvolvedor para o Visual Studio com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="5bebe-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="5bebe-183">A execução de **Setup. bat** com o argumento de **serviço** cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service. cer.</span><span class="sxs-lookup"><span data-stu-id="5bebe-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="5bebe-184">Edite Web. config para refletir o novo nome do certificado ( `findValue` no atributo no [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)do Service-Certificate), que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="5bebe-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="5bebe-185">Copie o arquivo Service. cer do diretório de serviço para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="5bebe-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="5bebe-186">No cliente, execute o **cliente setup. bat** em um prompt de comando do desenvolvedor para o Visual Studio com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="5bebe-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="5bebe-187">A execução de **Setup. bat** com o argumento **Client** cria um certificado de cliente chamado Client.com e exporta o certificado do cliente para um arquivo chamado Client. cer.</span><span class="sxs-lookup"><span data-stu-id="5bebe-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="5bebe-188">No arquivo client. exe. config no computador cliente, altere o valor de endereço do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="5bebe-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="5bebe-189">Faça isso substituindo localhost pelo nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="5bebe-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="5bebe-190">Copie o arquivo client. cer do diretório cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="5bebe-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="5bebe-191">No cliente, execute ImportServiceCert. bat em um Prompt de Comando do Desenvolvedor para o Visual Studio com privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="5bebe-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="5bebe-192">Isso importa o certificado de serviço do arquivo Service. cer para o repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="5bebe-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="5bebe-193">No servidor, execute ImportClientCert. bat em um Prompt de Comando do Desenvolvedor para o Visual Studio com privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="5bebe-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="5bebe-194">Isso importa o certificado do cliente do arquivo client. cer para o repositório LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="5bebe-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="5bebe-195">No computador cliente, inicie o Client. exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="5bebe-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="5bebe-196">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5bebe-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5bebe-197">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="5bebe-197">To clean up after the sample</span></span>  
  
- <span data-ttu-id="5bebe-198">Execute o Cleanup. bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="5bebe-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5bebe-199">Esse script não remove certificados de serviço em um cliente ao executar esse exemplo em computadores.</span><span class="sxs-lookup"><span data-stu-id="5bebe-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="5bebe-200">Se você tiver executado Windows Communication Foundation (WCF) exemplos que usam certificados entre computadores, certifique-se de limpar os certificados de serviço que foram instalados no repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="5bebe-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="5bebe-201">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="5bebe-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
