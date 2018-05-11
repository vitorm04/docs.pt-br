---
title: '&lt;NET. pipe&gt;'
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: c054cf0e4110051bb4a9ce49003fd0099b111c21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltnetpipegt"></a><span data-ttu-id="0f239-102">&lt;NET. pipe&gt;</span><span class="sxs-lookup"><span data-stu-id="0f239-102">&lt;net.pipe&gt;</span></span>
<span data-ttu-id="0f239-103">Especifica as configurações para o serviço de ativação de Pipe nomeado, que gerencia o tempo de vida da conexão de pipe nomeado e manipula solicitações de ativação que chegam através de pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="0f239-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="0f239-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0f239-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="0f239-105">\<NET. pipe ></span><span class="sxs-lookup"><span data-stu-id="0f239-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f239-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f239-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="0f239-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="0f239-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f239-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0f239-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0f239-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0f239-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f239-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0f239-110">Attributes</span></span>  
  
|<span data-ttu-id="0f239-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0f239-111">Attribute</span></span>|<span data-ttu-id="0f239-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f239-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="0f239-113">Um inteiro que especifica o máximo threads de aceitação simultâneas pendentes no ponto de extremidade escutando para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="0f239-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="0f239-114">O padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="0f239-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="0f239-115">Um inteiro que especifica o número máximo de conexões que podem esperar por expedição.</span><span class="sxs-lookup"><span data-stu-id="0f239-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="0f239-116">O padrão é 100.</span><span class="sxs-lookup"><span data-stu-id="0f239-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0f239-117">Um `TimeSpan` que especifica o tempo limite para ler os dados de enquadramento e executar a expedição de conexão das conexões sublinhado.</span><span class="sxs-lookup"><span data-stu-id="0f239-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="0f239-118">O padrão é "00: 00:10"</span><span class="sxs-lookup"><span data-stu-id="0f239-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f239-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0f239-119">Child Elements</span></span>  
  
|<span data-ttu-id="0f239-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f239-120">Element</span></span>|<span data-ttu-id="0f239-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f239-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f239-122">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="0f239-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="0f239-123">Uma coleção de elementos de configuração que contêm um `securityIdentifier` atributo para especificar contas de usuário para processos que hospedam [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços e recebem acesso de conexão para o serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="0f239-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f239-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0f239-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0f239-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f239-125">Element</span></span>|<span data-ttu-id="0f239-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f239-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f239-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0f239-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="0f239-128">Contém definições de configuração para o processo do ouvinte SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="0f239-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f239-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f239-129">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
