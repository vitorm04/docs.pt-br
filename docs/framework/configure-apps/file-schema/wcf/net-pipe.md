---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397723"
---
# <a name="netpipe"></a><span data-ttu-id="2bc49-102">\<net.pipe></span><span class="sxs-lookup"><span data-stu-id="2bc49-102">\<net.pipe></span></span>
<span data-ttu-id="2bc49-103">Especifica as definições de configuração para o serviço de ativação de pipe nomeado, que gerencia o tempo de vida da conexão de pipe nomeado e lida com as solicitações de ativação que chegam em pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="2bc49-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
<span data-ttu-id="2bc49-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2bc49-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2bc49-105">&nbsp;&nbsp;[ **\<sistema. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="2bc49-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="2bc49-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> de net. pipe**</span><span class="sxs-lookup"><span data-stu-id="2bc49-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc49-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bc49-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="2bc49-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="2bc49-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bc49-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2bc49-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2bc49-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2bc49-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bc49-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2bc49-111">Attributes</span></span>  
  
|<span data-ttu-id="2bc49-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="2bc49-112">Attribute</span></span>|<span data-ttu-id="2bc49-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bc49-113">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="2bc49-114">Um inteiro que especifica o máximo de threads de aceitação simultâneas pendentes no ponto de extremidade de escuta para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="2bc49-114">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="2bc49-115">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="2bc49-115">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="2bc49-116">Um inteiro que especifica o número máximo de conexões que podem aguardar a expedição.</span><span class="sxs-lookup"><span data-stu-id="2bc49-116">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="2bc49-117">O padrão é 100.</span><span class="sxs-lookup"><span data-stu-id="2bc49-117">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="2bc49-118">Um <xref:System.TimeSpan> que especifica o tempo limite para ler os dados de enquadramento e executar a distribuição de conexão das conexões de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="2bc49-118">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="2bc49-119">O padrão é "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="2bc49-119">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bc49-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2bc49-120">Child Elements</span></span>  
  
|<span data-ttu-id="2bc49-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bc49-121">Element</span></span>|<span data-ttu-id="2bc49-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bc49-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bc49-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="2bc49-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="2bc49-124">Uma coleção de elementos de configuração que contêm `securityIdentifier` um atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="2bc49-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bc49-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2bc49-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2bc49-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bc49-126">Element</span></span>|<span data-ttu-id="2bc49-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bc49-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bc49-128">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="2bc49-128">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="2bc49-129">Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="2bc49-129">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bc49-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bc49-130">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
