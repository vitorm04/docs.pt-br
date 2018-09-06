---
title: Ativação de UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c64540db555d7cac56dd46c6ffb63ec95ca81f91
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788059"
---
# <a name="udp-activation"></a><span data-ttu-id="763e2-102">Ativação de UDP</span><span class="sxs-lookup"><span data-stu-id="763e2-102">UDP Activation</span></span>
<span data-ttu-id="763e2-103">Este exemplo se baseia a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="763e2-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="763e2-104">Ele estende o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo para dar suporte à ativação de processo usando o serviço de ativação de processos do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="763e2-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="763e2-105">O exemplo consiste em três partes principais:</span><span class="sxs-lookup"><span data-stu-id="763e2-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="763e2-106">Um ativador de protocolo UDP, um processo autônomo que recebe mensagens UDP em nome dos aplicativos que estão para ser ativado.</span><span class="sxs-lookup"><span data-stu-id="763e2-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="763e2-107">Um cliente que usa o transporte UDP personalizado para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="763e2-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="763e2-108">Um serviço (hospedado em um processo de trabalho ativado pelo WAS) que recebe mensagens por meio do transporte UDP personalizado.</span><span class="sxs-lookup"><span data-stu-id="763e2-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="763e2-109">Ativador de protocolo UDP</span><span class="sxs-lookup"><span data-stu-id="763e2-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="763e2-110">O ativador de protocolo UDP é uma ponte entre o cliente do WCF e o serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="763e2-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="763e2-111">Ele fornece a comunicação de dados por meio do protocolo UDP na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="763e2-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="763e2-112">Ele tem duas funções principais:</span><span class="sxs-lookup"><span data-stu-id="763e2-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="763e2-113">ERA o ouvinte do adaptador (LA), que colabora com WAS para ativar os processos em resposta às mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="763e2-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="763e2-114">Ouvinte de protocolo UDP, que aceita mensagens UDP em nome dos aplicativos que estão para ser ativado.</span><span class="sxs-lookup"><span data-stu-id="763e2-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="763e2-115">O ativador deve ser executado como um programa autônomo na máquina do servidor.</span><span class="sxs-lookup"><span data-stu-id="763e2-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="763e2-116">Normalmente, os adaptadores de escuta do WAS (como o NetTcpActivator e o NetPipeActivator) são implementados nos serviços do Windows de longa execução.</span><span class="sxs-lookup"><span data-stu-id="763e2-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="763e2-117">No entanto, para manter a simplicidade e clareza, este exemplo implementa o ativador de protocolo como um aplicativo autônomo.</span><span class="sxs-lookup"><span data-stu-id="763e2-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="763e2-118">FOI o adaptador de escuta</span><span class="sxs-lookup"><span data-stu-id="763e2-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="763e2-119">O adaptador de escuta foi para UDP é implementado de `UdpListenerAdapter` classe.</span><span class="sxs-lookup"><span data-stu-id="763e2-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="763e2-120">É o módulo que interage com o WAS para realizar a ativação de aplicativo para o protocolo UDP.</span><span class="sxs-lookup"><span data-stu-id="763e2-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="763e2-121">Isso é obtido chamando as APIs do Webhost seguintes:</span><span class="sxs-lookup"><span data-stu-id="763e2-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="763e2-122">Depois de chamar inicialmente `WebhostRegisterProtocol`, o adaptador de escuta recebe o retorno de chamada `ApplicationCreated` do WAS para todos os aplicativos registrados no applicationHost. config (localizado em % windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="763e2-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="763e2-123">Neste exemplo, estamos apenas lidar com os aplicativos com o protocolo UDP (com a id de protocolo como "net.udp") habilitados.</span><span class="sxs-lookup"><span data-stu-id="763e2-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="763e2-124">Outras implementações podem manipular essa forma diferente se essas implementações respondem a alterações de configuração dinâmica para o aplicativo (por exemplo, uma transição de aplicativos de desabilitado para habilitado).</span><span class="sxs-lookup"><span data-stu-id="763e2-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="763e2-125">Quando o retorno de chamada `ConfigManagerInitializationCompleted` for recebido, ele indica que o WAS concluiu todas as notificações para a inicialização do protocolo.</span><span class="sxs-lookup"><span data-stu-id="763e2-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="763e2-126">Neste momento, o adaptador de escuta está pronto para processar as solicitações de ativação.</span><span class="sxs-lookup"><span data-stu-id="763e2-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="763e2-127">Quando uma nova solicitação chega na primeira vez para um aplicativo, o adaptador de escuta chama `WebhostOpenListenerChannelInstance` no WAS, que inicia o processo de trabalho se ele ainda não foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="763e2-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="763e2-128">Em seguida, os manipuladores de protocolo são carregados e a comunicação entre o adaptador de escuta e o aplicativo virtual pode iniciar.</span><span class="sxs-lookup"><span data-stu-id="763e2-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="763e2-129">O adaptador de escuta é registrado no %SYSTEMROOT%\system32\inetsrv\ApplicationHost.config. no <`listenerAdapters`> seção da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="763e2-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="763e2-130">Ouvinte de protocolo</span><span class="sxs-lookup"><span data-stu-id="763e2-130">Protocol Listener</span></span>  
 <span data-ttu-id="763e2-131">O ouvinte de protocolo UDP é um módulo dentro o ativador de protocolo que escuta em um ponto de extremidade UDP em nome do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="763e2-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="763e2-132">Ele é implementado na classe `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="763e2-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="763e2-133">O ponto de extremidade é representado como `IPEndpoint` para que o número da porta é extraído da associação do protocolo para o site.</span><span class="sxs-lookup"><span data-stu-id="763e2-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="763e2-134">Serviço de controle</span><span class="sxs-lookup"><span data-stu-id="763e2-134">Control Service</span></span>  
 <span data-ttu-id="763e2-135">Neste exemplo, usamos o WCF para comunicação entre o ativador e o processo de trabalho do WAS.</span><span class="sxs-lookup"><span data-stu-id="763e2-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="763e2-136">O serviço que reside o ativador é chamado o serviço de controle.</span><span class="sxs-lookup"><span data-stu-id="763e2-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="763e2-137">Manipuladores de protocolo</span><span class="sxs-lookup"><span data-stu-id="763e2-137">Protocol Handlers</span></span>  
 <span data-ttu-id="763e2-138">Depois das chamadas de adaptador do ouvinte `WebhostOpenListenerChannelInstance`, o Gerenciador de processo WAS inicia o processo de trabalho se ele não for iniciado.</span><span class="sxs-lookup"><span data-stu-id="763e2-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="763e2-139">O Gerenciador de aplicativos dentro do processo de trabalho, em seguida, carrega o UDP processo protocolo manipulador PPH () com a solicitação para que `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="763e2-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="763e2-140">O PPH em chamadas desativa `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="763e2-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="763e2-141">para iniciar o manipulador de protocolo de AppDomain do UDP (ADPH).</span><span class="sxs-lookup"><span data-stu-id="763e2-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="763e2-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="763e2-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="763e2-143">As informações são registradas no Web. config da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="763e2-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="763e2-144">Instalação especial para este exemplo</span><span class="sxs-lookup"><span data-stu-id="763e2-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="763e2-145">Este exemplo pode ser compilado e executado no Windows Vista, Windows Server 2008 ou Windows 7 somente.</span><span class="sxs-lookup"><span data-stu-id="763e2-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="763e2-146">Para executar o exemplo, você deve primeiro obter todos os componentes configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="763e2-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="763e2-147">Use as etapas a seguir para instalar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="763e2-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="763e2-148">Para configurar este exemplo</span><span class="sxs-lookup"><span data-stu-id="763e2-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="763e2-149">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="763e2-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="763e2-150">Compile o projeto no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="763e2-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="763e2-151">Após a compilação, ele também executa as seguintes operações na fase de pós-compilação:</span><span class="sxs-lookup"><span data-stu-id="763e2-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="763e2-152">Instala a associação de UDP para o site "Site padrão".</span><span class="sxs-lookup"><span data-stu-id="763e2-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="763e2-153">Cria o aplicativo virtual "ServiceModelSamples" para apontar para o caminho físico: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="763e2-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="763e2-154">Ele também habilita o protocolo de "net.udp" para esse aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="763e2-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="763e2-155">Inicie o aplicativo de interface do usuário "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="763e2-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="763e2-156">Clique o **instalação** guia, marque as caixas de seleção a seguir e, em seguida, clique em **instalar** instalá-los:</span><span class="sxs-lookup"><span data-stu-id="763e2-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="763e2-157">Adaptador de escuta UDP</span><span class="sxs-lookup"><span data-stu-id="763e2-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="763e2-158">Manipuladores de protocolo UDP</span><span class="sxs-lookup"><span data-stu-id="763e2-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="763e2-159">Clique o **ativação** guia do aplicativo de interface do usuário "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="763e2-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="763e2-160">Clique o **iniciar** botão para iniciar o adaptador de escuta.</span><span class="sxs-lookup"><span data-stu-id="763e2-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="763e2-161">Agora você está pronto para executar o programa.</span><span class="sxs-lookup"><span data-stu-id="763e2-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="763e2-162">Quando tiver terminado com este exemplo, você deve executar CleanUp para remover a associação de net.udp de "Site da Web padrão".</span><span class="sxs-lookup"><span data-stu-id="763e2-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="763e2-163">Uso de exemplo</span><span class="sxs-lookup"><span data-stu-id="763e2-163">Sample Usage</span></span>  
 <span data-ttu-id="763e2-164">Após a compilação, há quatro binários diferentes gerados:</span><span class="sxs-lookup"><span data-stu-id="763e2-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="763e2-165">Client.exe: O código do cliente.</span><span class="sxs-lookup"><span data-stu-id="763e2-165">Client.exe: The client code.</span></span> <span data-ttu-id="763e2-166">O App. config é compilado para o arquivo de configuração de cliente Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="763e2-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="763e2-167">UDPActivation.dll: a biblioteca que contém todas as principais implementações de UDP.</span><span class="sxs-lookup"><span data-stu-id="763e2-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="763e2-168">Service.dll: O código de serviço.</span><span class="sxs-lookup"><span data-stu-id="763e2-168">Service.dll: The service code.</span></span> <span data-ttu-id="763e2-169">Isso é copiado para o diretório \bin do aplicativo virtual ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="763e2-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="763e2-170">O arquivo de serviço é SVC e o arquivo de configuração é Web. config. Após a compilação, eles são copiados no seguinte local: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="763e2-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="763e2-171">WasNetActivator: O UDP activator programa.</span><span class="sxs-lookup"><span data-stu-id="763e2-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="763e2-172">Certifique-se de que todas as partes necessárias estão instaladas corretamente.</span><span class="sxs-lookup"><span data-stu-id="763e2-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="763e2-173">As etapas a seguir mostram como executar o exemplo:</span><span class="sxs-lookup"><span data-stu-id="763e2-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="763e2-174">Certifique-se de que os seguintes serviços do Windows foram iniciados:</span><span class="sxs-lookup"><span data-stu-id="763e2-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="763e2-175">Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="763e2-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="763e2-176">Serviços de informações da Internet (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="763e2-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="763e2-177">Em seguida, inicie o ativador, WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="763e2-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="763e2-178">Sob o **ativação** guia, o único protocolo, **UDP**, está selecionado na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="763e2-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="763e2-179">Clique o **iniciar** botão para iniciar o ativador.</span><span class="sxs-lookup"><span data-stu-id="763e2-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="763e2-180">Depois que o ativador for iniciado, você pode executar o código do cliente, executando Client.exe em uma janela de comando.</span><span class="sxs-lookup"><span data-stu-id="763e2-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="763e2-181">Este é o exemplo de saída:</span><span class="sxs-lookup"><span data-stu-id="763e2-181">The following is the sample output:</span></span>  
  
    ```  
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
>  <span data-ttu-id="763e2-182">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="763e2-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="763e2-183">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="763e2-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="763e2-184">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="763e2-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="763e2-185">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="763e2-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a><span data-ttu-id="763e2-186">Consulte também</span><span class="sxs-lookup"><span data-stu-id="763e2-186">See Also</span></span>
