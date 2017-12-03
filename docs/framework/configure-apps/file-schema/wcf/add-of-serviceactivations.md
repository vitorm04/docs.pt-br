---
title: '&lt;adicionar&gt; &lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c49845169265e48b232963ed5a2e6215be75d3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="ff202-102">&lt;adicionar&gt; &lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="ff202-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="ff202-103">Um elemento de configuração que permite que você defina configurações de ativação de serviços virtuais que são mapeados para seus [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tipos de serviço.</span><span class="sxs-lookup"><span data-stu-id="ff202-103">A configuration element that allows you to define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="ff202-104">Isso torna possível para ativar serviços hospedados no WAS / IIS sem um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="ff202-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="ff202-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ff202-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ff202-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="ff202-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff202-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff202-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff202-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff202-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ff202-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ff202-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff202-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff202-110">Attributes</span></span>  
  
|<span data-ttu-id="ff202-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ff202-111">Attribute</span></span>|<span data-ttu-id="ff202-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff202-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff202-113">fábrica</span><span class="sxs-lookup"><span data-stu-id="ff202-113">factory</span></span>|<span data-ttu-id="ff202-114">Uma cadeia de caracteres que especifica o nome do tipo CLR da fábrica que gera um elemento de ativação do serviço.</span><span class="sxs-lookup"><span data-stu-id="ff202-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="ff202-115">serviço</span><span class="sxs-lookup"><span data-stu-id="ff202-115">service</span></span>|<span data-ttu-id="ff202-116">O ServiceType que implementa o serviço (o Typename qualificado completo ou o Typename curto (quando ele é colocado na pasta App_Code).</span><span class="sxs-lookup"><span data-stu-id="ff202-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="ff202-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="ff202-117">relativeAddress</span></span>|<span data-ttu-id="ff202-118">O endereço relativo dentro do aplicativo IIS atual - por exemplo "SVC".</span><span class="sxs-lookup"><span data-stu-id="ff202-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="ff202-119">No WCF 4.0 Este endereço relativo deve conter uma das extensões de arquivo conhecidos (. svc .xamlx,...). Nenhum arquivo físico deve existir para o relativeUrl</span><span class="sxs-lookup"><span data-stu-id="ff202-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff202-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff202-120">Child Elements</span></span>  
 <span data-ttu-id="ff202-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ff202-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff202-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff202-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ff202-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff202-123">Element</span></span>|<span data-ttu-id="ff202-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff202-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff202-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="ff202-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="ff202-126">Uma seção de configuração que descreve as configurações de ativação.</span><span class="sxs-lookup"><span data-stu-id="ff202-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff202-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff202-127">Remarks</span></span>  
 <span data-ttu-id="ff202-128">O exemplo a seguir mostra como definir as configurações de ativação em seu arquivo Web. config.</span><span class="sxs-lookup"><span data-stu-id="ff202-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="ff202-129">Usando esta configuração, você pode ativar o GreetingService sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="ff202-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="ff202-130">Observe que `<serviceHostingEnvironment>` é uma configuração de nível de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff202-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="ff202-131">Você precisa colocar a `web.config` que contém a configuração abaixo da raiz do aplicativo virtual.</span><span class="sxs-lookup"><span data-stu-id="ff202-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="ff202-132">Além disso, `serviceHostingEnvironment` uma seção herdáveis machinetoApplication.</span><span class="sxs-lookup"><span data-stu-id="ff202-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="ff202-133">Se você registrar um único serviço na raiz da máquina, cada serviço no aplicativo herdará esse serviço.</span><span class="sxs-lookup"><span data-stu-id="ff202-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="ff202-134">Ativação baseada em configuração oferece suporte à ativação pelo protocolo http e não http.</span><span class="sxs-lookup"><span data-stu-id="ff202-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="ff202-135">Ele requer extensões no relatativeAddress, ou seja,. svc,. xoml ou .xamlx.</span><span class="sxs-lookup"><span data-stu-id="ff202-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="ff202-136">Você pode mapear suas próprias extensões para o buildProviders sabe, que, em seguida, permite que você ative o serviço em qualquer extensão.</span><span class="sxs-lookup"><span data-stu-id="ff202-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="ff202-137">Em conflito, a `<serviceActivations>` seção substitui registros. svc.</span><span class="sxs-lookup"><span data-stu-id="ff202-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff202-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff202-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
