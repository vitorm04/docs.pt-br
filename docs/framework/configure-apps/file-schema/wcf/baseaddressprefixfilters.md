---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39ceaf3377f1da7f3f953024e1207618df84bf1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="d80c2-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="d80c2-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="d80c2-103">Representa uma coleção de elementos de configuração que especificam a passagem por meio de filtros, que fornecem um mecanismo para obter as associações de serviços de informações da Internet (IIS) apropriado ao hospedar o [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplicativo no IIS.</span><span class="sxs-lookup"><span data-stu-id="d80c2-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d80c2-104">\<baseAddressPrefixFilters > não reconhece "localhost", use o nome do computador totalmente qualificado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d80c2-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="d80c2-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d80c2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d80c2-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="d80c2-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80c2-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d80c2-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d80c2-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d80c2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d80c2-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d80c2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d80c2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d80c2-110">Attributes</span></span>  
 <span data-ttu-id="d80c2-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d80c2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d80c2-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d80c2-112">Child Elements</span></span>  
  
|<span data-ttu-id="d80c2-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d80c2-113">Element</span></span>|<span data-ttu-id="d80c2-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d80c2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d80c2-115">\<add></span><span class="sxs-lookup"><span data-stu-id="d80c2-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="d80c2-116">Adiciona um elemento de configuração que especifica um filtro de prefixo para os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="d80c2-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d80c2-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d80c2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d80c2-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d80c2-118">Element</span></span>|<span data-ttu-id="d80c2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d80c2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d80c2-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="d80c2-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="d80c2-121">Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="d80c2-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d80c2-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="d80c2-122">Remarks</span></span>  
 <span data-ttu-id="d80c2-123">Um filtro de prefixo fornece uma maneira para provedores de hospedagem compartilhadas especificar os URIs são usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="d80c2-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="d80c2-124">Ele permite que os hosts compartilhados hospedar vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.</span><span class="sxs-lookup"><span data-stu-id="d80c2-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="d80c2-125">Sites da Web do IIS são contêineres de aplicativos virtuais que contêm diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="d80c2-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="d80c2-126">O aplicativo em um site pode ser acessado por meio de um ou mais associações de IIS.</span><span class="sxs-lookup"><span data-stu-id="d80c2-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="d80c2-127">Associações do IIS fornecem duas informações: protocolo de associação e informações de associação.</span><span class="sxs-lookup"><span data-stu-id="d80c2-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="d80c2-128">Associação de protocolo (por exemplo, HTTP) define o esquema durante o qual a comunicação ocorre, e (por exemplo, endereço IP, porta e cabeçalho de host) de informações de associação contém dados usados para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="d80c2-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="d80c2-129">O IIS oferece suporte à especificação várias associações de IIS para cada site, o que resulta em vários endereços de base para cada esquema.</span><span class="sxs-lookup"><span data-stu-id="d80c2-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="d80c2-130">Porque um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviço hospedado em um site permite que a associação apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="d80c2-130">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="d80c2-131">Os endereços base entrados fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.</span><span class="sxs-lookup"><span data-stu-id="d80c2-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="d80c2-132">Por exemplo, seu site pode conter os seguintes endereços de base.</span><span class="sxs-lookup"><span data-stu-id="d80c2-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="d80c2-133">Você pode usar o seguinte arquivo de configuração para especificar um filtro de prefixo no nível do appdomain.</span><span class="sxs-lookup"><span data-stu-id="d80c2-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d80c2-134">Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os endereços base somente para seus respectivos esquemas, que têm permissão para ser passado.</span><span class="sxs-lookup"><span data-stu-id="d80c2-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="d80c2-135">Por padrão, quando o prefixo não for especificado, todos os endereços são passados.</span><span class="sxs-lookup"><span data-stu-id="d80c2-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="d80c2-136">Especifica o prefixo permite apenas o endereço base correspondente para esse esquema deverá ser passado.</span><span class="sxs-lookup"><span data-stu-id="d80c2-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d80c2-137">O filtro não oferece suporte a todos os curingas.</span><span class="sxs-lookup"><span data-stu-id="d80c2-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="d80c2-138">Além disso, o baseAddresses fornecida pelo IIS pode ter endereços associados a outros esquemas não está presentes no `baseAddressPrefixFilters` lista.</span><span class="sxs-lookup"><span data-stu-id="d80c2-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="d80c2-139">Esses endereços não serão filtrados.</span><span class="sxs-lookup"><span data-stu-id="d80c2-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d80c2-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d80c2-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="d80c2-141">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="d80c2-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
