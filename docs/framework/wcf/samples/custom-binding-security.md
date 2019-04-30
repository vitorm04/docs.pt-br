---
title: Segurança de associação personalizada
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: 1ff83d95dae06b787f8bc7ec8e1bf0f45c226532
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943930"
---
# <a name="custom-binding-security"></a><span data-ttu-id="2f518-102">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="2f518-102">Custom Binding Security</span></span>
<span data-ttu-id="2f518-103">Este exemplo demonstra como configurar a segurança por meio de uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2f518-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="2f518-104">Ele mostra como usar uma ligação personalizada para habilitar a segurança em nível de mensagem junto com um transporte seguro.</span><span class="sxs-lookup"><span data-stu-id="2f518-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="2f518-105">Isso é útil quando um transporte seguro é necessária para transmitir as mensagens entre o cliente e o serviço e ao mesmo tempo as mensagens devem ser seguras no nível da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2f518-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="2f518-106">Essa configuração não é suportada por associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="2f518-106">This configuration is not supported by system-provided bindings.</span></span>

 <span data-ttu-id="2f518-107">Esse exemplo consiste em um programa de console de cliente (EXE) e um programa de console de serviço (EXE).</span><span class="sxs-lookup"><span data-stu-id="2f518-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="2f518-108">O serviço implementa um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="2f518-108">The service implements a duplex contract.</span></span> <span data-ttu-id="2f518-109">O contrato é definido o `ICalculatorDuplex` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="2f518-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="2f518-110">O `ICalculatorDuplex` interface permite que o cliente a executar operações matemáticas, calculando um resultado em execução em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="2f518-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="2f518-111">De forma independente, o serviço pode retornar resultados no `ICalculatorDuplexCallback` interface.</span><span class="sxs-lookup"><span data-stu-id="2f518-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="2f518-112">Um contrato duplex requer uma sessão, porque um contexto deve ser estabelecido para correlacionar o conjunto de mensagens sendo enviadas entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="2f518-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="2f518-113">Uma associação personalizada é definida que dá suporte à comunicação duplex e é seguro.</span><span class="sxs-lookup"><span data-stu-id="2f518-113">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
