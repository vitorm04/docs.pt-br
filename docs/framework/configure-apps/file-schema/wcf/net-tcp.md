---
title: '&lt;net.tcp&gt;'
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: ae6837bf6dc8167e165a3adcd1fca8abc3dcd396
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500805"
---
# <a name="ltnettcpgt"></a><span data-ttu-id="b847e-102">&lt;net.tcp&gt;</span><span class="sxs-lookup"><span data-stu-id="b847e-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="b847e-103">Especifica as definições de configuração para a rede. TCP porta de serviço de compartilhamento, que permite que vários processos compartilhem a mesma porta TCP.</span><span class="sxs-lookup"><span data-stu-id="b847e-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="b847e-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b847e-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="b847e-105">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="b847e-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b847e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b847e-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="b847e-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="b847e-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b847e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b847e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b847e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b847e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b847e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b847e-110">Attributes</span></span>  
  
|<span data-ttu-id="b847e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b847e-111">Attribute</span></span>|<span data-ttu-id="b847e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b847e-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="b847e-113">Um inteiro que especifica o máximo de conexões pendentes que serão aceitas da conexão compartilhada, mas ainda não foram expedido para serviços Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b847e-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="b847e-114">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="b847e-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="b847e-115">Um inteiro que especifica o máximo threads de aceitação simultâneo pendentes no ponto de extremidade escutando para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="b847e-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="b847e-116">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="b847e-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="b847e-117">O número máximo de conexões que o ouvinte pode ter aguardando para serem aceitas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b847e-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="b847e-118">Quando esse valor de cota for excedida, novas conexões de entrada são descartadas em vez de esperar para ser aceito.</span><span class="sxs-lookup"><span data-stu-id="b847e-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="b847e-119">Recursos de Conexão, como segurança de mensagem podem fazer com que um cliente abrir mais de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="b847e-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="b847e-120">Os administradores de serviço devem levar em consideração para essas conexões adicionais ao definir esse valor de cota.</span><span class="sxs-lookup"><span data-stu-id="b847e-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="b847e-121">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="b847e-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b847e-122">Um `TimeSpan` que especifica o tempo limite para ler os dados de enquadramento e execução de expedição de conexão das conexões subjacentes.</span><span class="sxs-lookup"><span data-stu-id="b847e-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="b847e-123">O padrão é "00: 00:10".</span><span class="sxs-lookup"><span data-stu-id="b847e-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="b847e-124">Um valor booliano que indica se o serviço de compartilhamento de porta usa o serviço Teredo da Microsoft para escutar em portas TCP em nome dos serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="b847e-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="b847e-125">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b847e-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b847e-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b847e-126">Child Elements</span></span>  
  
|<span data-ttu-id="b847e-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="b847e-127">Element</span></span>|<span data-ttu-id="b847e-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="b847e-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b847e-129">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="b847e-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="b847e-130">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam serviços do WCF e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="b847e-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b847e-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b847e-131">Parent Elements</span></span>  
  
|<span data-ttu-id="b847e-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="b847e-132">Element</span></span>|<span data-ttu-id="b847e-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="b847e-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b847e-134">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="b847e-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="b847e-135">Contém definições de configuração para o processo de escuta SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="b847e-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b847e-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="b847e-136">Remarks</span></span>  
 <span data-ttu-id="b847e-137">Para obter mais informações sobre o compartilhamento de porta, consulte [compartilhamento de porta NET. TCP](https://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded).</span><span class="sxs-lookup"><span data-stu-id="b847e-137">For more information on port sharing, see [Net.TCP Port Sharing](https://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded).</span></span> <span data-ttu-id="b847e-138">Para entender como configurar a serviço de compartilhamento de porta, consulte [Configurando o serviço de compartilhamento de porta NET. TCP](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span><span class="sxs-lookup"><span data-stu-id="b847e-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b847e-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b847e-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="b847e-140">Compartilhamento de porta do NET.TCP</span><span class="sxs-lookup"><span data-stu-id="b847e-140">Net.TCP Port Sharing</span></span>](https://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="b847e-141">Configurando o serviço de compartilhamento de porta NET.TCP</span><span class="sxs-lookup"><span data-stu-id="b847e-141">Configuring the Net.TCP Port Sharing Service</span></span>](https://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
