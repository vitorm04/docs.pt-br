---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 378db238d647be2248c0303f45aece42f7ea5b31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701002"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="3dd62-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="3dd62-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="3dd62-102">Representa uma coleção de elementos que especificam a passam por meio de filtros, que fornecem um mecanismo para coletar as associações de serviços de informações da Internet (IIS) apropriadas ao hospedar o aplicativo do Windows Communication Foundation (WCF) no IIS de configuração.</span><span class="sxs-lookup"><span data-stu-id="3dd62-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3dd62-103">\<baseAddressPrefixFilters > não reconhece "localhost", use o nome totalmente qualificado do computador em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3dd62-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="3dd62-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3dd62-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3dd62-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="3dd62-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd62-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3dd62-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3dd62-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3dd62-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3dd62-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3dd62-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3dd62-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3dd62-109">Attributes</span></span>  
 <span data-ttu-id="3dd62-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3dd62-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3dd62-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3dd62-111">Child Elements</span></span>  
  
|<span data-ttu-id="3dd62-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3dd62-112">Element</span></span>|<span data-ttu-id="3dd62-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3dd62-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3dd62-114">\<add></span><span class="sxs-lookup"><span data-stu-id="3dd62-114">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="3dd62-115">Adiciona um elemento de configuração que especifica um filtro de prefixo para os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="3dd62-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3dd62-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3dd62-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3dd62-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="3dd62-117">Element</span></span>|<span data-ttu-id="3dd62-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3dd62-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3dd62-119">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="3dd62-119">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="3dd62-120">Define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="3dd62-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dd62-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="3dd62-121">Remarks</span></span>  
 <span data-ttu-id="3dd62-122">Um filtro de prefixo fornece uma maneira para os provedores de hospedagem compartilhadas especificar quais URIs devem ser usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="3dd62-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="3dd62-123">Ele permite que os hosts compartilhados hospedar vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.</span><span class="sxs-lookup"><span data-stu-id="3dd62-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="3dd62-124">Sites da Web do IIS são contêineres para aplicativos virtuais que contêm os diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="3dd62-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="3dd62-125">O aplicativo em um site pode ser acessado por meio de uma ou mais associações de IIS.</span><span class="sxs-lookup"><span data-stu-id="3dd62-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="3dd62-126">Associações do IIS fornecem dois tipos de informação: informações de associação e o protocolo de associação.</span><span class="sxs-lookup"><span data-stu-id="3dd62-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="3dd62-127">Associação de protocolo (por exemplo, HTTP) define o esquema no qual a comunicação ocorre, e informações (por exemplo, endereço IP, porta, cabeçalho de host) de associação contém dados usados para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="3dd62-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="3dd62-128">IIS dá suporte à especificação de várias associações de IIS para cada site, o que resulta em vários endereços de base para cada esquema.</span><span class="sxs-lookup"><span data-stu-id="3dd62-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="3dd62-129">Como um serviço WCF hospedado em um site permite que a associação para apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="3dd62-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="3dd62-130">Os endereços base entrados fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.</span><span class="sxs-lookup"><span data-stu-id="3dd62-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="3dd62-131">Por exemplo, seu site pode conter os seguintes endereços de base.</span><span class="sxs-lookup"><span data-stu-id="3dd62-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="3dd62-132">Você pode usar o seguinte arquivo de configuração para especificar um filtro de prefixo no nível do appdomain.</span><span class="sxs-lookup"><span data-stu-id="3dd62-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="3dd62-133">Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os endereços base somente para seus respectivos esquemas, que têm permissão para ser passado.</span><span class="sxs-lookup"><span data-stu-id="3dd62-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="3dd62-134">Por padrão, quando o prefixo não for especificado, todos os endereços são passados.</span><span class="sxs-lookup"><span data-stu-id="3dd62-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="3dd62-135">Especificar o prefixo permite apenas o endereço base correspondente para que o esquema deve ser passado.</span><span class="sxs-lookup"><span data-stu-id="3dd62-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3dd62-136">O filtro não oferece suporte a curingas.</span><span class="sxs-lookup"><span data-stu-id="3dd62-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="3dd62-137">Além disso, o baseAddresses fornecida pelo IIS podem ter endereços associados a outros esquemas não está presentes no `baseAddressPrefixFilters` lista.</span><span class="sxs-lookup"><span data-stu-id="3dd62-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="3dd62-138">Esses endereços não serão filtrados.</span><span class="sxs-lookup"><span data-stu-id="3dd62-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd62-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3dd62-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="3dd62-140">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="3dd62-140">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
