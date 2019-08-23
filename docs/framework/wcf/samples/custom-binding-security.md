---
title: Segurança de associação personalizada
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: 99fa1e7dea09601de5efff9ef8d8c6a66eae1bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953771"
---
# <a name="custom-binding-security"></a><span data-ttu-id="aa525-102">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="aa525-102">Custom Binding Security</span></span>
<span data-ttu-id="aa525-103">Este exemplo demonstra como configurar a segurança usando uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="aa525-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="aa525-104">Ele mostra como usar uma associação personalizada para habilitar a segurança em nível de mensagem com um transporte seguro.</span><span class="sxs-lookup"><span data-stu-id="aa525-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="aa525-105">Isso é útil quando um transporte seguro é necessário para transmitir as mensagens entre o cliente e o serviço e simultaneamente as mensagens devem ser seguras no nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="aa525-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="aa525-106">Não há suporte para essa configuração por associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="aa525-106">This configuration is not supported by system-provided bindings.</span></span>

 <span data-ttu-id="aa525-107">Este exemplo consiste em um programa de console do cliente (EXE) e um programa de console do serviço (EXE).</span><span class="sxs-lookup"><span data-stu-id="aa525-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="aa525-108">O serviço implementa um contrato duplex.</span><span class="sxs-lookup"><span data-stu-id="aa525-108">The service implements a duplex contract.</span></span> <span data-ttu-id="aa525-109">O contrato é definido pela `ICalculatorDuplex` interface, que expõe operações matemáticas (adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="aa525-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="aa525-110">A `ICalculatorDuplex` interface permite que o cliente execute operações matemáticas, calculando um resultado em execução em uma sessão.</span><span class="sxs-lookup"><span data-stu-id="aa525-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="aa525-111">Independentemente, o serviço pode retornar resultados na `ICalculatorDuplexCallback` interface.</span><span class="sxs-lookup"><span data-stu-id="aa525-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="aa525-112">Um contrato duplex requer uma sessão, porque um contexto deve ser estabelecido para correlacionar o conjunto de mensagens que estão sendo enviadas entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="aa525-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="aa525-113">Uma associação personalizada é definida com suporte à comunicação duplex e é segura.</span><span class="sxs-lookup"><span data-stu-id="aa525-113">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
