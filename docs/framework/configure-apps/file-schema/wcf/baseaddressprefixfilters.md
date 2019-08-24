---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 55ffcfb5c0c84d68033d082cbe451696bd3c9dc2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988352"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="9d9e4-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="9d9e4-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="9d9e4-102">Representa uma coleção de elementos de configuração que especificam filtros de passagem, que fornecem um mecanismo para escolher as associações de Serviços de Informações da Internet (IIS) apropriadas ao hospedar o aplicativo de Windows Communication Foundation (WCF) no IIS.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="9d9e4-103">\<baseAddressPrefixFilters > não reconhecer "localhost", use o nome do computador totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="9d9e4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9d9e4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d9e4-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="9d9e4-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d9e4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d9e4-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d9e4-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9d9e4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9d9e4-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d9e4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9d9e4-109">Attributes</span></span>  
 <span data-ttu-id="9d9e4-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d9e4-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9d9e4-111">Child Elements</span></span>  
  
|<span data-ttu-id="9d9e4-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d9e4-112">Element</span></span>|<span data-ttu-id="9d9e4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d9e4-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d9e4-114">\<add></span><span class="sxs-lookup"><span data-stu-id="9d9e4-114">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="9d9e4-115">Adiciona um elemento de configuração que especifica um filtro de prefixo para os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d9e4-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9d9e4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9d9e4-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d9e4-117">Element</span></span>|<span data-ttu-id="9d9e4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d9e4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d9e4-119">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="9d9e4-119">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="9d9e4-120">Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d9e4-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="9d9e4-121">Remarks</span></span>  
 <span data-ttu-id="9d9e4-122">Um filtro de prefixo fornece uma maneira de provedores de hospedagem compartilhados especificar quais URIs devem ser usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="9d9e4-123">Ele permite que hosts compartilhados hospedem vários aplicativos com endereços base diferentes para o mesmo esquema no mesmo site.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="9d9e4-124">Os sites da Web do IIS são contêineres para aplicativos virtuais que contêm diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="9d9e4-125">O aplicativo em um site pode ser acessado por meio de uma ou mais associações do IIS.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="9d9e4-126">As associações do IIS fornecem duas informações: vinculação de protocolo e informações de associação.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="9d9e4-127">O protocolo de associação (por exemplo, HTTP) define o esquema sobre o qual ocorre a comunicação e as informações de associação (por exemplo, endereço IP, porta, cabeçalho) contêm os dados usados para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="9d9e4-128">O IIS dá suporte à especificação de várias associações IIS para cada site, o que resulta em vários endereços base para cada esquema.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="9d9e4-129">Como um serviço WCF hospedado em um site permite a associação a apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="9d9e4-130">Os endereços base de entrada, fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="9d9e4-131">Por exemplo, seu site pode conter os seguintes endereços base.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="9d9e4-132">Você pode usar o arquivo de configuração a seguir para especificar um filtro de prefixo no nível do AppDomain.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="9d9e4-133">Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os únicos endereços base para seus respectivos esquemas, que têm permissão para serem passados.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="9d9e4-134">Por padrão, quando o prefixo não é especificado, todos os endereços são passados.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="9d9e4-135">A especificação do prefixo só permite que o endereço de base correspondente para esse esquema seja passado.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d9e4-136">O filtro não oferece suporte a caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="9d9e4-137">Além disso, os baseaddresss fornecidos pelo IIS podem ter endereços associados a outros esquemas que não estão presentes `baseAddressPrefixFilters` na lista.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="9d9e4-138">Esses endereços não são filtrados.</span><span class="sxs-lookup"><span data-stu-id="9d9e4-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9e4-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d9e4-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="9d9e4-140">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="9d9e4-140">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
