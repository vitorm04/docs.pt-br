---
title: Message Security User Name
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183508"
---
# <a name="message-security-user-name"></a><span data-ttu-id="2036c-102">Message Security User Name</span><span class="sxs-lookup"><span data-stu-id="2036c-102">Message Security User Name</span></span>
<span data-ttu-id="2036c-103">Esta amostra demonstra como implementar um aplicativo que usa o WS-Security com autenticação de nome de usuário para o cliente e requer autenticação do servidor usando o certificado X.509v3 do servidor.</span><span class="sxs-lookup"><span data-stu-id="2036c-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="2036c-104">Todas as mensagens de aplicativo entre o cliente e o servidor são assinadas e criptografadas.</span><span class="sxs-lookup"><span data-stu-id="2036c-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="2036c-105">Por padrão, o nome de usuário e a senha fornecidos pelo cliente são usados para fazer logon em uma conta válida do Windows.</span><span class="sxs-lookup"><span data-stu-id="2036c-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="2036c-106">Esta amostra é baseada no [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2036c-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="2036c-107">Esta amostra consiste em um programa de console cliente (Client.exe) e uma biblioteca de serviços (Service.dll) hospedada pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="2036c-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="2036c-108">O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="2036c-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2036c-109">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2036c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2036c-110">Esta amostra também demonstra:</span><span class="sxs-lookup"><span data-stu-id="2036c-110">This sample also demonstrates:</span></span>  
  