> <span data-ttu-id="aa525-114">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="aa525-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="aa525-115">A configuração de serviço define uma associação personalizada que dá suporte ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="aa525-115">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="aa525-116">Comunicação TCP protegida usando o protocolo TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="aa525-116">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="aa525-117">Segurança de mensagem do Windows.</span><span class="sxs-lookup"><span data-stu-id="aa525-117">Windows message security.</span></span>

 <span data-ttu-id="aa525-118">A configuração de associação personalizada permite o transporte seguro habilitando simultaneamente a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="aa525-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="aa525-119">A ordenação de elementos de associação é importante na definição de uma associação personalizada, pois cada uma representa uma camada na pilha de canais (consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="aa525-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="aa525-120">A associação personalizada é definida nos arquivos de configuração do serviço e do cliente, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="aa525-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

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

 <span data-ttu-id="aa525-121">A associação personalizada usa um certificado de serviço para autenticar o serviço no nível de transporte e para proteger as mensagens durante a transmissão entre o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="aa525-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="aa525-122">Isso é feito pelo `sslStreamSecurity` elemento Binding.</span><span class="sxs-lookup"><span data-stu-id="aa525-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="aa525-123">O certificado do serviço é configurado usando um comportamento de serviço, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="aa525-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

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

 <span data-ttu-id="aa525-124">Além disso, a associação personalizada usa segurança de mensagem com o tipo de credencial do Windows – esse é o tipo de credencial padrão.</span><span class="sxs-lookup"><span data-stu-id="aa525-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="aa525-125">Isso é feito pelo `security` elemento Binding.</span><span class="sxs-lookup"><span data-stu-id="aa525-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="aa525-126">O cliente e o serviço são autenticados usando a segurança no nível da mensagem se o mecanismo de autenticação Kerberos estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="aa525-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="aa525-127">Isso ocorrerá se o exemplo for executado no ambiente de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="aa525-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="aa525-128">Se o mecanismo de autenticação Kerberos não estiver disponível, a autenticação NTLM será usada.</span><span class="sxs-lookup"><span data-stu-id="aa525-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="aa525-129">O NTLM autentica o cliente para o serviço, mas não autentica o serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="aa525-130">O `security` elemento Binding é configurado para usar `SecureConversation` `authenticationType`, o que resulta na criação de uma sessão de segurança no cliente e no serviço.</span><span class="sxs-lookup"><span data-stu-id="aa525-130">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="aa525-131">Isso é necessário para permitir que o contrato duplex do serviço funcione.</span><span class="sxs-lookup"><span data-stu-id="aa525-131">This is required to enable the service's duplex contract to work.</span></span>

 <span data-ttu-id="aa525-132">Quando você executa o exemplo, as solicitações e respostas da operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="aa525-133">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-133">Press ENTER in the client window to shut down the client.</span></span>

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 <span data-ttu-id="aa525-134">Ao executar o exemplo, você verá as mensagens retornadas para o cliente na interface de retorno de chamada enviadas do serviço.</span><span class="sxs-lookup"><span data-stu-id="aa525-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="aa525-135">Cada resultado intermediário é exibido, seguido de toda a equação após a conclusão de todas as operações.</span><span class="sxs-lookup"><span data-stu-id="aa525-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="aa525-136">Pressione ENTER para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-136">Press ENTER to shut down the client.</span></span>

 <span data-ttu-id="aa525-137">O arquivo setup. bat incluído permite que você configure o cliente e o servidor com o certificado de serviço relevante para executar um aplicativo hospedado que requer segurança baseada em certificado.</span><span class="sxs-lookup"><span data-stu-id="aa525-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="aa525-138">Esse arquivo em lotes deve ser modificado para funcionar em computadores ou para funcionar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="aa525-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="aa525-139">Veja a seguir uma breve visão geral das diferentes seções dos arquivos em lotes que se aplicam a esse exemplo para que eles possam ser modificados para serem executados na configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="aa525-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="aa525-140">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="aa525-140">Creating the server certificate.</span></span>

     <span data-ttu-id="aa525-141">As linhas a seguir do arquivo setup. bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="aa525-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="aa525-142">A `%SERVER_NAME%` variável especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="aa525-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="aa525-143">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="aa525-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="aa525-144">Esse arquivo em lotes padroniza o nome do servidor para localhost.</span><span class="sxs-lookup"><span data-stu-id="aa525-144">This batch file defaults the server name to localhost.</span></span>

     <span data-ttu-id="aa525-145">O certificado é armazenado no armazenamento CurrentUser para os serviços hospedados na Web.</span><span class="sxs-lookup"><span data-stu-id="aa525-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="aa525-146">Instalar o certificado do servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-146">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="aa525-147">As linhas a seguir no arquivo setup. bat copiam o certificado do servidor no repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="aa525-148">Essa etapa é necessária porque os certificados gerados pelo MakeCert. exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="aa525-149">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="aa525-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="aa525-150">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando do Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="aa525-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="aa525-151">Ele requer que a variável de ambiente MSSDK aponte para o diretório em que o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="aa525-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="aa525-152">Essa variável de ambiente é definida automaticamente em um prompt de comando do Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="aa525-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa525-153">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="aa525-153">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="aa525-154">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa525-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="aa525-155">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa525-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="aa525-156">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aa525-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="aa525-157">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="aa525-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="aa525-158">Abra um Prompt de Comando do Desenvolvedor para a janela do Visual Studio com privilégios de administrador e execute Setup. bat na pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="aa525-158">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="aa525-159">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="aa525-159">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="aa525-160">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="aa525-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="aa525-161">A variável de ambiente PATH definida no prompt de comando do Visual Studio 2012 aponta para o diretório que contém os executáveis exigidos pelo script setup. bat.</span><span class="sxs-lookup"><span data-stu-id="aa525-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="aa525-162">Inicie o Service. exe em \service\bin.</span><span class="sxs-lookup"><span data-stu-id="aa525-162">Launch Service.exe from \service\bin.</span></span>  
  
