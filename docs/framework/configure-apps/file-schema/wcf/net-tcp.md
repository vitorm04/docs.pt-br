---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397690"
---
# <a name="nettcp"></a><span data-ttu-id="f1692-102">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="f1692-102">\<net.tcp></span></span>
<span data-ttu-id="f1692-103">Especifica as definições de configuração para a rede. O serviço de compartilhamento de porta TCP, que permite que vários processos compartilhem a mesma porta TCP.</span><span class="sxs-lookup"><span data-stu-id="f1692-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
<span data-ttu-id="f1692-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f1692-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f1692-105">&nbsp;&nbsp;[ **\<sistema. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="f1692-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="f1692-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> NET. TCP**</span><span class="sxs-lookup"><span data-stu-id="f1692-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1692-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1692-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="f1692-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="f1692-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1692-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1692-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f1692-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f1692-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1692-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1692-111">Attributes</span></span>  
  
|<span data-ttu-id="f1692-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f1692-112">Attribute</span></span>|<span data-ttu-id="f1692-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1692-113">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="f1692-114">Um inteiro que especifica o máximo de conexões pendentes que são aceitas da conexão compartilhada, mas que ainda não foram expedidas para serviços de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f1692-114">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="f1692-115">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="f1692-115">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="f1692-116">Um inteiro que especifica o máximo de threads de aceitação simultâneas pendentes no ponto de extremidade de escuta para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="f1692-116">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="f1692-117">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="f1692-117">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="f1692-118">O número máximo de conexões que o ouvinte pode ter aguardando para ser aceito pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1692-118">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="f1692-119">Quando esse valor de cota é excedido, novas conexões de entrada são removidas em vez de aguardar para serem aceitas.</span><span class="sxs-lookup"><span data-stu-id="f1692-119">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="f1692-120">Recursos de conexão, como segurança de mensagem, podem fazer com que um cliente Abra mais de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="f1692-120">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="f1692-121">Os administradores de serviço devem considerar essas conexões adicionais ao definir esse valor de cota.</span><span class="sxs-lookup"><span data-stu-id="f1692-121">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="f1692-122">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="f1692-122">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f1692-123">Um <xref:System.TimeSpan> que especifica o tempo limite para ler os dados de enquadramento e executar a distribuição de conexão das conexões de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="f1692-123">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="f1692-124">O padrão é "00:00:10".</span><span class="sxs-lookup"><span data-stu-id="f1692-124">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="f1692-125">Um valor booliano que indica se o serviço de compartilhamento de porta usa o serviço Microsoft Teredo para escutar portas TCP em nome dos serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="f1692-125">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="f1692-126">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f1692-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1692-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1692-127">Child Elements</span></span>  
  
|<span data-ttu-id="f1692-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1692-128">Element</span></span>|<span data-ttu-id="f1692-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1692-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1692-130">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="f1692-130">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="f1692-131">Uma coleção de elementos de configuração que contêm `securityIdentifier` um atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="f1692-131">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1692-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f1692-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f1692-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1692-133">Element</span></span>|<span data-ttu-id="f1692-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1692-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1692-135">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f1692-135">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="f1692-136">Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="f1692-136">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1692-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1692-137">Remarks</span></span>  
 <span data-ttu-id="f1692-138">Para obter mais informações sobre compartilhamento de porta, consulte [net. TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="f1692-138">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="f1692-139">Para entender como configurar o serviço de compartilhamento de porta, consulte [Configurando o serviço de compartilhamento de porta Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="f1692-139">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1692-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1692-140">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="f1692-141">Compartilhamento de porta do NET.TCP</span><span class="sxs-lookup"><span data-stu-id="f1692-141">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="f1692-142">Configurando o serviço de compartilhamento de porta NET.TCP</span><span class="sxs-lookup"><span data-stu-id="f1692-142">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
