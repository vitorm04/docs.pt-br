---
title: Arquitetura de ativação do WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184249"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="bbd2d-102">Arquitetura de ativação do WAS</span><span class="sxs-lookup"><span data-stu-id="bbd2d-102">WAS Activation Architecture</span></span>
<span data-ttu-id="bbd2d-103">Este tópico itemeiza e discute os componentes do Serviço de Ativação de Processos do Windows (também conhecido como WAS).</span><span class="sxs-lookup"><span data-stu-id="bbd2d-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="bbd2d-104">Componentes de ativação</span><span class="sxs-lookup"><span data-stu-id="bbd2d-104">Activation Components</span></span>  
 <span data-ttu-id="bbd2d-105">Was consiste em vários componentes arquitetônicos:</span><span class="sxs-lookup"><span data-stu-id="bbd2d-105">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="bbd2d-106">Adaptadores de ouvintes.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-106">Listener adapters.</span></span> <span data-ttu-id="bbd2d-107">Os serviços do Windows que recebem mensagens em protocolos específicos de rede e se comunicam com o WAS para encaminhar mensagens recebidas para o processo correto do trabalhador.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="bbd2d-108">Foi.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-108">WAS.</span></span> <span data-ttu-id="bbd2d-109">O serviço Windows que gerencia a criação e a vida útil dos processos dos trabalhadores.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="bbd2d-110">O processo de trabalhador genérico executável (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="bbd2d-110">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="bbd2d-111">Gerente de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-111">Application manager.</span></span> <span data-ttu-id="bbd2d-112">Gerencia a criação e a vida útil dos domínios de aplicativos que hospedam aplicativos dentro do processo do trabalhador.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="bbd2d-113">Manipuladores de protocolo.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-113">Protocol handlers.</span></span> <span data-ttu-id="bbd2d-114">Componentes específicos do protocolo que executam no processo do trabalhador e gerenciam a comunicação entre o processo do trabalhador e os adaptadores individuais do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="bbd2d-115">Existem dois tipos de manipuladores de protocolo: manipuladores de protocolo de processo e manipuladores de protocolo AppDomain.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="bbd2d-116">Quando o WAS ativa uma instância de processo do trabalhador, ele carrega os manipuladores de protocolo de processo necessários no processo do trabalhador e usa o gerenciador de aplicativos para criar um domínio de aplicativo para hospedar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="bbd2d-117">O domínio do aplicativo carrega o código do aplicativo, bem como os manipuladores de protocolo AppDomain que os protocolos de rede usados pelo aplicativo exigem.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![Captura de tela que mostra a arquitetura WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="bbd2d-119">Adaptadores de Ouvintes</span><span class="sxs-lookup"><span data-stu-id="bbd2d-119">Listener Adapters</span></span>  
 <span data-ttu-id="bbd2d-120">Os adaptadores de ouvinte são serviços individuais do Windows que implementam a lógica de comunicação de rede usada para receber mensagens usando o protocolo de rede no qual eles ouvem.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="bbd2d-121">A tabela a seguir lista os adaptadores de ouvinte para protocolos Da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bbd2d-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="bbd2d-122">Nome do serviço do adaptador do ouvinte</span><span class="sxs-lookup"><span data-stu-id="bbd2d-122">Listener adapter service name</span></span>|<span data-ttu-id="bbd2d-123">Protocolo</span><span class="sxs-lookup"><span data-stu-id="bbd2d-123">Protocol</span></span>|<span data-ttu-id="bbd2d-124">Observações</span><span class="sxs-lookup"><span data-stu-id="bbd2d-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="bbd2d-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="bbd2d-125">W3SVC</span></span>|<span data-ttu-id="bbd2d-126">http</span><span class="sxs-lookup"><span data-stu-id="bbd2d-126">http</span></span>|<span data-ttu-id="bbd2d-127">Componente comum que fornece ativação HTTP para IIS 7.0 e WCF.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="bbd2d-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="bbd2d-128">NetTcpActivator</span></span>|<span data-ttu-id="bbd2d-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="bbd2d-129">net.tcp</span></span>|<span data-ttu-id="bbd2d-130">Depende do serviço NetTcpPortSharing.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="bbd2d-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="bbd2d-131">NetPipeActivator</span></span>|<span data-ttu-id="bbd2d-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="bbd2d-132">net.pipe</span></span>||  
|<span data-ttu-id="bbd2d-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="bbd2d-133">NetMsmqActivator</span></span>|<span data-ttu-id="bbd2d-134">net.msmq</span><span class="sxs-lookup"><span data-stu-id="bbd2d-134">net.msmq</span></span>|<span data-ttu-id="bbd2d-135">Para uso com aplicativos de fila de mensagens baseados em WCF.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="bbd2d-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="bbd2d-136">NetMsmqActivator</span></span>|<span data-ttu-id="bbd2d-137">msmq.formatname</span><span class="sxs-lookup"><span data-stu-id="bbd2d-137">msmq.formatname</span></span>|<span data-ttu-id="bbd2d-138">Fornece retrocompatibilidade com aplicativos de fila de mensagens existentes.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="bbd2d-139">Os adaptadores de ouvinte para protocolos específicos são registrados durante a instalação no arquivo applicationHost.config, como mostrado no exemplo XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a><span data-ttu-id="bbd2d-140">Manipuladores de protocolo</span><span class="sxs-lookup"><span data-stu-id="bbd2d-140">Protocol Handlers</span></span>  
 <span data-ttu-id="bbd2d-141">Os manipuladores de protocolos Process e AppDomain para protocolos específicos estão registrados no arquivo Web.config no nível da máquina.</span><span class="sxs-lookup"><span data-stu-id="bbd2d-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbd2d-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="bbd2d-142">See also</span></span>

- [<span data-ttu-id="bbd2d-143">Configurar o WAS para uso com o WCF</span><span class="sxs-lookup"><span data-stu-id="bbd2d-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="bbd2d-144">[Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="bbd2d-144">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