3. <span data-ttu-id="aa525-163">Inicie o Client.exe no \client\bin.</span><span class="sxs-lookup"><span data-stu-id="aa525-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="aa525-164">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-164">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="aa525-165">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="aa525-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="aa525-166">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="aa525-166">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="aa525-167">No computador do serviço:</span><span class="sxs-lookup"><span data-stu-id="aa525-167">On the service computer:</span></span>  
  
    1. <span data-ttu-id="aa525-168">Crie um diretório virtual chamado servicemodelsamples no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="aa525-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2. <span data-ttu-id="aa525-169">Copie os arquivos de programa do serviço do \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="aa525-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="aa525-170">Certifique-se de copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="aa525-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3. <span data-ttu-id="aa525-171">Copie os arquivos Setup. bat e Cleanup. bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="aa525-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4. <span data-ttu-id="aa525-172">Execute o seguinte comando em um Prompt de Comando do Desenvolvedor para Visual Studio aberto com privilégios de administrador `Setup.bat service`:.</span><span class="sxs-lookup"><span data-stu-id="aa525-172">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="aa525-173">Isso cria o certificado de serviço com o nome da entidade correspondente ao nome do computador em que o arquivo em lotes foi executado.</span><span class="sxs-lookup"><span data-stu-id="aa525-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="aa525-174">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando do Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="aa525-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="aa525-175">Ele requer que a variável de ambiente Path aponte para o diretório em que o SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="aa525-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="aa525-176">Essa variável de ambiente é definida automaticamente em um prompt de comando do Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="aa525-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="aa525-177">Altere o [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) de serviço dentro do arquivo Service. exe. config para refletir o nome da entidade do certificado gerado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="aa525-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="aa525-178">Execute o Service. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="aa525-178">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="aa525-179">No computador cliente:</span><span class="sxs-lookup"><span data-stu-id="aa525-179">On the client computer:</span></span>

    1. <span data-ttu-id="aa525-180">Copie os arquivos de programa do cliente da pasta \client\bin\ para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="aa525-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="aa525-181">Copie também o arquivo Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="aa525-181">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="aa525-182">Execute Cleanup. bat para remover quaisquer certificados antigos de exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="aa525-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="aa525-183">Exporte o certificado do serviço abrindo um prompt de comando do desenvolvedor para o Visual Studio com privilégios administrativos e executando o seguinte comando no computador do serviço (substitua `%SERVER_NAME%` pelo nome totalmente qualificado do computador em que o serviço está em execução):</span><span class="sxs-lookup"><span data-stu-id="aa525-183">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="aa525-184">Copie% SERVER_NAME%. cer para o computador cliente (substitua% SERVER_NAME% pelo nome totalmente qualificado do computador em que o serviço está em execução).</span><span class="sxs-lookup"><span data-stu-id="aa525-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="aa525-185">Importe o certificado do serviço abrindo um Prompt de Comando do Desenvolvedor para o Visual Studio com privilégios administrativos e executando o seguinte comando no computador cliente (substitua% SERVER_NAME% pelo nome totalmente qualificado do computador em que o serviço em execução):</span><span class="sxs-lookup"><span data-stu-id="aa525-185">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         <span data-ttu-id="aa525-186">As etapas c, d e e não serão necessárias se o certificado for emitido por um emissor confiável.</span><span class="sxs-lookup"><span data-stu-id="aa525-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="aa525-187">Modifique o arquivo app. config do cliente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aa525-187">Modify the client’s App.config file as follows:</span></span>

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

    7. <span data-ttu-id="aa525-188">Se o serviço estiver sendo executado em uma conta diferente da conta NetworkService ou LocalSystem em um ambiente de domínio, talvez seja necessário modificar a identidade do ponto de extremidade para o ponto de extremidade de serviço dentro do arquivo app. config do cliente para definir o UPN ou o SPN apropriado com base na conta que é usada para executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="aa525-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="aa525-189">Para obter mais informações sobre a identidade do ponto de extremidade, consulte o tópico [identidade e autenticação de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) .</span><span class="sxs-lookup"><span data-stu-id="aa525-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="aa525-190">Execute Client. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="aa525-190">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="aa525-191">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="aa525-191">To clean up after the sample</span></span>

- <span data-ttu-id="aa525-192">Execute o Cleanup. bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="aa525-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
