---
title: "Arquitetura de ativação do WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cfbda764984305c141fd416baea8efa6aef4591
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="was-activation-architecture"></a><span data-ttu-id="1d67a-102">Arquitetura de ativação do WAS</span><span class="sxs-lookup"><span data-stu-id="1d67a-102">WAS Activation Architecture</span></span>
<span data-ttu-id="1d67a-103">Este tópico relaciona e descreve os componentes do Windows Process Activation Service (também conhecido como WAS).</span><span class="sxs-lookup"><span data-stu-id="1d67a-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="1d67a-104">Componentes de ativação</span><span class="sxs-lookup"><span data-stu-id="1d67a-104">Activation Components</span></span>  
 <span data-ttu-id="1d67a-105">FOI consiste em vários componentes de arquitetura:</span><span class="sxs-lookup"><span data-stu-id="1d67a-105">WAS consists of several architectural components:</span></span>  
  
-   <span data-ttu-id="1d67a-106">Adaptadores de escuta.</span><span class="sxs-lookup"><span data-stu-id="1d67a-106">Listener adapters.</span></span> <span data-ttu-id="1d67a-107">Serviços do Windows que recebem mensagens em protocolos de rede específicos e se comunicar com o WAS para rotear mensagens de entrada para o processo de trabalho correto.</span><span class="sxs-lookup"><span data-stu-id="1d67a-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
-   <span data-ttu-id="1d67a-108">FOI.</span><span class="sxs-lookup"><span data-stu-id="1d67a-108">WAS.</span></span> <span data-ttu-id="1d67a-109">O serviço do Windows que gerencia a criação e o tempo de vida de processos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1d67a-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
-   <span data-ttu-id="1d67a-110">O executável do processo worker genérico (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="1d67a-110">The generic worker process executable (w3wp.exe).</span></span>  
  
-   <span data-ttu-id="1d67a-111">Gerenciador de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1d67a-111">Application manager.</span></span> <span data-ttu-id="1d67a-112">Gerencia a criação e o tempo de vida de domínios de aplicativos que processam hospedar aplicativos dentro do trabalhador.</span><span class="sxs-lookup"><span data-stu-id="1d67a-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
-   <span data-ttu-id="1d67a-113">Manipuladores de protocolo.</span><span class="sxs-lookup"><span data-stu-id="1d67a-113">Protocol handlers.</span></span> <span data-ttu-id="1d67a-114">Componentes de protocolo específico que executar no processo de trabalho e gerenciam a comunicação entre o processo de trabalho e os adaptadores de escuta individuais.</span><span class="sxs-lookup"><span data-stu-id="1d67a-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="1d67a-115">Existem dois tipos de manipuladores de protocolo: processar manipuladores de protocolo e manipuladores de protocolo do AppDomain.</span><span class="sxs-lookup"><span data-stu-id="1d67a-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="1d67a-116">Quando WAS ativa uma instância do processo de trabalho, ele carrega os manipuladores de protocolo de processo necessários no processo de trabalho e usa o Gerenciador de aplicativos para criar um domínio de aplicativo para hospedar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d67a-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="1d67a-117">O domínio do aplicativo carrega o código do aplicativo, bem como os manipuladores de protocolo do AppDomain que os protocolos de rede usados pelo exigem aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d67a-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 <span data-ttu-id="1d67a-118">![ARQUITETURA](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span><span class="sxs-lookup"><span data-stu-id="1d67a-118">![WAS Architecture](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span></span>  
  
### <a name="listener-adapters"></a><span data-ttu-id="1d67a-119">Adaptadores de escuta</span><span class="sxs-lookup"><span data-stu-id="1d67a-119">Listener Adapters</span></span>  
 <span data-ttu-id="1d67a-120">Os adaptadores de escuta são serviços individuais do Windows que implementam a lógica de comunicação de rede usada para receber mensagens usando o protocolo de rede na escuta.</span><span class="sxs-lookup"><span data-stu-id="1d67a-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="1d67a-121">A tabela a seguir lista os adaptadores de escuta para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protocolos.</span><span class="sxs-lookup"><span data-stu-id="1d67a-121">The following table lists the listener adapters for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protocols.</span></span>  
  
|<span data-ttu-id="1d67a-122">Nome de serviço do adaptador de escuta</span><span class="sxs-lookup"><span data-stu-id="1d67a-122">Listener adapter service name</span></span>|<span data-ttu-id="1d67a-123">Protocolo</span><span class="sxs-lookup"><span data-stu-id="1d67a-123">Protocol</span></span>|<span data-ttu-id="1d67a-124">Observações</span><span class="sxs-lookup"><span data-stu-id="1d67a-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="1d67a-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="1d67a-125">W3SVC</span></span>|<span data-ttu-id="1d67a-126">HTTP</span><span class="sxs-lookup"><span data-stu-id="1d67a-126">http</span></span>|<span data-ttu-id="1d67a-127">Componente comum que fornece ativação de HTTP para ambos os IIS 7.0 e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d67a-127">Common component that provides HTTP activation for both IIS 7.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>|  
|<span data-ttu-id="1d67a-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="1d67a-128">NetTcpActivator</span></span>|<span data-ttu-id="1d67a-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="1d67a-129">net.tcp</span></span>|<span data-ttu-id="1d67a-130">Depende do serviço de NetTcpPortSharing.</span><span class="sxs-lookup"><span data-stu-id="1d67a-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="1d67a-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="1d67a-131">NetPipeActivator</span></span>|<span data-ttu-id="1d67a-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="1d67a-132">net.pipe</span></span>||  
|<span data-ttu-id="1d67a-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="1d67a-133">NetMsmqActivator</span></span>|<span data-ttu-id="1d67a-134">NET. MSMQ</span><span class="sxs-lookup"><span data-stu-id="1d67a-134">net.msmq</span></span>|<span data-ttu-id="1d67a-135">Para uso com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-com base em aplicativos de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1d67a-135">For use with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="1d67a-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="1d67a-136">NetMsmqActivator</span></span>|<span data-ttu-id="1d67a-137">FormatName</span><span class="sxs-lookup"><span data-stu-id="1d67a-137">msmq.formatname</span></span>|<span data-ttu-id="1d67a-138">Versões anteriores fornece compatibilidade com aplicativos de enfileiramento de mensagens existentes.</span><span class="sxs-lookup"><span data-stu-id="1d67a-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="1d67a-139">Os adaptadores de escuta para protocolos específicos são registrados durante a instalação no arquivo applicationHost. config, conforme mostrado no exemplo XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="1d67a-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="1d67a-140">Manipuladores de protocolo</span><span class="sxs-lookup"><span data-stu-id="1d67a-140">Protocol Handlers</span></span>  
 <span data-ttu-id="1d67a-141">Processo e AppDomain manipuladores de protocolo para protocolos específicos são registrados no arquivo Web. config no nível da máquina.</span><span class="sxs-lookup"><span data-stu-id="1d67a-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d67a-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d67a-142">See Also</span></span>  
 [<span data-ttu-id="1d67a-143">Configurando o WAS para utilização com o WCF</span><span class="sxs-lookup"><span data-stu-id="1d67a-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="1d67a-144">Recursos de hospedagem do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="1d67a-144">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
