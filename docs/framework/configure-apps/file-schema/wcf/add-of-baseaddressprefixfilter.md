---
title: '&lt;adicionar&gt; &lt;baseAddressPrefixFilter&gt;'
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: ece3178c48c84c609ab959a5cfc426062de9255f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145595"
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a><span data-ttu-id="9a929-102">&lt;adicionar&gt; &lt;baseAddressPrefixFilter&gt;</span><span class="sxs-lookup"><span data-stu-id="9a929-102">&lt;add&gt; of &lt;baseAddressPrefixFilter&gt;</span></span>
<span data-ttu-id="9a929-103">Representa um elemento de configuração que especifica um filtro de passagem, que fornece um mecanismo para coletar as associações de serviços de informações da Internet (IIS) apropriadas ao hospedar um aplicativo do Windows Communication Foundation (WCF) no IIS.</span><span class="sxs-lookup"><span data-stu-id="9a929-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="9a929-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9a929-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9a929-105">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="9a929-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="9a929-106">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="9a929-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="9a929-107">\<add></span><span class="sxs-lookup"><span data-stu-id="9a929-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a929-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a929-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a929-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9a929-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9a929-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9a929-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a929-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a929-111">Attributes</span></span>  
  
|<span data-ttu-id="9a929-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="9a929-112">Attribute</span></span>|<span data-ttu-id="9a929-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a929-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a929-114">Prefixo</span><span class="sxs-lookup"><span data-stu-id="9a929-114">prefix</span></span>|<span data-ttu-id="9a929-115">Um URI que é usado para corresponder a uma parte de um endereço básico.</span><span class="sxs-lookup"><span data-stu-id="9a929-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a929-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9a929-116">Child Elements</span></span>  
 <span data-ttu-id="9a929-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9a929-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a929-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9a929-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9a929-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a929-119">Element</span></span>|<span data-ttu-id="9a929-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a929-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a929-121">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="9a929-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="9a929-122">Uma coleção de elementos de configuração que especificam filtros de passagem, que fornecem um mecanismo para coletar as associações de IIS apropriadas ao hospedar um aplicativo do Windows Communication Foundation (WCF) no IIS.</span><span class="sxs-lookup"><span data-stu-id="9a929-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a929-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a929-123">Remarks</span></span>  
 <span data-ttu-id="9a929-124">Um filtro de prefixo fornece uma maneira para os provedores de hospedagem compartilhadas especificar quais URIs devem ser usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="9a929-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="9a929-125">Ele permite que os hosts compartilhados hospedar vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.</span><span class="sxs-lookup"><span data-stu-id="9a929-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="9a929-126">Sites da Web do IIS são contêineres para aplicativos virtuais que contêm os diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="9a929-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="9a929-127">O aplicativo em um site pode ser acessado por meio de um ou mais associação do IIS.</span><span class="sxs-lookup"><span data-stu-id="9a929-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="9a929-128">Associações do IIS fornecem dois tipos de informação: informações de associação e o protocolo de associação.</span><span class="sxs-lookup"><span data-stu-id="9a929-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="9a929-129">Associação de protocolo (por exemplo, HTTP) define o esquema no qual a comunicação ocorre, e informações (por exemplo, endereço IP, porta, cabeçalho de host) de associação contém dados usados para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="9a929-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="9a929-130">IIS dá suporte à especificação de várias associações de IIS para cada site, o que resulta em vários endereços de base para cada esquema.</span><span class="sxs-lookup"><span data-stu-id="9a929-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="9a929-131">Como um serviço WCF hospedado em um site permite que a associação para apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="9a929-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="9a929-132">Os endereços base entrados fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.</span><span class="sxs-lookup"><span data-stu-id="9a929-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="9a929-133">Por exemplo, seu site pode conter os seguintes endereços de base.</span><span class="sxs-lookup"><span data-stu-id="9a929-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="9a929-134">Você pode usar o seguinte arquivo de configuração para especificar um filtro de prefixo no nível do appdomain.</span><span class="sxs-lookup"><span data-stu-id="9a929-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="9a929-135">Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os endereços base somente para seus respectivos esquemas que têm permissão para ser passado.</span><span class="sxs-lookup"><span data-stu-id="9a929-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="9a929-136">Por padrão, quando o prefixo não for especificado, todos os endereços são passados.</span><span class="sxs-lookup"><span data-stu-id="9a929-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="9a929-137">Especificar o prefixo permite apenas o endereço base correspondente para que o esquema deve ser passado.</span><span class="sxs-lookup"><span data-stu-id="9a929-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a929-138">O filtro não oferece suporte a curingas.</span><span class="sxs-lookup"><span data-stu-id="9a929-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="9a929-139">Além disso, o baseAddresses fornecida pelo IIS podem ter endereços associados a outros esquemas não está presentes no `baseAddressPrefixFilters` lista.</span><span class="sxs-lookup"><span data-stu-id="9a929-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="9a929-140">Esses endereços não serão filtrados.</span><span class="sxs-lookup"><span data-stu-id="9a929-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a929-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a929-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="9a929-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="9a929-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