>  <span data-ttu-id="2f518-114">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2f518-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="2f518-115">A configuração de serviço define uma associação personalizada que dá suporte ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f518-115">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="2f518-116">Comunicação TCP protegida usando o protocolo TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="2f518-116">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="2f518-117">Segurança de mensagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="2f518-117">Windows message security.</span></span>

 <span data-ttu-id="2f518-118">A configuração de associação personalizado permite que o transporte seguro, permitindo simultaneamente a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2f518-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="2f518-119">A ordenação dos elementos de associação é importante definir uma ligação personalizada, porque cada um representa uma camada da pilha de canal (consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="2f518-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="2f518-120">A associação personalizada é definida nos arquivos de configuração de cliente e o serviço, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2f518-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

 <span data-ttu-id="2f518-121">A associação personalizada usa um certificado de serviço para autenticar o serviço no nível de transporte e proteger as mensagens durante a transmissão entre cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="2f518-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="2f518-122">Isso é feito usando o `sslStreamSecurity` elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="2f518-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="2f518-123">O certificado do serviço é configurado usando um comportamento de serviço, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2f518-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="2f518-124">Além disso, a associação personalizada usa segurança de mensagem com o tipo de credencial do Windows - esse é o tipo de credencial padrão.</span><span class="sxs-lookup"><span data-stu-id="2f518-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="2f518-125">Isso é feito usando o `security` elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="2f518-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="2f518-126">Cliente e o serviço são autenticados usando a segurança de nível de mensagem se o mecanismo de autenticação Kerberos está disponível.</span><span class="sxs-lookup"><span data-stu-id="2f518-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="2f518-127">Isso ocorre se a amostra for executada no ambiente do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2f518-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="2f518-128">Se o mecanismo de autenticação Kerberos não estiver disponível, a autenticação NTLM é usada.</span><span class="sxs-lookup"><span data-stu-id="2f518-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="2f518-129">NTLM autentica o cliente para o serviço, mas não autentica o serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="2f518-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="2f518-130">O `security` elemento de associação está configurado para usar `SecureConversation` `authenticationType`, que resulta na criação de uma sessão de segurança no cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="2f518-130">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="2f518-131">Isso é necessário para habilitar o contrato do serviço duplex trabalhar.</span><span class="sxs-lookup"><span data-stu-id="2f518-131">This is required to enable the service's duplex contract to work.</span></span>

 <span data-ttu-id="2f518-132">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2f518-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="2f518-133">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2f518-133">Press ENTER in the client window to shut down the client.</span></span>

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 <span data-ttu-id="2f518-134">Quando você executar o exemplo, você ver as mensagens retornadas ao cliente sobre a interface de retorno de chamada enviada do serviço.</span><span class="sxs-lookup"><span data-stu-id="2f518-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="2f518-135">Cada resultado intermediário é exibido, seguido por toda a equação após a conclusão de todas as operações.</span><span class="sxs-lookup"><span data-stu-id="2f518-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="2f518-136">Pressione ENTER para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2f518-136">Press ENTER to shut down the client.</span></span>

 <span data-ttu-id="2f518-137">O arquivo Setup. bat incluído permite que você configure o cliente e servidor com o certificado de serviço relevante para executar um aplicativo hospedado que exige a segurança baseada em certificado.</span><span class="sxs-lookup"><span data-stu-id="2f518-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="2f518-138">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso de não hospedados.</span><span class="sxs-lookup"><span data-stu-id="2f518-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="2f518-139">O exemplo a seguir fornece uma visão geral das diferentes seções dos arquivos de lote que se aplicam a este exemplo, para que eles podem ser modificados para executar a configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="2f518-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="2f518-140">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="2f518-140">Creating the server certificate.</span></span>

     <span data-ttu-id="2f518-141">As seguintes linhas do arquivo Setup. bat de criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2f518-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="2f518-142">O `%SERVER_NAME%` variável Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="2f518-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="2f518-143">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="2f518-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="2f518-144">Esse arquivo em lotes padrão é o nome do servidor ao localhost.</span><span class="sxs-lookup"><span data-stu-id="2f518-144">This batch file defaults the server name to localhost.</span></span>

     <span data-ttu-id="2f518-145">O certificado é armazenado no repositório CurrentUser para os serviços hospedados na Web.</span><span class="sxs-lookup"><span data-stu-id="2f518-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="2f518-146">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="2f518-146">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="2f518-147">As seguintes linhas na cópia do arquivo Setup. bat o certificado do servidor as pessoas confiáveis do cliente ao repositório.</span><span class="sxs-lookup"><span data-stu-id="2f518-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2f518-148">Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="2f518-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2f518-149">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="2f518-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="2f518-150">O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2010 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f518-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="2f518-151">Ele requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="2f518-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="2f518-152">Essa variável de ambiente é definido automaticamente dentro de um Visual Studio 2010 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f518-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2f518-153">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2f518-153">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2f518-154">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f518-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="2f518-155">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f518-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="2f518-156">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f518-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2f518-157">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="2f518-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="2f518-158">Abra um Prompt de comando do desenvolvedor para a janela do Visual Studio com privilégios de administrador e execute Setup. bat da pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="2f518-158">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="2f518-159">Essa opção instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2f518-159">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2f518-160">O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2012 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f518-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="2f518-161">A variável de ambiente PATH definido dentro de pontos de Prompt de comando do Visual Studio 2012 para o diretório que contém executáveis exigido pelo script de Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="2f518-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="2f518-162">Inicie o Service.exe no \service\bin.</span><span class="sxs-lookup"><span data-stu-id="2f518-162">Launch Service.exe from \service\bin.</span></span>  
  
3. <span data-ttu-id="2f518-163">Inicie o Client.exe no \client\bin.</span><span class="sxs-lookup"><span data-stu-id="2f518-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="2f518-164">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2f518-164">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="2f518-165">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2f518-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2f518-166">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="2f518-166">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="2f518-167">No computador do serviço:</span><span class="sxs-lookup"><span data-stu-id="2f518-167">On the service computer:</span></span>  
  
    1. <span data-ttu-id="2f518-168">Crie um diretório virtual chamado servicemodelsamples no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="2f518-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2. <span data-ttu-id="2f518-169">Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="2f518-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="2f518-170">Certifique-se de que você copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="2f518-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3. <span data-ttu-id="2f518-171">Copie os arquivos Setup. bat e Cleanup no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2f518-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4. <span data-ttu-id="2f518-172">Execute o seguinte comando em um Prompt de comando do desenvolvedor para Visual Studio é aberto com privilégios de administrador: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="2f518-172">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="2f518-173">Isso cria o certificado de serviço com o nome da entidade que corresponde ao nome do computador em que o arquivo em lotes foi executado em.</span><span class="sxs-lookup"><span data-stu-id="2f518-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2f518-174">O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2010 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f518-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="2f518-175">Ele requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="2f518-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="2f518-176">Essa variável de ambiente é definido automaticamente dentro de um Visual Studio 2010 Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f518-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="2f518-177">Alterar o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) dentro do arquivo Service.exe.config para refletir o nome da entidade do certificado gerado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="2f518-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="2f518-178">Execute Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f518-178">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="2f518-179">No computador cliente:</span><span class="sxs-lookup"><span data-stu-id="2f518-179">On the client computer:</span></span>

    1. <span data-ttu-id="2f518-180">Copie os arquivos de programa do cliente da pasta \client\bin\ no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="2f518-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="2f518-181">Copie também o arquivo de CleanUp.</span><span class="sxs-lookup"><span data-stu-id="2f518-181">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="2f518-182">Execute CleanUp para remover todos os certificados antigos de amostras anteriores.</span><span class="sxs-lookup"><span data-stu-id="2f518-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="2f518-183">Exportar o certificado do serviço abrindo um Prompt de comando do desenvolvedor para Visual Studio com privilégios administrativos e executando o seguinte comando no computador do serviço (substitua `%SERVER_NAME%` com o nome totalmente qualificado do computador em que o serviço está em execução):</span><span class="sxs-lookup"><span data-stu-id="2f518-183">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="2f518-184">Copie %SERVER_NAME%.cer para o computador cliente (substitua % SERVER_NAME % com o nome totalmente qualificado do computador onde o serviço está em execução).</span><span class="sxs-lookup"><span data-stu-id="2f518-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="2f518-185">Importar o certificado do serviço abrindo um Prompt de comando do desenvolvedor para Visual Studio com privilégios administrativos e executando o seguinte comando no computador cliente (substitua % SERVER_NAME % com o nome totalmente qualificado do computador em que o serviço está em execução):</span><span class="sxs-lookup"><span data-stu-id="2f518-185">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         <span data-ttu-id="2f518-186">Etapas de c, d e e não são necessárias se o certificado é emitido por um emissor confiável.</span><span class="sxs-lookup"><span data-stu-id="2f518-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="2f518-187">Modifique o arquivo do cliente App. config da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2f518-187">Modify the client’s App.config file as follows:</span></span>

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
        behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7. <span data-ttu-id="2f518-188">Se o serviço for executado sob uma conta que não seja o NetworkService ou LocalSystem em um ambiente de domínio, você talvez precise modificar a identidade do ponto de extremidade para o ponto de extremidade de serviço dentro do arquivo de App. config do cliente para definir o UPN ou o SPN com base em apropriado na conta que é usado para executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="2f518-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="2f518-189">Para obter mais informações sobre a identidade do ponto de extremidade, consulte a [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="2f518-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="2f518-190">Execute Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2f518-190">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2f518-191">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="2f518-191">To clean up after the sample</span></span>

- <span data-ttu-id="2f518-192">Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="2f518-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
