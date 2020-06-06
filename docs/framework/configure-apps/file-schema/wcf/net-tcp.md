---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397690"
---
# \<net.tcp>
<span data-ttu-id="6e231-102">Especifica as definições de configuração para a rede. O serviço de compartilhamento de porta TCP, que permite que vários processos compartilhem a mesma porta TCP.</span><span class="sxs-lookup"><span data-stu-id="6e231-102">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a><span data-ttu-id="6e231-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e231-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="6e231-104">Type</span><span class="sxs-lookup"><span data-stu-id="6e231-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e231-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6e231-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6e231-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6e231-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e231-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="6e231-107">Attributes</span></span>  
  
|<span data-ttu-id="6e231-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="6e231-108">Attribute</span></span>|<span data-ttu-id="6e231-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e231-109">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="6e231-110">Um inteiro que especifica o máximo de conexões pendentes que são aceitas da conexão compartilhada, mas que ainda não foram expedidas para serviços de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6e231-110">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="6e231-111">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="6e231-111">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="6e231-112">Um inteiro que especifica o máximo de threads de aceitação simultâneas pendentes no ponto de extremidade de escuta para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="6e231-112">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="6e231-113">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="6e231-113">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="6e231-114">O número máximo de conexões que o ouvinte pode ter aguardando para ser aceito pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6e231-114">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="6e231-115">Quando esse valor de cota é excedido, novas conexões de entrada são removidas em vez de aguardar para serem aceitas.</span><span class="sxs-lookup"><span data-stu-id="6e231-115">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="6e231-116">Recursos de conexão, como segurança de mensagem, podem fazer com que um cliente Abra mais de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="6e231-116">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="6e231-117">Os administradores de serviço devem considerar essas conexões adicionais ao definir esse valor de cota.</span><span class="sxs-lookup"><span data-stu-id="6e231-117">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="6e231-118">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="6e231-118">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6e231-119">Um <xref:System.TimeSpan> que especifica o tempo limite para ler os dados de enquadramento e executar a distribuição de conexão das conexões de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="6e231-119">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="6e231-120">O padrão é "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="6e231-120">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="6e231-121">Um valor booliano que indica se o serviço de compartilhamento de porta usa o serviço Microsoft Teredo para escutar portas TCP em nome dos serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="6e231-121">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="6e231-122">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="6e231-122">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e231-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6e231-123">Child Elements</span></span>  
  
|<span data-ttu-id="6e231-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e231-124">Element</span></span>|<span data-ttu-id="6e231-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e231-125">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="6e231-126">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="6e231-126">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e231-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e231-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6e231-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e231-128">Element</span></span>|<span data-ttu-id="6e231-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e231-129">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="6e231-130">Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="6e231-130">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e231-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e231-131">Remarks</span></span>  
 <span data-ttu-id="6e231-132">Para obter mais informações sobre compartilhamento de porta, consulte [net. TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="6e231-132">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="6e231-133">Para entender como configurar o serviço de compartilhamento de porta, consulte [Configurando o serviço de compartilhamento de porta Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="6e231-133">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e231-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="6e231-134">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="6e231-135">Compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="6e231-135">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="6e231-136">Configurando o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="6e231-136">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
