---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 5a7043064593fa329618510d15baeb87da432652
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167087"
---
# \<serviceHostingEnvironment>

<span data-ttu-id="95de0-101">Esse elemento define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="95de0-101">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="95de0-102">Se esse elemento estiver vazio, o tipo padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="95de0-102">If this element is empty, the default type is used.</span></span> <span data-ttu-id="95de0-103">Esse elemento só pode ser usado nos arquivos de configuração no nível do aplicativo ou do computador.</span><span class="sxs-lookup"><span data-stu-id="95de0-103">This element can only be used at the application or machine level configuration files.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**  
  
## <a name="syntax"></a><span data-ttu-id="95de0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95de0-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95de0-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="95de0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="95de0-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="95de0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95de0-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="95de0-107">Attributes</span></span>  
  
|<span data-ttu-id="95de0-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="95de0-108">Attribute</span></span>|<span data-ttu-id="95de0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="95de0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95de0-110">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="95de0-110">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="95de0-111">Um valor booliano que indica se o modo de compatibilidade ASP.NET foi ativado para o aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="95de0-111">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="95de0-112">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="95de0-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="95de0-113">Quando esse atributo é definido como `true` , as solicitações para Windows Communication Foundation (WCF) fluem por meio do pipeline HTTP ASP.net e a comunicação por protocolos não http é proibida.</span><span class="sxs-lookup"><span data-stu-id="95de0-113">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="95de0-114">Para obter mais informações, consulte [Serviços WCF e ASP.net](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="95de0-114">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="95de0-115">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="95de0-115">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="95de0-116">Um inteiro que especifica a quantidade mínima de memória livre que deve estar disponível para o sistema, antes que um serviço WCF possa ser ativado.</span><span class="sxs-lookup"><span data-stu-id="95de0-116">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="95de0-117">**Cuidado:**  A especificação desse atributo junto com a confiança parcial no arquivo de web.config de um serviço WCF resultará em um <xref:System.Security.SecurityException> quando o serviço for executado.</span><span class="sxs-lookup"><span data-stu-id="95de0-117">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="95de0-118">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="95de0-118">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="95de0-119">Um valor booliano que especifica se várias associações IIS por site estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="95de0-119">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="95de0-120">O IIS consiste em sites da Web, que são contêineres para aplicativos virtuais que contêm diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="95de0-120">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="95de0-121">O aplicativo em um site pode ser acessado por meio de uma ou mais associações do IIS.</span><span class="sxs-lookup"><span data-stu-id="95de0-121">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="95de0-122">Uma associação do IIS fornece duas informações: um protocolo de associação e informações de associação.</span><span class="sxs-lookup"><span data-stu-id="95de0-122">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="95de0-123">O protocolo de associação define o esquema sobre o qual ocorre a comunicação e informações de associação são as informações usadas para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="95de0-123">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="95de0-124">Um exemplo de protocolo de associação pode ser HTTP, enquanto as informações de associação podem conter um endereço IP, uma porta, um cabeçalho de host, etc.</span><span class="sxs-lookup"><span data-stu-id="95de0-124">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="95de0-125">O IIS dá suporte à especificação de várias associações do IIS por site, o que resulta em vários endereços base por esquema.</span><span class="sxs-lookup"><span data-stu-id="95de0-125">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="95de0-126">No entanto, um serviço de Windows Communication Foundation (WCF) hospedado em um site permite a associação a apenas um baseAddress por esquema.</span><span class="sxs-lookup"><span data-stu-id="95de0-126">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="95de0-127">Para habilitar várias associações do IIS por site para um serviço Windows Communication Foundation (WCF), defina esse atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="95de0-127">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="95de0-128">Observe que a associação de vários sites tem suporte apenas para o protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="95de0-128">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="95de0-129">O endereço dos pontos de extremidade no arquivo de configuração precisa ser um URI completo.</span><span class="sxs-lookup"><span data-stu-id="95de0-129">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95de0-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="95de0-130">Child Elements</span></span>  
  
|<span data-ttu-id="95de0-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="95de0-131">Element</span></span>|<span data-ttu-id="95de0-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="95de0-132">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="95de0-133">Uma coleção de elementos de configuração que especificam filtros de prefixo para os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="95de0-133">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[\<serviceActivations>](serviceactivations.md)|<span data-ttu-id="95de0-134">Uma seção de configuração que descreve as configurações de ativação.</span><span class="sxs-lookup"><span data-stu-id="95de0-134">A configuration section that describes activation settings.</span></span>|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="95de0-135">Uma coleção de elementos de configuração que identificam o tipo de um transporte específico.</span><span class="sxs-lookup"><span data-stu-id="95de0-135">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95de0-136">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="95de0-136">Parent Elements</span></span>  
  
