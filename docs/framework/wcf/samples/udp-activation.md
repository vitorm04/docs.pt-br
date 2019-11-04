---
title: Ativação de UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 6e8d2f4428e85c71571021e2735f90e2e0a9d35a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424182"
---
# <a name="udp-activation"></a><span data-ttu-id="366cd-102">Ativação de UDP</span><span class="sxs-lookup"><span data-stu-id="366cd-102">UDP Activation</span></span>
<span data-ttu-id="366cd-103">Este exemplo é baseado na amostra [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="366cd-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="366cd-104">Ele estende a amostra [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) para dar suporte à ativação do processo usando o WAS (serviço de ativação de processos do Windows).</span><span class="sxs-lookup"><span data-stu-id="366cd-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="366cd-105">O exemplo consiste em três partes principais:</span><span class="sxs-lookup"><span data-stu-id="366cd-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="366cd-106">Um UDP Protocol Activator, um processo autônomo que recebe mensagens UDP em nome dos aplicativos que devem ser ativados.</span><span class="sxs-lookup"><span data-stu-id="366cd-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="366cd-107">Um cliente que usa o transporte personalizado UDP para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="366cd-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="366cd-108">Um serviço (hospedado em um processo de trabalho ativado pelo WAS) que recebe mensagens sobre o transporte personalizado UDP.</span><span class="sxs-lookup"><span data-stu-id="366cd-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="366cd-109">Ativador de protocolo UDP</span><span class="sxs-lookup"><span data-stu-id="366cd-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="366cd-110">O UDP Protocol Activator é uma ponte entre o cliente WCF e o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="366cd-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="366cd-111">Ele fornece comunicação de dados por meio do protocolo UDP na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="366cd-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="366cd-112">Ele tem duas funções principais:</span><span class="sxs-lookup"><span data-stu-id="366cd-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="366cd-113">ERA o adaptador de escuta (LA), que colabora com o WAS para ativar processos em resposta a mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="366cd-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="366cd-114">Ouvinte de protocolo UDP, que aceita mensagens UDP em nome dos aplicativos que devem ser ativados.</span><span class="sxs-lookup"><span data-stu-id="366cd-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="366cd-115">O ativador deve estar sendo executado como um programa autônomo no computador do servidor.</span><span class="sxs-lookup"><span data-stu-id="366cd-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="366cd-116">Normalmente, os adaptadores de escuta eram (como o NetTcpActivator e o NetPipeActivator) são implementados em serviços do Windows de longa execução.</span><span class="sxs-lookup"><span data-stu-id="366cd-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="366cd-117">No entanto, para simplificar e clareza, este exemplo implementa o ativador de protocolo como um aplicativo autônomo.</span><span class="sxs-lookup"><span data-stu-id="366cd-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="366cd-118">FOI o adaptador de escuta</span><span class="sxs-lookup"><span data-stu-id="366cd-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="366cd-119">O adaptador de escuta WAS para UDP é implementado na classe `UdpListenerAdapter`.</span><span class="sxs-lookup"><span data-stu-id="366cd-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="366cd-120">É o módulo que interage com o WAS para executar a ativação do aplicativo para o protocolo UDP.</span><span class="sxs-lookup"><span data-stu-id="366cd-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="366cd-121">Isso é feito chamando as seguintes APIs Webhost:</span><span class="sxs-lookup"><span data-stu-id="366cd-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="366cd-122">Depois de chamar inicialmente `WebhostRegisterProtocol`, o adaptador de escuta recebe o `ApplicationCreated` de retorno de chamada do WAS para todos os aplicativos registrados em applicationHost. config (localizado em%windir%\system32\inetsrv.).</span><span class="sxs-lookup"><span data-stu-id="366cd-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="366cd-123">Neste exemplo, tratamos apenas dos aplicativos com o protocolo UDP (com a ID de protocolo como "net. UDP") habilitado.</span><span class="sxs-lookup"><span data-stu-id="366cd-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="366cd-124">Outras implementações podem lidar com isso de forma diferente se essas implementações responderem às alterações de configuração dinâmicas para o aplicativo (por exemplo, uma transição de aplicativo de desabilitado para habilitado).</span><span class="sxs-lookup"><span data-stu-id="366cd-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="366cd-125">Quando o `ConfigManagerInitializationCompleted` de retorno de chamada é recebido, ele indica que o foi concluído todas as notificações para a inicialização do protocolo.</span><span class="sxs-lookup"><span data-stu-id="366cd-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="366cd-126">Neste momento, o adaptador do ouvinte está pronto para processar solicitações de ativação.</span><span class="sxs-lookup"><span data-stu-id="366cd-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="366cd-127">Quando uma nova solicitação chega na primeira vez para um aplicativo, o adaptador de escuta chama `WebhostOpenListenerChannelInstance` no WAS, o que inicia o processo de trabalho se ele ainda não foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="366cd-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="366cd-128">Em seguida, os manipuladores de protocolo são carregados e a comunicação entre o adaptador de escuta e o aplicativo virtual pode ser iniciada.</span><span class="sxs-lookup"><span data-stu-id="366cd-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="366cd-129">O adaptador de escuta é registrado no%SystemRoot%\System32\inetsrv\ApplicationHost.config na seção <`listenerAdapters`> da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="366cd-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="366cd-130">Ouvinte de protocolo</span><span class="sxs-lookup"><span data-stu-id="366cd-130">Protocol Listener</span></span>  
 <span data-ttu-id="366cd-131">O ouvinte de protocolo UDP é um módulo dentro do ativador de protocolo que escuta em um ponto de extremidade UDP em nome do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="366cd-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="366cd-132">Ele é implementado na classe `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="366cd-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="366cd-133">O ponto de extremidade é representado como `IPEndpoint` para o qual o número da porta é extraído da associação do protocolo para o site.</span><span class="sxs-lookup"><span data-stu-id="366cd-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="366cd-134">Serviço de controle</span><span class="sxs-lookup"><span data-stu-id="366cd-134">Control Service</span></span>  
 <span data-ttu-id="366cd-135">Neste exemplo, usamos o WCF para se comunicar entre o ativador e o WAS processo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="366cd-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="366cd-136">O serviço que reside no ativador é chamado de serviço de controle.</span><span class="sxs-lookup"><span data-stu-id="366cd-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="366cd-137">Manipuladores de protocolo</span><span class="sxs-lookup"><span data-stu-id="366cd-137">Protocol Handlers</span></span>  
 <span data-ttu-id="366cd-138">Depois que o adaptador do ouvinte chamar `WebhostOpenListenerChannelInstance`, o Gerenciador de processos do WAS iniciará o processo de trabalho se ele não for iniciado.</span><span class="sxs-lookup"><span data-stu-id="366cd-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="366cd-139">O Gerenciador de aplicativos dentro do processo de trabalho então carrega o PPH (manipulador de protocolo de processo) do UDP com a solicitação para essa `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="366cd-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="366cd-140">O PPH em ativa chamadas `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="366cd-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="366cd-141">para iniciar o manipulador de protocolo de AppDomain de UDP (ADPH).</span><span class="sxs-lookup"><span data-stu-id="366cd-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="366cd-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="366cd-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="366cd-143">As informações são registradas no Web. config da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="366cd-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="366cd-144">Configuração especial para este exemplo</span><span class="sxs-lookup"><span data-stu-id="366cd-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="366cd-145">Este exemplo só pode ser criado e executado no Windows Vista, no Windows Server 2008 ou no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="366cd-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="366cd-146">Para executar o exemplo, você deve primeiro obter todos os componentes configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="366cd-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="366cd-147">Use as etapas a seguir para instalar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="366cd-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="366cd-148">Para configurar este exemplo</span><span class="sxs-lookup"><span data-stu-id="366cd-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="366cd-149">Instale o ASP.NET 4,0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="366cd-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="366cd-150">Compile o projeto no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="366cd-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="366cd-151">Após a compilação, ele também executa as seguintes operações na fase pós-compilação:</span><span class="sxs-lookup"><span data-stu-id="366cd-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="366cd-152">Instala a associação UDP ao site "Default Web site".</span><span class="sxs-lookup"><span data-stu-id="366cd-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="366cd-153">Cria o aplicativo virtual "ServiceModelSamples" para apontar para o caminho físico: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="366cd-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="366cd-154">Ele também habilita o protocolo "net. UDP" para este aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="366cd-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="366cd-155">Inicie o aplicativo de interface do usuário "WasNetActivator. exe".</span><span class="sxs-lookup"><span data-stu-id="366cd-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="366cd-156">Clique na guia **instalação** , marque as seguintes caixas de seleção e clique em **instalar** para instalá-las:</span><span class="sxs-lookup"><span data-stu-id="366cd-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="366cd-157">Adaptador de escuta UDP</span><span class="sxs-lookup"><span data-stu-id="366cd-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="366cd-158">Manipuladores de protocolo UDP</span><span class="sxs-lookup"><span data-stu-id="366cd-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="366cd-159">Clique na guia **ativação** do aplicativo de interface do usuário "WasNetActivator. exe".</span><span class="sxs-lookup"><span data-stu-id="366cd-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="366cd-160">Clique no botão **Iniciar** para iniciar o adaptador do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="366cd-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="366cd-161">Agora você está pronto para executar o programa.</span><span class="sxs-lookup"><span data-stu-id="366cd-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="366cd-162">Ao concluir este exemplo, você deve executar o Cleanup. bat para remover a associação net. UDP do "site padrão".</span><span class="sxs-lookup"><span data-stu-id="366cd-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="366cd-163">Uso de exemplo</span><span class="sxs-lookup"><span data-stu-id="366cd-163">Sample Usage</span></span>  
 <span data-ttu-id="366cd-164">Após a compilação, há quatro binários diferentes gerados:</span><span class="sxs-lookup"><span data-stu-id="366cd-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="366cd-165">Client. exe: o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="366cd-165">Client.exe: The client code.</span></span> <span data-ttu-id="366cd-166">O app. config é compilado no arquivo de configuração do cliente Client. exe. config.</span><span class="sxs-lookup"><span data-stu-id="366cd-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="366cd-167">UDPActivation. dll: a biblioteca que contém todas as principais implementações de UDP.</span><span class="sxs-lookup"><span data-stu-id="366cd-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="366cd-168">Service. dll: o código do serviço.</span><span class="sxs-lookup"><span data-stu-id="366cd-168">Service.dll: The service code.</span></span> <span data-ttu-id="366cd-169">Isso é copiado para o diretório \bin do aplicativo virtual ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="366cd-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="366cd-170">O arquivo de serviço é Service. svc e o arquivo de configuração é Web. config. Após a compilação, eles são copiados para o seguinte local:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="366cd-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="366cd-171">WasNetActivator: o programa UDP Activator.</span><span class="sxs-lookup"><span data-stu-id="366cd-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="366cd-172">Verifique se todas as partes necessárias estão instaladas corretamente.</span><span class="sxs-lookup"><span data-stu-id="366cd-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="366cd-173">As etapas a seguir mostram como executar o exemplo:</span><span class="sxs-lookup"><span data-stu-id="366cd-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="366cd-174">Verifique se os seguintes serviços do Windows foram iniciados:</span><span class="sxs-lookup"><span data-stu-id="366cd-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="366cd-175">WAS (serviço de ativação de processos do Windows).</span><span class="sxs-lookup"><span data-stu-id="366cd-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="366cd-176">Serviços de Informações da Internet (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="366cd-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="366cd-177">Em seguida, inicie o ativador, WasNetActivator. exe.</span><span class="sxs-lookup"><span data-stu-id="366cd-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="366cd-178">Na guia **ativação** , o único protocolo, **UDP**, é selecionado na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="366cd-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="366cd-179">Clique no botão **Iniciar** para iniciar o ativador.</span><span class="sxs-lookup"><span data-stu-id="366cd-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="366cd-180">Depois que o ativador for iniciado, você poderá executar o código do cliente executando o Client. exe em uma janela de comando.</span><span class="sxs-lookup"><span data-stu-id="366cd-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="366cd-181">A seguir está a saída de exemplo:</span><span class="sxs-lookup"><span data-stu-id="366cd-181">The following is the sample output:</span></span>  
  
    ```console  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="366cd-182">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="366cd-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="366cd-183">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="366cd-183">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="366cd-184">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="366cd-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="366cd-185">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="366cd-185">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
