---
title: '&lt;adicionar&gt; &lt;baseAddressPrefixFilter&gt;'
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 549574d0d6585a857f3e0979e814c827139c7536
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a><span data-ttu-id="19360-102">&lt;adicionar&gt; &lt;baseAddressPrefixFilter&gt;</span><span class="sxs-lookup"><span data-stu-id="19360-102">&lt;add&gt; of &lt;baseAddressPrefixFilter&gt;</span></span>
<span data-ttu-id="19360-103">Representa um elemento de configuração que especifica um filtro de passagem, o que fornece um mecanismo para obter as associações de serviços de informações da Internet (IIS) apropriado ao hospedar um aplicativo do Windows Communication Foundation (WCF) no IIS.</span><span class="sxs-lookup"><span data-stu-id="19360-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="19360-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="19360-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="19360-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="19360-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="19360-106">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="19360-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="19360-107">\<add></span><span class="sxs-lookup"><span data-stu-id="19360-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19360-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19360-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19360-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="19360-109">Attributes and Elements</span></span>  
 <span data-ttu-id="19360-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="19360-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19360-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="19360-111">Attributes</span></span>  
  
|<span data-ttu-id="19360-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="19360-112">Attribute</span></span>|<span data-ttu-id="19360-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="19360-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19360-114">Prefixo</span><span class="sxs-lookup"><span data-stu-id="19360-114">prefix</span></span>|<span data-ttu-id="19360-115">Um URI que é usado para corresponder a uma parte de um endereço base.</span><span class="sxs-lookup"><span data-stu-id="19360-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19360-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="19360-116">Child Elements</span></span>  
 <span data-ttu-id="19360-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="19360-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19360-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="19360-118">Parent Elements</span></span>  
  
|<span data-ttu-id="19360-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="19360-119">Element</span></span>|<span data-ttu-id="19360-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="19360-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19360-121">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="19360-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="19360-122">Uma coleção de elementos de configuração que especificam filtros de passagem, que fornecem um mecanismo para obter as associações de IIS apropriadas ao hospedar um aplicativo do Windows Communication Foundation (WCF) no IIS.</span><span class="sxs-lookup"><span data-stu-id="19360-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19360-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="19360-123">Remarks</span></span>  
 <span data-ttu-id="19360-124">Um filtro de prefixo fornece uma maneira para provedores de hospedagem compartilhadas especificar os URIs são usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="19360-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="19360-125">Ele permite que os hosts compartilhados hospedar vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.</span><span class="sxs-lookup"><span data-stu-id="19360-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="19360-126">Sites da Web do IIS são contêineres de aplicativos virtuais que contêm diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="19360-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="19360-127">O aplicativo em um site pode ser acessado por meio de um ou mais associação do IIS.</span><span class="sxs-lookup"><span data-stu-id="19360-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="19360-128">Associações do IIS fornecem duas informações: protocolo de associação e informações de associação.</span><span class="sxs-lookup"><span data-stu-id="19360-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="19360-129">Associação de protocolo (por exemplo, HTTP) define o esquema durante o qual a comunicação ocorre, e (por exemplo, endereço IP, porta e cabeçalho de host) de informações de associação contém dados usados para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="19360-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="19360-130">O IIS oferece suporte à especificação várias associações de IIS para cada site, o que resulta em vários endereços de base para cada esquema.</span><span class="sxs-lookup"><span data-stu-id="19360-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="19360-131">Porque um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviço hospedado em um site permite que a associação apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="19360-131">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="19360-132">Os endereços base entrados fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.</span><span class="sxs-lookup"><span data-stu-id="19360-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="19360-133">Por exemplo, seu site pode conter os seguintes endereços de base.</span><span class="sxs-lookup"><span data-stu-id="19360-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="19360-134">Você pode usar o seguinte arquivo de configuração para especificar um filtro de prefixo no nível do appdomain.</span><span class="sxs-lookup"><span data-stu-id="19360-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="19360-135">Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os endereços base somente para seus respectivos esquemas que têm permissão para ser passado.</span><span class="sxs-lookup"><span data-stu-id="19360-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="19360-136">Por padrão, quando o prefixo não for especificado, todos os endereços são passados.</span><span class="sxs-lookup"><span data-stu-id="19360-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="19360-137">Especifica o prefixo permite apenas o endereço base correspondente para esse esquema deverá ser passado.</span><span class="sxs-lookup"><span data-stu-id="19360-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19360-138">O filtro não oferece suporte a todos os curingas.</span><span class="sxs-lookup"><span data-stu-id="19360-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="19360-139">Além disso, o baseAddresses fornecida pelo IIS pode ter endereços associados a outros esquemas não está presentes no `baseAddressPrefixFilters` lista.</span><span class="sxs-lookup"><span data-stu-id="19360-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="19360-140">Esses endereços não serão filtrados.</span><span class="sxs-lookup"><span data-stu-id="19360-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19360-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19360-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="19360-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="19360-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
