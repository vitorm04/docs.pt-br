---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 5da05c7b6a9685b9e34b3181ce8e0bd31ccd052b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704950"
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="0367e-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="0367e-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="0367e-103">Um elemento de configuração que permite adicionar configurações que definem as configurações de ativação de serviço virtual que são mapeados para seus tipos de serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0367e-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="0367e-104">Isso torna possível para ativar serviços hospedados no WAS / IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="0367e-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="0367e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0367e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0367e-106">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="0367e-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="0367e-107">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="0367e-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0367e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0367e-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0367e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0367e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0367e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0367e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0367e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0367e-111">Attributes</span></span>  
 <span data-ttu-id="0367e-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0367e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0367e-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0367e-113">Child Elements</span></span>  
  
|<span data-ttu-id="0367e-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0367e-114">Element</span></span>|<span data-ttu-id="0367e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0367e-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0367e-116">\<add></span><span class="sxs-lookup"><span data-stu-id="0367e-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="0367e-117">Adiciona um elemento de configuração que especifica a ativação de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="0367e-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0367e-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0367e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0367e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="0367e-119">Element</span></span>|<span data-ttu-id="0367e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0367e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0367e-121">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="0367e-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="0367e-122">Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="0367e-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0367e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="0367e-123">Remarks</span></span>  
 <span data-ttu-id="0367e-124">O exemplo a seguir mostra como definir as configurações de ativação dentro de seu arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="0367e-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="0367e-125">Usando esta configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="0367e-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="0367e-126">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0367e-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="0367e-127">Você precisa colocar o `web.config` que contém a configuração sob a raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="0367e-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="0367e-128">Além disso, `serviceHostingEnvironment` é uma seção de herdável machinetoApplication.</span><span class="sxs-lookup"><span data-stu-id="0367e-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="0367e-129">Se você registrar um único serviço na raiz do computador, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="0367e-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="0367e-130">Ativação baseada em configuração oferece suporte à ativação pelo protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="0367e-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="0367e-131">Ele requer que as extensões no relatativeAddress, ou seja,. svc,. xoml ou. xamlx.</span><span class="sxs-lookup"><span data-stu-id="0367e-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="0367e-132">Você pode mapear suas próprias extensões para o buildProviders saber, que, em seguida, permitirá que você ativar o serviço ao longo de qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="0367e-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="0367e-133">Após o conflito, o `<serviceActivations>` seção substitui os registros. svc.</span><span class="sxs-lookup"><span data-stu-id="0367e-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0367e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0367e-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
