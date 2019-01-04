---
title: Segurança de mensagem anônima
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: bca5942985ca5a0af8ce504565506cda8c396d16
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029925"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="8b58a-102">Segurança de mensagem anônima</span><span class="sxs-lookup"><span data-stu-id="8b58a-102">Message Security Anonymous</span></span>
<span data-ttu-id="8b58a-103">O exemplo de segurança de mensagem anônimo demonstra como implementar um aplicativo do Windows Communication Foundation (WCF) que usa a segurança de nível de mensagem sem autenticação de cliente, mas que requer autenticação de servidor usando o X.509 do servidor certificado.</span><span class="sxs-lookup"><span data-stu-id="8b58a-103">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="8b58a-104">Todas as mensagens de aplicativo entre o cliente e servidor assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="8b58a-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="8b58a-105">Este exemplo se baseia a [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="8b58a-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span> <span data-ttu-id="8b58a-106">Esse exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="8b58a-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="8b58a-107">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="8b58a-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
>  <span data-ttu-id="8b58a-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="8b58a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="8b58a-109">Este exemplo adiciona uma nova operação para a interface de calculadora retorna `True` se o cliente não foi autenticado.</span><span class="sxs-lookup"><span data-stu-id="8b58a-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 <span data-ttu-id="8b58a-110">O serviço expõe um ponto de extremidade para se comunicar com o serviço, definido usando um arquivo de configuração (Web. config).</span><span class="sxs-lookup"><span data-stu-id="8b58a-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="8b58a-111">O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="8b58a-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="8b58a-112">A associação está configurada com um `wsHttpBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="8b58a-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="8b58a-113">O modo de segurança padrão para o `wsHttpBinding` associação é `Message`.</span><span class="sxs-lookup"><span data-stu-id="8b58a-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="8b58a-114">O `clientCredentialType` atributo é definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="8b58a-114">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="8b58a-115">As credenciais a serem usadas para autenticação de serviço são especificadas na [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span><span class="sxs-lookup"><span data-stu-id="8b58a-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="8b58a-116">O certificado do servidor deve conter o mesmo valor para o `SubjectName` como o valor especificado para o `findValue` atributo conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b58a-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="8b58a-117">A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="8b58a-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="8b58a-118">O modo de segurança do cliente para o `wsHttpBinding` associação é `Message`.</span><span class="sxs-lookup"><span data-stu-id="8b58a-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="8b58a-119">O `clientCredentialType` atributo é definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="8b58a-119">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="8b58a-120">O exemplo define o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> para <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> para autenticar o certificado do serviço.</span><span class="sxs-lookup"><span data-stu-id="8b58a-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="8b58a-121">Isso é feito no arquivo de App. config do cliente no `behaviors` seção.</span><span class="sxs-lookup"><span data-stu-id="8b58a-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="8b58a-122">Isso significa que se o certificado estiver no armazenamento de pessoas confiáveis do usuário, em seguida, ele é confiável sem executar uma validação de cadeia de emissores do certificado.</span><span class="sxs-lookup"><span data-stu-id="8b58a-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="8b58a-123">Essa configuração é usada aqui para sua conveniência para que o exemplo pode ser executado sem a necessidade de certificados emitidos por uma autoridade de certificação (CA).</span><span class="sxs-lookup"><span data-stu-id="8b58a-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="8b58a-124">Essa configuração é menos segura do que o padrão, ChainTrust.</span><span class="sxs-lookup"><span data-stu-id="8b58a-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="8b58a-125">As implicações de segurança dessa configuração devem ser consideradas com cuidado antes de usar `PeerOrChainTrust` no código de produção.</span><span class="sxs-lookup"><span data-stu-id="8b58a-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="8b58a-126">A implementação do cliente adiciona uma chamada para o `IsCallerAnonymous` método e, caso contrário, não será diferente do [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="8b58a-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="8b58a-127">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8b58a-128">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-128">Press ENTER in the client window to shut down the client.</span></span>

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="8b58a-129">O arquivo em lotes de Setup. bat incluído no exemplo de segurança de mensagem anônima permite que você configure o servidor com um certificado apropriado para executar um aplicativo hospedado que exige a segurança baseada em certificado.</span><span class="sxs-lookup"><span data-stu-id="8b58a-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="8b58a-130">O arquivo em lotes pode ser executado em dois modos.</span><span class="sxs-lookup"><span data-stu-id="8b58a-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="8b58a-131">Para executar o arquivo em lote no modo único computador, digite `setup.bat` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="8b58a-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="8b58a-132">Para executá-lo no modo de serviço, digite `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="8b58a-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="8b58a-133">Use este modo, ao executar a amostra entre computadores.</span><span class="sxs-lookup"><span data-stu-id="8b58a-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="8b58a-134">Consulte o procedimento de instalação no final deste tópico para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="8b58a-134">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="8b58a-135">O exemplo a seguir fornece uma visão geral das diferentes seções dos arquivos de lote:</span><span class="sxs-lookup"><span data-stu-id="8b58a-135">The following provides a brief overview of the different sections of the batch files:</span></span>

-   <span data-ttu-id="8b58a-136">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="8b58a-136">Creating the server certificate.</span></span>

     <span data-ttu-id="8b58a-137">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="8b58a-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="8b58a-138">A variável % SERVER_NAME % Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="8b58a-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="8b58a-139">O certificado é armazenado no repositório de LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="8b58a-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="8b58a-140">Se o arquivo de lote é executado com um argumento de serviço (como `setup.bat service`) % % SERVER_NAME contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="8b58a-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="8b58a-141">Caso contrário, o padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="8b58a-141">Otherwise it defaults to localhost.</span></span>

-   <span data-ttu-id="8b58a-142">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-142">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="8b58a-143">A linha a seguir copia o certificado do servidor para o repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="8b58a-144">Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="8b58a-145">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="8b58a-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   <span data-ttu-id="8b58a-146">Concedendo permissões de chave privada do certificado.</span><span class="sxs-lookup"><span data-stu-id="8b58a-146">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="8b58a-147">As seguintes linhas no arquivo em lotes bat Verifique o certificado de servidor armazenado no repositório de LocalMachine acessível para o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] conta de processo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8b58a-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
>  <span data-ttu-id="8b58a-148">Se você estiver usando um fora dos EUA Edição em inglês do Windows, você deve editar o arquivo Setup. bat e substitua o `NT AUTHORITY\NETWORK SERVICE` nome da conta com seu equivalente regional.</span><span class="sxs-lookup"><span data-stu-id="8b58a-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8b58a-149">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="8b58a-149">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="8b58a-150">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b58a-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="8b58a-151">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b58a-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="8b58a-152">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="8b58a-152">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="8b58a-153">Certifique-se de que o caminho inclui a pasta onde Makecert.exe e FindPrivateKey.exe estão localizados.</span><span class="sxs-lookup"><span data-stu-id="8b58a-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2.  <span data-ttu-id="8b58a-154">Execute Setup. bat da pasta de instalação de exemplo em um prompt de comando do Visual Studio executar com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="8b58a-154">Run Setup.bat from the sample install folder in a Visual Studio command prompt run with administrator privileges.</span></span> <span data-ttu-id="8b58a-155">Essa opção instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="8b58a-155">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8b58a-156">O arquivo de lote é criado para ser executado em um Prompt de comando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8b58a-156">The setup batch file is designed to be run from a  Visual Studio Command Prompt.</span></span> <span data-ttu-id="8b58a-157">Ele requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="8b58a-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="8b58a-158">Essa variável de ambiente é definido automaticamente dentro de um Prompt de comando Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8b58a-158">This environment variable is automatically set within a Visual Studio Command Prompt.</span></span>  
  
