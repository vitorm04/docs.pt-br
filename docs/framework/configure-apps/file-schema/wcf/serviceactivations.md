---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: c62f2bd1a34aca31ea9f9d5de17840f2967b269c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="90894-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="90894-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="90894-103">Um elemento de configuração que permite adicionar configurações que definem as configurações de ativação de serviços virtuais que são mapeados para seus tipos de serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="90894-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="90894-104">Isso torna possível para ativar serviços hospedados no WAS / IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="90894-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="90894-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="90894-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="90894-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="90894-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="90894-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="90894-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90894-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90894-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90894-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="90894-109">Attributes and Elements</span></span>  
 <span data-ttu-id="90894-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="90894-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90894-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="90894-111">Attributes</span></span>  
 <span data-ttu-id="90894-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="90894-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90894-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="90894-113">Child Elements</span></span>  
  
|<span data-ttu-id="90894-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="90894-114">Element</span></span>|<span data-ttu-id="90894-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="90894-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90894-116">\<add></span><span class="sxs-lookup"><span data-stu-id="90894-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="90894-117">Adiciona um elemento de configuração que especifica a ativação de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="90894-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90894-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="90894-118">Parent Elements</span></span>  
  
|<span data-ttu-id="90894-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="90894-119">Element</span></span>|<span data-ttu-id="90894-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="90894-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90894-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="90894-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="90894-122">Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="90894-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90894-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="90894-123">Remarks</span></span>  
 <span data-ttu-id="90894-124">O exemplo a seguir mostra como definir as configurações de ativação em seu arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="90894-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="90894-125">Usando esta configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="90894-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="90894-126">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="90894-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="90894-127">Você precisa colocar a `web.config` que contém a configuração abaixo da raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="90894-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="90894-128">Além disso, `serviceHostingEnvironment` uma seção herdáveis machinetoApplication.</span><span class="sxs-lookup"><span data-stu-id="90894-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="90894-129">Se você registrar um único serviço na raiz da máquina, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="90894-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="90894-130">Ativação baseada em configuração oferece suporte à ativação pelo protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="90894-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="90894-131">Ele requer extensões no relatativeAddress ou seja,. svc,. xoml ou .xamlx.</span><span class="sxs-lookup"><span data-stu-id="90894-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="90894-132">Você pode mapear suas próprias extensões para o buildProviders sabe, que, em seguida, permite que você ative o serviço em qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="90894-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="90894-133">Em conflito, a `<serviceActivations>` seção substitui registros. svc.</span><span class="sxs-lookup"><span data-stu-id="90894-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90894-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90894-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
