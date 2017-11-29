---
title: '&lt;NET. TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cd220b07c2d8f9a24591fc6e9614099e8460139
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltnettcpgt"></a><span data-ttu-id="ccc39-102">&lt;NET. TCP&gt;</span><span class="sxs-lookup"><span data-stu-id="ccc39-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="ccc39-103">Especifica as definições de configuração de rede. TCP porta de serviço de compartilhamento, que permite que vários processos compartilhem a mesma porta TCP.</span><span class="sxs-lookup"><span data-stu-id="ccc39-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="ccc39-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="ccc39-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="ccc39-105">\<NET. TCP ></span><span class="sxs-lookup"><span data-stu-id="ccc39-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccc39-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccc39-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="ccc39-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="ccc39-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccc39-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ccc39-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ccc39-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ccc39-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccc39-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ccc39-110">Attributes</span></span>  
  
|<span data-ttu-id="ccc39-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ccc39-111">Attribute</span></span>|<span data-ttu-id="ccc39-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccc39-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="ccc39-113">Um inteiro que especifica o máximo de conexões pendente que é aceitas da conexão compartilhada, mas ainda não foram expedido para [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="ccc39-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="ccc39-114">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="ccc39-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="ccc39-115">Um inteiro que especifica o máximo threads de aceitação simultâneas pendentes no ponto de extremidade escutando para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="ccc39-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="ccc39-116">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="ccc39-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="ccc39-117">O número máximo de conexões que o ouvinte pode ter aguardando para serem aceitas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ccc39-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="ccc39-118">Quando esse valor de cota for ultrapassada, novas conexões de entrada são descartadas em vez de esperar ser aceito.</span><span class="sxs-lookup"><span data-stu-id="ccc39-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="ccc39-119">Recursos de Conexão, como segurança de mensagem podem causar um cliente abrir mais de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="ccc39-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="ccc39-120">Os administradores de serviço devem levar em consideração para essas conexões adicionais ao definir esse valor de cota.</span><span class="sxs-lookup"><span data-stu-id="ccc39-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="ccc39-121">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="ccc39-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ccc39-122">Um `TimeSpan` que especifica o tempo limite para ler os dados de enquadramento e executar a expedição de conexão das conexões sublinhado.</span><span class="sxs-lookup"><span data-stu-id="ccc39-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="ccc39-123">O padrão é "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="ccc39-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="ccc39-124">Um valor booliano que indica se o serviço de compartilhamento de porta usa o serviço Teredo da Microsoft para escutar em TCP portas em nome de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="ccc39-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="ccc39-125">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="ccc39-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccc39-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ccc39-126">Child Elements</span></span>  
  
|<span data-ttu-id="ccc39-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="ccc39-127">Element</span></span>|<span data-ttu-id="ccc39-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccc39-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccc39-129">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="ccc39-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="ccc39-130">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="ccc39-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ccc39-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ccc39-131">Parent Elements</span></span>  
  
|<span data-ttu-id="ccc39-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="ccc39-132">Element</span></span>|<span data-ttu-id="ccc39-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccc39-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccc39-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="ccc39-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="ccc39-135">Contém definições de configuração para o processo do ouvinte SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="ccc39-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccc39-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="ccc39-136">Remarks</span></span>  
 <span data-ttu-id="ccc39-137">Para obter mais informações sobre o compartilhamento de porta, consulte [compartilhamento de porta NET. TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span><span class="sxs-lookup"><span data-stu-id="ccc39-137">For more information on port sharing, see [Net.TCP Port Sharing](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded).</span></span> <span data-ttu-id="ccc39-138">Para entender como configurar a serviço de compartilhamento de porta, consulte [Configurando o serviço de compartilhamento de porta NET. TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span><span class="sxs-lookup"><span data-stu-id="ccc39-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc39-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccc39-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="ccc39-140">Compartilhamento de porta NET. TCP</span><span class="sxs-lookup"><span data-stu-id="ccc39-140">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="ccc39-141">Configurando o serviço de compartilhamento de porta NET. TCP</span><span class="sxs-lookup"><span data-stu-id="ccc39-141">Configuring the Net.TCP Port Sharing Service</span></span>](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
