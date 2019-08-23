---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 7d868d84318db8c9fe188293154dc275060a3952
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933177"
---
# <a name="netpipe"></a><span data-ttu-id="68a1b-102">\<net.pipe></span><span class="sxs-lookup"><span data-stu-id="68a1b-102">\<net.pipe></span></span>
<span data-ttu-id="68a1b-103">Especifica as definições de configuração para o serviço de ativação de pipe nomeado, que gerencia o tempo de vida da conexão de pipe nomeado e lida com as solicitações de ativação que chegam em pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="68a1b-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="68a1b-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="68a1b-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="68a1b-105">\<net.pipe></span><span class="sxs-lookup"><span data-stu-id="68a1b-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68a1b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68a1b-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="68a1b-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="68a1b-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68a1b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="68a1b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="68a1b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="68a1b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68a1b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="68a1b-110">Attributes</span></span>  
  
|<span data-ttu-id="68a1b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="68a1b-111">Attribute</span></span>|<span data-ttu-id="68a1b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="68a1b-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="68a1b-113">Um inteiro que especifica o máximo de threads de aceitação simultâneas pendentes no ponto de extremidade de escuta para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="68a1b-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="68a1b-114">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="68a1b-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="68a1b-115">Um inteiro que especifica o número máximo de conexões que podem aguardar a expedição.</span><span class="sxs-lookup"><span data-stu-id="68a1b-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="68a1b-116">O padrão é 100.</span><span class="sxs-lookup"><span data-stu-id="68a1b-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="68a1b-117">Um <xref:System.TimeSpan> que especifica o tempo limite para ler os dados de enquadramento e executar a distribuição de conexão das conexões de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="68a1b-117">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="68a1b-118">O padrão é "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="68a1b-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68a1b-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="68a1b-119">Child Elements</span></span>  
  
|<span data-ttu-id="68a1b-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="68a1b-120">Element</span></span>|<span data-ttu-id="68a1b-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="68a1b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68a1b-122">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="68a1b-122">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="68a1b-123">Uma coleção de elementos de configuração que contêm `securityIdentifier` um atributo para especificar contas de usuário para processos que hospedam serviços WCF e recebem acesso de conexão ao serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="68a1b-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68a1b-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="68a1b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="68a1b-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="68a1b-125">Element</span></span>|<span data-ttu-id="68a1b-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="68a1b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68a1b-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="68a1b-127">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="68a1b-128">Contém definições de configuração para o processo de ouvinte SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="68a1b-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68a1b-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68a1b-129">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