- <span data-ttu-id="2036c-111">O mapeamento padrão para contas do Windows para que a autorização adicional possa ser realizada.</span><span class="sxs-lookup"><span data-stu-id="2036c-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
- <span data-ttu-id="2036c-112">Como acessar as informações de identidade do chamador a partir do código de serviço.</span><span class="sxs-lookup"><span data-stu-id="2036c-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="2036c-113">O serviço expõe um único ponto final para se comunicar com o serviço, que é definido usando o arquivo de configuração Web.config. O ponto final consiste em um endereço, um vinculativo e um contrato.</span><span class="sxs-lookup"><span data-stu-id="2036c-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2036c-114">A vinculação é configurada com um>padrão [ \<wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), que é padrão para usar a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2036c-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="2036c-115">Esta amostra define o padrão [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) para usar a autenticação do nome de usuário do cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="2036c-116">O comportamento especifica que as credenciais do usuário devem ser usadas para autenticação de serviço.</span><span class="sxs-lookup"><span data-stu-id="2036c-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="2036c-117">O certificado de servidor deve conter o `findValue` mesmo valor para o nome do objeto que o atributo no [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="2036c-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
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
</system.serviceModel>  
```  
  
 <span data-ttu-id="2036c-118">A configuração de ponto final do cliente consiste em um endereço absoluto para o ponto final do serviço, a vinculação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="2036c-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="2036c-119">A vinculação do cliente `securityMode` é `authenticationMode`configurada com o apropriado e .</span><span class="sxs-lookup"><span data-stu-id="2036c-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="2036c-120">Ao ser executado em um cenário de computador entre computadores, o endereço de ponto final de serviço deve ser alterado em conformidade.</span><span class="sxs-lookup"><span data-stu-id="2036c-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="2036c-121">A implementação do cliente define o nome de usuário e a senha a serem usados.</span><span class="sxs-lookup"><span data-stu-id="2036c-121">The client implementation sets the user name and password to use.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 <span data-ttu-id="2036c-122">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2036c-123">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="2036c-124">O arquivo de lote Setup.bat incluído com as amostras MessageSecurity permite configurar o servidor com um certificado relevante para executar um aplicativo hospedado que requer segurança baseada em certificados.</span><span class="sxs-lookup"><span data-stu-id="2036c-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="2036c-125">O arquivo em lote pode ser executado em dois modos.</span><span class="sxs-lookup"><span data-stu-id="2036c-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="2036c-126">Para executar o arquivo em lote no `setup.bat` modo de computador único, digite na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2036c-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="2036c-127">Para executá-lo `setup.bat service`no tipo de modo de serviço .</span><span class="sxs-lookup"><span data-stu-id="2036c-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="2036c-128">Você usa este modo ao executar a amostra em computadores.</span><span class="sxs-lookup"><span data-stu-id="2036c-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="2036c-129">Consulte o procedimento de configuração no final deste tópico para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="2036c-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="2036c-130">O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote.</span><span class="sxs-lookup"><span data-stu-id="2036c-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="2036c-131">Criando o certificado do servidor</span><span class="sxs-lookup"><span data-stu-id="2036c-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="2036c-132">As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2036c-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="2036c-133">A variável %SERVER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="2036c-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2036c-134">O certificado é armazenado na loja LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2036c-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="2036c-135">Se o arquivo de lote Setup.bat for executado `setup.bat service`com um argumento de serviço (como ) o %SERVER_NAME% contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="2036c-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="2036c-136">Caso contrário, ele é padrão para host local.</span><span class="sxs-lookup"><span data-stu-id="2036c-136">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="2036c-137">Instalando o certificado do servidor na loja de certificados confiáveis do cliente</span><span class="sxs-lookup"><span data-stu-id="2036c-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="2036c-138">A linha a seguir copia o certificado do servidor na loja de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2036c-139">Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2036c-140">Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="2036c-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="2036c-141">Concessão de permissões na chave privada do certificado</span><span class="sxs-lookup"><span data-stu-id="2036c-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="2036c-142">As seguintes linhas no arquivo setup.bat batch tornam o certificado de servidor armazenado na loja LocalMachine acessível à conta do processo do trabalhador ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2036c-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
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
    > <span data-ttu-id="2036c-143">Se você estiver usando uma edição não-americana em inglês do Windows, você `NT AUTHORITY\NETWORK SERVICE` deve editar o arquivo Setup.bat e substituir o nome da conta pelo seu equivalente regional.</span><span class="sxs-lookup"><span data-stu-id="2036c-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2036c-144">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2036c-144">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2036c-145">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2036c-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2036c-146">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2036c-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2036c-147">Para executar a amostra no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="2036c-147">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="2036c-148">Certifique-se de que o caminho inclui a pasta onde o Makecert.exe e o FindPrivateKey.exe estão localizados.</span><span class="sxs-lookup"><span data-stu-id="2036c-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2. <span data-ttu-id="2036c-149">Executar setup.bat da pasta de instalação de amostra em um Prompt de comando do desenvolvedor para o Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="2036c-149">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="2036c-150">Isso instala todos os certificados necessários para a execução da amostra.</span><span class="sxs-lookup"><span data-stu-id="2036c-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2036c-151">O arquivo de lote Setup.bat foi projetado para ser executado a partir de um prompt de comando do desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2036c-151">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="2036c-152">Requer que a variável ambiente de caminho aponte para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="2036c-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="2036c-153">Essa variável de ambiente é definida automaticamente dentro de um Prompt de comando do desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2036c-153">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="2036c-154">Verifique o acesso ao serviço usando `http://localhost/servicemodelsamples/service.svc`um navegador inserindo o endereço .</span><span class="sxs-lookup"><span data-stu-id="2036c-154">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>
  
4. <span data-ttu-id="2036c-155">Inicie client.exe a partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="2036c-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="2036c-156">A atividade do cliente é exibida no aplicativo do console cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-156">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="2036c-157">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2036c-157">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2036c-158">Para executar a amostra através de computadores</span><span class="sxs-lookup"><span data-stu-id="2036c-158">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="2036c-159">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2036c-159">Create a directory on the service computer.</span></span> <span data-ttu-id="2036c-160">Crie um aplicativo virtual chamado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de Serviços de Informação da Internet.</span><span class="sxs-lookup"><span data-stu-id="2036c-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2. <span data-ttu-id="2036c-161">Copie os arquivos do programa de serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2036c-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="2036c-162">Certifique-se de copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="2036c-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="2036c-163">Copie também os arquivos Setup.bat e Cleanup.bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2036c-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="2036c-164">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="2036c-165">Copie os arquivos do programa cliente para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="2036c-166">Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="2036c-167">No servidor, `setup.bat service` execute em um Prompt de comando de desenvolvedor para o Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="2036c-167">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="2036c-168">A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="2036c-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="2036c-169">Editar Web.config para refletir o novo nome do certificado (no atributo findValue no elemento serviceCertificate) que é o mesmo que o nome de domínio totalmente qualificado do computador`.`</span><span class="sxs-lookup"><span data-stu-id="2036c-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7. <span data-ttu-id="2036c-170">Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="2036c-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="2036c-171">No arquivo Client.exe.config no computador do cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="2036c-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="2036c-172">No cliente, execute ImportServiceCert.bat em um Prompt de comando de desenvolvedor para o Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="2036c-172">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="2036c-173">Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="2036c-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="2036c-174">No computador do cliente, inicie client.exe a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2036c-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="2036c-175">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2036c-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2036c-176">Para limpar depois da amostra</span><span class="sxs-lookup"><span data-stu-id="2036c-176">To clean up after the sample</span></span>  
  
- <span data-ttu-id="2036c-177">Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="2036c-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2036c-178">Este script não remove certificados de serviço em um cliente ao executar essa amostra em computadores.</span><span class="sxs-lookup"><span data-stu-id="2036c-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="2036c-179">Se você tiver executado amostras de WCF (Windows Communication Foundation, fundação de comunicação do Windows) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="2036c-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="2036c-180">Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` seguinte comando: Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="2036c-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
