---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 0673507b72690c3a5c7dcc35442c05e378dba43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153029"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="b4dca-101">\<baseAddressPrefixFiltros></span><span class="sxs-lookup"><span data-stu-id="b4dca-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="b4dca-102">Representa uma coleção de elementos de configuração que especificam passar por filtros, que fornecem um mecanismo para escolher as vinculações apropriadas do IIS (Internet Information Services, serviços de informação da Internet) ao hospedar o aplicativo Da Windows Communication Foundation (WCF) no IIS.</span><span class="sxs-lookup"><span data-stu-id="b4dca-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b4dca-103">\<baseAddressPrefixFilters> não reconhece "localhost"; use o nome da máquina totalmente qualificado.</span><span class="sxs-lookup"><span data-stu-id="b4dca-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
<span data-ttu-id="b4dca-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4dca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b4dca-105">&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b4dca-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b4dca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviçoHospedagemdeambiente>**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="b4dca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="b4dca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFiltros>**</span><span class="sxs-lookup"><span data-stu-id="b4dca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4dca-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4dca-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4dca-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b4dca-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b4dca-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b4dca-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4dca-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b4dca-111">Attributes</span></span>  
 <span data-ttu-id="b4dca-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b4dca-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4dca-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b4dca-113">Child Elements</span></span>  
  
|<span data-ttu-id="b4dca-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4dca-114">Element</span></span>|<span data-ttu-id="b4dca-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4dca-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4dca-116">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="b4dca-116">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="b4dca-117">Adiciona um elemento de configuração que especifica um filtro de prefixo para os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="b4dca-117">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4dca-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b4dca-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b4dca-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4dca-119">Element</span></span>|<span data-ttu-id="b4dca-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4dca-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4dca-121">\<serviçoHospedagemdeambiente></span><span class="sxs-lookup"><span data-stu-id="b4dca-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="b4dca-122">Define o tipo que o ambiente de hospedagem de serviços instancia para um determinado transporte.</span><span class="sxs-lookup"><span data-stu-id="b4dca-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4dca-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4dca-123">Remarks</span></span>  
 <span data-ttu-id="b4dca-124">Um filtro de prefixo fornece uma maneira para os provedores de hospedagem compartilhada especificarem quais URIs devem ser usadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="b4dca-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="b4dca-125">Ele permite que hosts compartilhados hospedem vários aplicativos com diferentes endereços base para o mesmo esquema no mesmo site.</span><span class="sxs-lookup"><span data-stu-id="b4dca-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="b4dca-126">Os sites iIS são contêineres para aplicativos virtuais que contêm diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="b4dca-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="b4dca-127">O aplicativo em um site pode ser acessado através de uma ou mais vinculações iIS.</span><span class="sxs-lookup"><span data-stu-id="b4dca-127">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="b4dca-128">As ligações iIS fornecem duas informações: protocolo de vinculação e informações vinculativas.</span><span class="sxs-lookup"><span data-stu-id="b4dca-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="b4dca-129">O protocolo de vinculação (por exemplo, HTTP) define o esquema sobre o qual ocorre a comunicação e as informações vinculativas (por exemplo, endereço IP, porta, hostheader) contém dados usados para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="b4dca-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="b4dca-130">O IIS suporta especificar várias vinculações iis para cada site, o que resulta em vários endereços base para cada esquema.</span><span class="sxs-lookup"><span data-stu-id="b4dca-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="b4dca-131">Como um serviço WCF hospedado em um site permite vincular a apenas um endereço base para cada esquema, você pode usar o recurso de filtro de prefixo para escolher o endereço base necessário do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="b4dca-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="b4dca-132">Os endereços base de entrada, fornecidos pelo IIS, são filtrados com base no filtro de lista de prefixo opcional.</span><span class="sxs-lookup"><span data-stu-id="b4dca-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="b4dca-133">Por exemplo, seu site pode conter os seguintes endereços base:</span><span class="sxs-lookup"><span data-stu-id="b4dca-133">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="b4dca-134">Você pode usar o seguinte arquivo de configuração para especificar um filtro de prefixo no nível de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b4dca-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="b4dca-135">Neste exemplo, `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` e são os únicos endereços básicos para seus respectivos esquemas, que podem ser passados.</span><span class="sxs-lookup"><span data-stu-id="b4dca-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="b4dca-136">Por padrão, quando o prefixo não é especificado, todos os endereços são passados.</span><span class="sxs-lookup"><span data-stu-id="b4dca-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="b4dca-137">Especificar o prefixo só permite que o endereço base correspondente para esse esquema seja passado.</span><span class="sxs-lookup"><span data-stu-id="b4dca-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4dca-138">O filtro não suporta curingas.</span><span class="sxs-lookup"><span data-stu-id="b4dca-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="b4dca-139">Além disso, os endereços base fornecidos pelo IIS podem `baseAddressPrefixFilters` ter endereços vinculados a outros esquemas não presentes na lista.</span><span class="sxs-lookup"><span data-stu-id="b4dca-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="b4dca-140">Esses endereços não são filtrados.</span><span class="sxs-lookup"><span data-stu-id="b4dca-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4dca-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="b4dca-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="b4dca-142">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="b4dca-142">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
