---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397723"
---
# \<net.pipe>
<span data-ttu-id="287f4-102">Especifica as definições de configuração para o serviço de ativação de pipe nomeado, que gerencia o tempo de vida da conexão de pipe nomeado e lida com as solicitações de ativação que chegam em pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="287f4-102">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="287f4-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="287f4-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="287f4-104">Type</span><span class="sxs-lookup"><span data-stu-id="287f4-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="287f4-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="287f4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="287f4-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="287f4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="287f4-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="287f4-107">Attributes</span></span>  
  
|<span data-ttu-id="287f4-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="287f4-108">Attribute</span></span>|<span data-ttu-id="287f4-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="287f4-109">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="287f4-110">Um inteiro que especifica o máximo de threads de aceitação simultâneas pendentes no ponto de extremidade de escuta para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="287f4-110">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="287f4-111">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="287f4-111">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="287f4-112">Um inteiro que especifica o número máximo de conexões que podem aguardar a expedição.</span><span class="sxs-lookup"><span data-stu-id="287f4-112">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="287f4-113">O padrão é 100.</span><span class="sxs-lookup"><span data-stu-id="287f4-113">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="287f4-114">Um <xref:System.TimeSpan> que especifica o tempo limite para ler os dados de enquadramento e executar a distribuição de conexão das conexões de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="287f4-114">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="287f4-115">O padrão é "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="287f4-115">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="287f4-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="287f4-116">Child Elements</span></span>  
  
|<span data-ttu-id="287f4-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="287f4-117">Element</span></span>|<span data-ttu-id="287f4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="287f4-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="287f4-119">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="287f4-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="287f4-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="287f4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="287f4-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="287f4-121">Element</span></span>|<span data-ttu-id="287f4-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="287f4-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="287f4-123">Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="287f4-123">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="287f4-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="287f4-124">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