3.  <span data-ttu-id="8b58a-159">Verificar o acesso ao serviço usando um navegador, inserindo o endereço `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="8b58a-159">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4.  <span data-ttu-id="8b58a-160">Inicie o Client.exe no \client\bin.</span><span class="sxs-lookup"><span data-stu-id="8b58a-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="8b58a-161">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-161">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="8b58a-162">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="8b58a-162">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="8b58a-163">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="8b58a-163">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="8b58a-164">Crie um diretório no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="8b58a-164">Create a directory on the service computer.</span></span> <span data-ttu-id="8b58a-165">Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="8b58a-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="8b58a-166">Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="8b58a-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="8b58a-167">Certifique-se de que você copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="8b58a-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="8b58a-168">Também copie os arquivos Setup. bat e Cleanup para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="8b58a-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="8b58a-169">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="8b58a-170">Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="8b58a-171">Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="8b58a-172">No servidor, execute `setup.bat service` em um prompt de comando do Visual Studio aberta com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="8b58a-172">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="8b58a-173">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="8b58a-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="8b58a-174">Editar o Web. config para refletir o novo nome do certificado (na `findValue` de atributo no [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), que é igual ao nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="8b58a-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="8b58a-175">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="8b58a-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="8b58a-176">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="8b58a-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="8b58a-177">No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="8b58a-177">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="8b58a-178">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="8b58a-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="8b58a-179">No computador cliente, inicie Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="8b58a-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="8b58a-180">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="8b58a-180">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="8b58a-181">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="8b58a-181">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="8b58a-182">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="8b58a-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b58a-183">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="8b58a-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="8b58a-184">Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store.</span><span class="sxs-lookup"><span data-stu-id="8b58a-184">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="8b58a-185">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="8b58a-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>

## <a name="see-also"></a><span data-ttu-id="8b58a-186">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b58a-186">See Also</span></span>
