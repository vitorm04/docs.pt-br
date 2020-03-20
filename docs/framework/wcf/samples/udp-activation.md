---
title: Ativação de UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c0b351adb0b45f42404e94c74bdcff7785c2d0ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143714"
---
# <a name="udp-activation"></a><span data-ttu-id="78163-102">Ativação de UDP</span><span class="sxs-lookup"><span data-stu-id="78163-102">UDP Activation</span></span>
<span data-ttu-id="78163-103">Esta amostra é baseada na amostra [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="78163-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="78163-104">Ele estende a amostra [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) para suportar a ativação do processo usando o Serviço de Ativação de Processos do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="78163-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="78163-105">A amostra consiste em três peças principais:</span><span class="sxs-lookup"><span data-stu-id="78163-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="78163-106">Um Ativador de Protocolo UDP, um processo autônomo que recebe mensagens UDP em nome de aplicativos que devem ser ativados.</span><span class="sxs-lookup"><span data-stu-id="78163-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="78163-107">Um cliente que usa o transporte personalizado UDP para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="78163-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="78163-108">Um serviço (hospedado em um processo de trabalhador ativado pela WAS) que recebe mensagens sobre o transporte personalizado UDP.</span><span class="sxs-lookup"><span data-stu-id="78163-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="78163-109">Ativador de protocolo UDP</span><span class="sxs-lookup"><span data-stu-id="78163-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="78163-110">O Ativador de Protocolo UDP é uma ponte entre o cliente WCF e o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="78163-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="78163-111">Fornece comunicação de dados através do protocolo UDP na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="78163-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="78163-112">Tem duas funções principais:</span><span class="sxs-lookup"><span data-stu-id="78163-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="78163-113">WAS Listener Adapter (LA), que colabora com a WAS para ativar processos em resposta às mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="78163-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="78163-114">UDP Protocol Listener, que aceita mensagens UDP em nome de aplicativos que devem ser ativados.</span><span class="sxs-lookup"><span data-stu-id="78163-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="78163-115">O ativador deve estar sendo executado como um programa autônomo na máquina do servidor.</span><span class="sxs-lookup"><span data-stu-id="78163-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="78163-116">Normalmente, os adaptadores de ouvinte WAS (como o NetTcpActivator e o NetPipeActivator) são implementados em serviços windows de longa duração.</span><span class="sxs-lookup"><span data-stu-id="78163-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="78163-117">No entanto, para simplicidade e clareza, esta amostra implementa o ativador de protocolo como um aplicativo autônomo.</span><span class="sxs-lookup"><span data-stu-id="78163-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="78163-118">WAS Adaptador de ouvinte</span><span class="sxs-lookup"><span data-stu-id="78163-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="78163-119">O adaptador de ouvinte WAS para UDP é implementado na `UdpListenerAdapter` classe.</span><span class="sxs-lookup"><span data-stu-id="78163-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="78163-120">É o módulo que interage com o WAS para realizar a ativação do aplicativo para o protocolo UDP.</span><span class="sxs-lookup"><span data-stu-id="78163-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="78163-121">Isso é conseguido chamando as seguintes APIs do Webhost:</span><span class="sxs-lookup"><span data-stu-id="78163-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="78163-122">Após a `WebhostRegisterProtocol`chamada inicialmente, o adaptador de ouvinte recebe o retorno `ApplicationCreated` de chamada do WAS para todos os aplicativos registrados no aplicativoHost.config (localizado em %windir%\system32\inetsrv).</span><span class="sxs-lookup"><span data-stu-id="78163-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="78163-123">Nesta amostra, apenas lidamos com os aplicativos com o protocolo UDP (com o id de protocolo como "net.udp") ativado.</span><span class="sxs-lookup"><span data-stu-id="78163-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="78163-124">Outras implementações podem lidar com isso de forma diferente se essas implementações responderem a alterações dinâmicas de configuração no aplicativo (por exemplo, uma transição de aplicativo de desativado para habilitado).</span><span class="sxs-lookup"><span data-stu-id="78163-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="78163-125">Quando o `ConfigManagerInitializationCompleted` retorno de chamada é recebido, indica que o WAS tenha terminado todas as notificações para a inicialização do protocolo.</span><span class="sxs-lookup"><span data-stu-id="78163-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="78163-126">Neste momento, o adaptador de ouvinte está pronto para processar solicitações de ativação.</span><span class="sxs-lookup"><span data-stu-id="78163-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="78163-127">Quando uma nova solicitação chega na primeira vez para um `WebhostOpenListenerChannelInstance` aplicativo, o adaptador de ouvinte liga para o WAS, que inicia o processo do trabalhador se ele ainda não for iniciado.</span><span class="sxs-lookup"><span data-stu-id="78163-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="78163-128">Em seguida, os manipuladores de protocolo são carregados e a comunicação entre o adaptador ouvinte e o aplicativo virtual pode começar.</span><span class="sxs-lookup"><span data-stu-id="78163-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="78163-129">O adaptador de ouvinte está registrado na seção %SystemRoot%\System32\inetsrv\ApplicationHost.config na seção <`listenerAdapters`>:</span><span class="sxs-lookup"><span data-stu-id="78163-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="78163-130">Ouvinte de Protocolo</span><span class="sxs-lookup"><span data-stu-id="78163-130">Protocol Listener</span></span>  
 <span data-ttu-id="78163-131">O ouvinte de protocolo UDP é um módulo dentro do ativador de protocolo que ouve em um ponto final UDP em nome do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="78163-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="78163-132">É implementado na `UdpSocketListener`classe.</span><span class="sxs-lookup"><span data-stu-id="78163-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="78163-133">O ponto final `IPEndpoint` é representado como para o qual o número da porta é extraído da vinculação do protocolo para o site.</span><span class="sxs-lookup"><span data-stu-id="78163-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="78163-134">Serviço de Controle</span><span class="sxs-lookup"><span data-stu-id="78163-134">Control Service</span></span>  
 <span data-ttu-id="78163-135">Nesta amostra, utilizamos o WCF para comunicar entre o ativador e o processo do trabalhador WAS.</span><span class="sxs-lookup"><span data-stu-id="78163-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="78163-136">O serviço que reside no ativador é chamado de Serviço de Controle.</span><span class="sxs-lookup"><span data-stu-id="78163-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="78163-137">Manipuladores de protocolo</span><span class="sxs-lookup"><span data-stu-id="78163-137">Protocol Handlers</span></span>  
 <span data-ttu-id="78163-138">Após as chamadas `WebhostOpenListenerChannelInstance`do adaptador de ouvinte, o gerente de processo WAS inicia o processo do trabalhador se ele não for iniciado.</span><span class="sxs-lookup"><span data-stu-id="78163-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="78163-139">O gerenciador de aplicativos dentro do processo do trabalhador então carrega o PPH (Process Protocol Handler, manipulador de protocolo de processo udp) com a solicitação para isso `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="78163-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="78163-140">O PPH em `IAdphManager`turnos chamadas .`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="78163-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="78163-141">para iniciar o UDP AppDomain Protocol Handler (ADPH).</span><span class="sxs-lookup"><span data-stu-id="78163-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="78163-142">Configuração hostedUDPTransporte</span><span class="sxs-lookup"><span data-stu-id="78163-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="78163-143">As informações estão registradas no Web.config da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="78163-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="78163-144">Configuração especial para esta amostra</span><span class="sxs-lookup"><span data-stu-id="78163-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="78163-145">Esta amostra só pode ser construída e executada no Windows Vista, Windows Server 2008 ou Windows 7.</span><span class="sxs-lookup"><span data-stu-id="78163-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="78163-146">Para executar a amostra, primeiro você deve obter todos os componentes configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="78163-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="78163-147">Use as seguintes etapas para instalar a amostra.</span><span class="sxs-lookup"><span data-stu-id="78163-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="78163-148">Para configurar este exemplo</span><span class="sxs-lookup"><span data-stu-id="78163-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="78163-149">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="78163-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="78163-150">Construa o projeto no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="78163-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="78163-151">Após a compilação, ele também executa as seguintes operações na fase pós-compilação:</span><span class="sxs-lookup"><span data-stu-id="78163-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="78163-152">Instala a vinculação udp ao site "Site padrão".</span><span class="sxs-lookup"><span data-stu-id="78163-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="78163-153">Cria o aplicativo virtual "ServiceModelSamples" para apontar para o caminho físico: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="78163-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="78163-154">Ele também permite o protocolo "net.udp" para este aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="78163-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="78163-155">Inicie o aplicativo de interface de usuário "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="78163-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="78163-156">Clique na guia **Configuração,** verifique as seguintes caixas de seleção e clique **em Instalar** para instalá-las:</span><span class="sxs-lookup"><span data-stu-id="78163-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="78163-157">Adaptador de ouvinte UDP</span><span class="sxs-lookup"><span data-stu-id="78163-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="78163-158">Manipuladores de protocolo UDP</span><span class="sxs-lookup"><span data-stu-id="78163-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="78163-159">Clique na guia **Ativação** do aplicativo de interface do usuário "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="78163-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="78163-160">Clique no botão **Iniciar** para iniciar o adaptador de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="78163-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="78163-161">Agora você está pronto para executar o programa.</span><span class="sxs-lookup"><span data-stu-id="78163-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="78163-162">Quando você terminar com esta amostra, você deve executar Cleanup.bat para remover a vinculação net.udp do "Site da Web padrão".</span><span class="sxs-lookup"><span data-stu-id="78163-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="78163-163">Exemplo de uso</span><span class="sxs-lookup"><span data-stu-id="78163-163">Sample Usage</span></span>  
 <span data-ttu-id="78163-164">Após a compilação, há quatro binários diferentes gerados:</span><span class="sxs-lookup"><span data-stu-id="78163-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="78163-165">Cliente.exe: O código do cliente.</span><span class="sxs-lookup"><span data-stu-id="78163-165">Client.exe: The client code.</span></span> <span data-ttu-id="78163-166">A configuração App.config é compilada no arquivo de configuração cliente Client.exe.config.</span><span class="sxs-lookup"><span data-stu-id="78163-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="78163-167">UDPActivation.dll: a biblioteca que contém todas as principais implementações de UDP.</span><span class="sxs-lookup"><span data-stu-id="78163-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="78163-168">Service.dll: O código de serviço.</span><span class="sxs-lookup"><span data-stu-id="78163-168">Service.dll: The service code.</span></span> <span data-ttu-id="78163-169">Isso é copiado para o diretório \bin do aplicativo virtual ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="78163-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="78163-170">O arquivo de serviço é Service.svc e o arquivo de configuração é Web.config. Após a compilação, eles são copiados para o seguinte local: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="78163-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="78163-171">WasNetActivator: O programa ativador UDP.</span><span class="sxs-lookup"><span data-stu-id="78163-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="78163-172">Certifique-se de que todas as peças necessárias estejam instaladas corretamente.</span><span class="sxs-lookup"><span data-stu-id="78163-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="78163-173">As etapas a seguir mostram como executar a amostra:</span><span class="sxs-lookup"><span data-stu-id="78163-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="78163-174">Certifique-se de que os seguintes serviços do Windows foram iniciados:</span><span class="sxs-lookup"><span data-stu-id="78163-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="78163-175">Serviço de ativação de processos do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="78163-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="78163-176">Serviços de Informação na Internet (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="78163-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="78163-177">Em seguida, inicie o ativador, WasNetActivator.exe.</span><span class="sxs-lookup"><span data-stu-id="78163-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="78163-178">Na guia **Ativação,** o único protocolo, **UDP,** é selecionado na lista de desímparadas.</span><span class="sxs-lookup"><span data-stu-id="78163-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="78163-179">Clique no botão **Iniciar** para iniciar o ativador.</span><span class="sxs-lookup"><span data-stu-id="78163-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="78163-180">Uma vez iniciado o ativador, você pode executar o código do cliente executando Client.exe a partir de uma janela de comando.</span><span class="sxs-lookup"><span data-stu-id="78163-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="78163-181">A seguir está a saída da amostra:</span><span class="sxs-lookup"><span data-stu-id="78163-181">The following is the sample output:</span></span>  
  
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
> <span data-ttu-id="78163-182">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="78163-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="78163-183">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="78163-183">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="78163-184">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="78163-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="78163-185">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="78163-185">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
