---
title: Segurança de mensagem anônima
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 0665ce331492a5322fdfde9e91fc1dae5b8e7ea8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424103"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="0c0b0-102">Segurança de mensagem anônima</span><span class="sxs-lookup"><span data-stu-id="0c0b0-102">Message Security Anonymous</span></span>
<span data-ttu-id="0c0b0-103">O exemplo de segurança de mensagem anônima demonstra como implementar um aplicativo Windows Communication Foundation (WCF) que usa segurança em nível de mensagem sem autenticação de cliente, mas que requer autenticação de servidor usando X. 509 do servidor Certificate.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-103">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="0c0b0-104">Todas as mensagens de aplicativo entre o cliente e o servidor são assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="0c0b0-105">Este exemplo é baseado no exemplo de [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0c0b0-105">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span> <span data-ttu-id="0c0b0-106">Este exemplo consiste em um programa de console do cliente (. exe) e uma biblioteca de serviços (. dll) hospedados pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="0c0b0-107">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="0c0b0-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="0c0b0-109">Este exemplo adiciona uma nova operação à interface de calculadora que retorna `True` se o cliente não foi autenticado.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

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

 <span data-ttu-id="0c0b0-110">O serviço expõe um único ponto de extremidade para se comunicar com o serviço, definido usando um arquivo de configuração (Web. config).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="0c0b0-111">O ponto de extremidade consiste em um endereço, uma associação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="0c0b0-112">A associação é configurada com uma associação de `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="0c0b0-113">O modo de segurança padrão para a associação de `wsHttpBinding` é `Message`.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="0c0b0-114">O atributo `clientCredentialType` é definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-114">The `clientCredentialType` attribute is set to `None`.</span></span>

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

 <span data-ttu-id="0c0b0-115">As credenciais a serem usadas para autenticação de serviço são especificadas no [comportamento de\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="0c0b0-116">O certificado do servidor deve conter o mesmo valor para o `SubjectName` como o valor especificado para o atributo `findValue`, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

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

 <span data-ttu-id="0c0b0-117">A configuração de ponto de extremidade do cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="0c0b0-118">O modo de segurança do cliente para a associação de `wsHttpBinding` é `Message`.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="0c0b0-119">O atributo `clientCredentialType` é definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-119">The `clientCredentialType` attribute is set to `None`.</span></span>

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

 <span data-ttu-id="0c0b0-120">O exemplo define o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> como <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> para autenticar o certificado do serviço.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="0c0b0-121">Isso é feito no arquivo app. config do cliente na seção `behaviors`.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="0c0b0-122">Isso significa que, se o certificado estiver no repositório de pessoas confiáveis do usuário, ele será confiável sem executar uma validação da cadeia do emissor do certificado.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="0c0b0-123">Essa configuração é usada aqui para conveniência para que o exemplo possa ser executado sem a necessidade de certificados emitidos por uma autoridade de certificação (CA).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="0c0b0-124">Essa configuração é menos segura do que o padrão, ChainTrust.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="0c0b0-125">As implicações de segurança dessa configuração devem ser consideradas cuidadosamente antes de usar `PeerOrChainTrust` no código de produção.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="0c0b0-126">A implementação do cliente adiciona uma chamada ao método `IsCallerAnonymous` e, caso contrário, não difere da amostra de [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0c0b0-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>

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

 <span data-ttu-id="0c0b0-127">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0c0b0-128">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-128">Press ENTER in the client window to shut down the client.</span></span>

```console
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="0c0b0-129">O arquivo em lotes setup. bat incluído com a mensagem segurança de exemplo Anonymous permite que você configure o servidor com um certificado relevante para executar um aplicativo hospedado que requer segurança baseada em certificado.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="0c0b0-130">O arquivo em lotes pode ser executado em dois modos.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="0c0b0-131">Para executar o arquivo em lotes no modo de computador único, digite `setup.bat` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="0c0b0-132">Para executá-lo no modo de serviço, digite `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="0c0b0-133">Use esse modo ao executar o exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="0c0b0-134">Consulte o procedimento de instalação no final deste tópico para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-134">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="0c0b0-135">Veja a seguir uma breve visão geral das diferentes seções dos arquivos em lotes:</span><span class="sxs-lookup"><span data-stu-id="0c0b0-135">The following provides a brief overview of the different sections of the batch files:</span></span>

- <span data-ttu-id="0c0b0-136">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-136">Creating the server certificate.</span></span>

     <span data-ttu-id="0c0b0-137">As linhas a seguir do arquivo em lotes setup. bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="0c0b0-138">A variável% SERVER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="0c0b0-139">O certificado é armazenado no armazenamento LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="0c0b0-140">Se o arquivo em lotes de instalação for executado com um argumento de serviço (como `setup.bat service`), o% SERVER_NAME% conterá o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="0c0b0-141">Caso contrário, o padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-141">Otherwise it defaults to localhost.</span></span>

- <span data-ttu-id="0c0b0-142">Instalar o certificado do servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-142">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="0c0b0-143">A linha a seguir copia o certificado do servidor no repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="0c0b0-144">Essa etapa é necessária porque os certificados gerados pelo MakeCert. exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="0c0b0-145">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="0c0b0-146">Concedendo permissões na chave privada do certificado.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-146">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="0c0b0-147">As linhas a seguir no arquivo em lotes setup. bat tornam o certificado do servidor armazenado no repositório LocalMachine acessível para a conta de processo de trabalho do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>

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
> <span data-ttu-id="0c0b0-148">Se você estiver usando uma edição que não seja a U. S. em inglês do Windows, deverá editar o arquivo setup. bat e substituir o nome da conta de `NT AUTHORITY\NETWORK SERVICE` pelo equivalente regional.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0c0b0-149">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0c0b0-149">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0c0b0-150">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0c0b0-151">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="0c0b0-152">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="0c0b0-152">To run the sample on the same computer</span></span>

1. <span data-ttu-id="0c0b0-153">Verifique se o caminho inclui a pasta em que o MakeCert. exe e o FindPrivateKey. exe estão localizados.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2. <span data-ttu-id="0c0b0-154">Execute setup. bat da pasta de instalação de exemplo em um Prompt de Comando do Desenvolvedor para o Visual Studio executar com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-154">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="0c0b0-155">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-155">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0c0b0-156">O arquivo em lotes de instalação foi projetado para ser executado de um Prompt de Comando do Desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-156">The setup batch file is designed to be run from a  Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="0c0b0-157">Ele requer que a variável de ambiente Path aponte para o diretório em que o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="0c0b0-158">Essa variável de ambiente é definida automaticamente dentro de um Prompt de Comando do Desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-158">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="0c0b0-159">Verifique o acesso ao serviço usando um navegador inserindo o endereço `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-159">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4. <span data-ttu-id="0c0b0-160">Inicie o Client. exe em \client\bin.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="0c0b0-161">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-161">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="0c0b0-162">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-162">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="0c0b0-163">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="0c0b0-163">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="0c0b0-164">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-164">Create a directory on the service computer.</span></span> <span data-ttu-id="0c0b0-165">Crie um aplicativo virtual chamado servicemodelsamples para esse diretório usando a ferramenta de gerenciamento do Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="0c0b0-166">Copie os arquivos de programa do serviço do \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="0c0b0-167">Certifique-se de copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="0c0b0-168">Copie também os arquivos Setup. bat e Cleanup. bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="0c0b0-169">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="0c0b0-170">Copie os arquivos de programa do cliente para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="0c0b0-171">Copie também os arquivos Setup. bat, Cleanup. bat e ImportServiceCert. bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="0c0b0-172">No servidor, execute `setup.bat service` em um Prompt de Comando do Desenvolvedor para o Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-172">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="0c0b0-173">A execução de `setup.bat` com o argumento `service` cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service. cer.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="0c0b0-174">Edite Web. config para refletir o novo nome de certificado (no atributo `findValue` no [> de\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)ServiceName), que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="0c0b0-175">Copie o arquivo Service. cer do diretório de serviço para o diretório cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="0c0b0-176">No arquivo client. exe. config no computador cliente, altere o valor de endereço do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="0c0b0-177">No cliente, execute ImportServiceCert. bat em um Prompt de Comando do Desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-177">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="0c0b0-178">Isso importa o certificado de serviço do arquivo Service. cer para o repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="0c0b0-179">No computador cliente, inicie o Client. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="0c0b0-180">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0c0b0-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0c0b0-181">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="0c0b0-181">To clean up after the sample</span></span>  
  
- <span data-ttu-id="0c0b0-182">Execute o Cleanup. bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c0b0-183">Esse script não remove certificados de serviço em um cliente ao executar esse exemplo em computadores.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="0c0b0-184">Se você tiver executado Windows Communication Foundation (WCF) exemplos que usam certificados entre computadores, certifique-se de limpar os certificados de serviço que foram instalados no repositório CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="0c0b0-184">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="0c0b0-185">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="0c0b0-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>
