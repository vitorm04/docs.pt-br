---
title: <add> de <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 2572a6ee6763ae26fe5c56669e10f8c9aef8a280
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811789"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="a81a2-102">\<add> de \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="a81a2-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="a81a2-103">Representa um elemento de configuração que especifica um filtro de passagem, que fornece um mecanismo para escolher as associações de Serviços de Informações da Internet (IIS) apropriadas ao hospedar um aplicativo de Windows Communication Foundation (WCF) no IIS.</span><span class="sxs-lookup"><span data-stu-id="a81a2-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="a81a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a81a2-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a81a2-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a81a2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a81a2-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a81a2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a81a2-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a81a2-107">Attributes</span></span>  
  
|<span data-ttu-id="a81a2-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a81a2-108">Attribute</span></span>|<span data-ttu-id="a81a2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a81a2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a81a2-110">prefixo</span><span class="sxs-lookup"><span data-stu-id="a81a2-110">prefix</span></span>|<span data-ttu-id="a81a2-111">Um URI que é usado para corresponder a uma parte de um endereço base.</span><span class="sxs-lookup"><span data-stu-id="a81a2-111">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a81a2-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a81a2-112">Child Elements</span></span>  
 <span data-ttu-id="a81a2-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a81a2-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a81a2-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a81a2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a81a2-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="a81a2-115">Element</span></span>|<span data-ttu-id="a81a2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a81a2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="a81a2-117">Uma coleção de elementos de configuração que especificam filtros de passagem, que fornecem um mecanismo para escolher as associações do IIS apropriadas ao hospedar um aplicativo de Windows Communication Foundation (WCF) no IIS.</span><span class="sxs-lookup"><span data-stu-id="a81a2-117">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a81a2-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="a81a2-118">Remarks</span></span>  
 <span data-ttu-id="a81a2-119">Um filtro de prefixo fornece uma maneira de provedores de hospedagem compartilhados especificar quais URIs devem ser usados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="a81a2-119">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="a81a2-120">Ele permite que hosts compartilhados hospedem vários aplicativos com endereços base diferentes para o mesmo esquema no mesmo site.</span><span class="sxs-lookup"><span data-stu-id="a81a2-120">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="a81a2-121">Os sites da Web do IIS são contêineres para aplicativos virtuais que contêm diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="a81a2-121">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="a81a2-122">O aplicativo em um site pode ser acessado por meio de uma ou mais associações do IIS.</span><span class="sxs-lookup"><span data-stu-id="a81a2-122">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="a81a2-123">As associações do IIS fornecem duas informações: vinculação de protocolo e informações de associação.</span><span class="sxs-lookup"><span data-stu-id="a81a2-123">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="a81a2-124">O protocolo de associação (por exemplo, HTTP) define o esquema sobre o qual ocorre a comunicação e as informações de associação (por exemplo, endereço IP, porta, cabeçalho) contêm os dados usados para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="a81a2-124">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="a81a2-125">O IIS dá suporte à especificação de várias associações IIS para cada site, o que resulta em vários endereços base para cada esquema.</span><span class="sxs-lookup"><span data-stu-id="a81a2-125">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="a81a2-126">Como um serviço WCF hospedado em um site permite a associação a apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="a81a2-126">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="a81a2-127">Os endereços base de entrada, fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.</span><span class="sxs-lookup"><span data-stu-id="a81a2-127">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="a81a2-128">Por exemplo, seu site pode conter os seguintes endereços base:</span><span class="sxs-lookup"><span data-stu-id="a81a2-128">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="a81a2-129">Você pode usar o arquivo de configuração a seguir para especificar um filtro de prefixo no nível do AppDomain.</span><span class="sxs-lookup"><span data-stu-id="a81a2-129">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="a81a2-130">Neste exemplo, `net.tcp://test1.fabrikam.com:8000` e `http://test2.fabrikam.com:9000` são os únicos endereços base para seus respectivos esquemas que têm permissão para serem passados.</span><span class="sxs-lookup"><span data-stu-id="a81a2-130">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="a81a2-131">Por padrão, quando o prefixo não é especificado, todos os endereços são passados.</span><span class="sxs-lookup"><span data-stu-id="a81a2-131">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="a81a2-132">A especificação do prefixo só permite que o endereço de base correspondente para esse esquema seja passado.</span><span class="sxs-lookup"><span data-stu-id="a81a2-132">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a81a2-133">O filtro não oferece suporte a caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="a81a2-133">The filter does not support any wildcards.</span></span> <span data-ttu-id="a81a2-134">Além disso, os baseAddresss fornecidos pelo IIS podem ter endereços associados a outros esquemas que não estão presentes na `baseAddressPrefixFilters` lista.</span><span class="sxs-lookup"><span data-stu-id="a81a2-134">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="a81a2-135">Esses endereços não são filtrados.</span><span class="sxs-lookup"><span data-stu-id="a81a2-135">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a81a2-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="a81a2-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="a81a2-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="a81a2-137">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