|<span data-ttu-id="95de0-137">Elemento</span><span class="sxs-lookup"><span data-stu-id="95de0-137">Element</span></span>|<span data-ttu-id="95de0-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="95de0-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95de0-139">serviceModel</span><span class="sxs-lookup"><span data-stu-id="95de0-139">serviceModel</span></span>|<span data-ttu-id="95de0-140">O elemento raiz de todos os elementos de configuração de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="95de0-140">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95de0-141">Comentários</span><span class="sxs-lookup"><span data-stu-id="95de0-141">Remarks</span></span>  

 <span data-ttu-id="95de0-142">Por padrão, os serviços WCF são executados lado a lado com ASP.NET em domínios de aplicativo hospedado (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="95de0-142">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="95de0-143">Embora o WCF e o ASP.NET possam coexistir no mesmo AppDomain, as solicitações do WCF não são processadas pelo pipeline HTTP do ASP.NET por padrão.</span><span class="sxs-lookup"><span data-stu-id="95de0-143">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="95de0-144">Como resultado, vários elementos da plataforma de aplicativo ASP.NET não estão disponíveis para os serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="95de0-144">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="95de0-145">Eles incluem:</span><span class="sxs-lookup"><span data-stu-id="95de0-145">These include</span></span>  
  
- <span data-ttu-id="95de0-146">Autorização de arquivo/URL ASP.NET</span><span class="sxs-lookup"><span data-stu-id="95de0-146">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="95de0-147">Personificação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="95de0-147">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="95de0-148">Estado de sessão baseado em cookie</span><span class="sxs-lookup"><span data-stu-id="95de0-148">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="95de0-149">HttpContext. Current</span><span class="sxs-lookup"><span data-stu-id="95de0-149">HttpContext.Current</span></span>  
  
- <span data-ttu-id="95de0-150">Extensibilidade de pipeline por meio de HttpModule personalizado</span><span class="sxs-lookup"><span data-stu-id="95de0-150">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="95de0-151">Se os serviços WCF precisarem funcionar no contexto ASP.NET e se comunicarem somente por meio de HTTP, você poderá usar o modo de compatibilidade ASP.NET do WCF.</span><span class="sxs-lookup"><span data-stu-id="95de0-151">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="95de0-152">Esse modo é ativado quando o `aspNetCompatibilityEnabled` atributo é definido como `true` no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95de0-152">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="95de0-153">As implementações de serviço devem declarar sua capacidade de execução no modo de compatibilidade usando a <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> classe.</span><span class="sxs-lookup"><span data-stu-id="95de0-153">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="95de0-154">Quando o modo de compatibilidade estiver habilitado,</span><span class="sxs-lookup"><span data-stu-id="95de0-154">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="95de0-155">A autorização de arquivo/URL ASP.NET é imposta antes da autorização do WCF.</span><span class="sxs-lookup"><span data-stu-id="95de0-155">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="95de0-156">Uma decisão de autorização é baseada na identidade de nível de transporte da solicitação.</span><span class="sxs-lookup"><span data-stu-id="95de0-156">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="95de0-157">As identidades no nível da mensagem são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="95de0-157">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="95de0-158">As operações de serviço WCF começam a ser executadas no contexto de representação ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="95de0-158">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="95de0-159">Se a representação do ASP.NET e a representação do WCF estiverem habilitadas para um serviço específico, o contexto de representação do WCF será aplicado.</span><span class="sxs-lookup"><span data-stu-id="95de0-159">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="95de0-160">HttpContext. Current pode ser usado no código do serviço WCF, e os serviços são impedidos de expor pontos de extremidade não HTTP.</span><span class="sxs-lookup"><span data-stu-id="95de0-160">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="95de0-161">As solicitações do WCF são processadas pelo pipeline ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="95de0-161">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="95de0-162">HttpModules que foram configurados para atuar em solicitações de entrada também podem processar solicitações do WCF.</span><span class="sxs-lookup"><span data-stu-id="95de0-162">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="95de0-163">Eles podem incluir componentes de plataforma ASP.NET (por exemplo, <xref:System.Web.SessionState.SessionStateModule> ), bem como módulos de terceiros personalizados.</span><span class="sxs-lookup"><span data-stu-id="95de0-163">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95de0-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95de0-164">Example</span></span>  

 <span data-ttu-id="95de0-165">O exemplo de código a seguir mostra como habilitar o modo de compatibilidade ASP.</span><span class="sxs-lookup"><span data-stu-id="95de0-165">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="95de0-166">Código</span><span class="sxs-lookup"><span data-stu-id="95de0-166">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="95de0-167">Confira também</span><span class="sxs-lookup"><span data-stu-id="95de0-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="95de0-168">Hosting</span><span class="sxs-lookup"><span data-stu-id="95de0-168">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="95de0-169">Serviços WCF e ASP.NET</span><span class="sxs-lookup"><span data-stu-id="95de0-169">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
