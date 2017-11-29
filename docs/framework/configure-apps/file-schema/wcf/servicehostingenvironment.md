---
title: '&lt;serviceHostingEnvironment&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5770cb8fd68eb68145f3f7fbcf197302883efe9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicehostingenvironmentgt"></a><span data-ttu-id="de71d-102">&lt;serviceHostingEnvironment&gt;</span><span class="sxs-lookup"><span data-stu-id="de71d-102">&lt;serviceHostingEnvironment&gt;</span></span>
<span data-ttu-id="de71d-103">Este elemento define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="de71d-103">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="de71d-104">Se esse elemento estiver vazio, o tipo padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="de71d-104">If this element is empty, the default type is used.</span></span> <span data-ttu-id="de71d-105">Esse elemento só pode ser usado no aplicativo ou arquivos de configuração no nível de máquina.</span><span class="sxs-lookup"><span data-stu-id="de71d-105">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="de71d-106">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="de71d-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="de71d-107">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="de71d-107">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de71d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de71d-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de71d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="de71d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="de71d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="de71d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de71d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="de71d-111">Attributes</span></span>  
  
|<span data-ttu-id="de71d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="de71d-112">Attribute</span></span>|<span data-ttu-id="de71d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="de71d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de71d-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="de71d-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="de71d-115">Um valor booliano que indica se o modo de compatibilidade ASP.NET foi ativado para o aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="de71d-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="de71d-116">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="de71d-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="de71d-117">Quando esse atributo é definido como `true`, solicitações [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviços fluem através do pipeline HTTP do ASP.NET e comunicação por meio de protocolos não HTTP está proibida.</span><span class="sxs-lookup"><span data-stu-id="de71d-117">When this attribute is set to `true`, requests to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="de71d-118">Para obter mais informações, consulte [serviços WCF e ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="de71d-118">For more information, see [WCF Services and ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="de71d-119">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="de71d-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="de71d-120">Um inteiro que especifica a quantidade mínima de memória livre que deve estar disponível para o sistema, antes que um serviço [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] possa ser ativado.</span><span class="sxs-lookup"><span data-stu-id="de71d-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service can be activated.</span></span> <span data-ttu-id="de71d-121">**Cuidado:** especificar esse atributo juntamente com confiança parcial no arquivo Web. config de um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviço resultará em um <xref:System.Security.SecurityException> quando o serviço é executado.</span><span class="sxs-lookup"><span data-stu-id="de71d-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="de71d-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="de71d-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="de71d-123">Um valor booleano que especifica se várias associações IIS por site está habilitado.</span><span class="sxs-lookup"><span data-stu-id="de71d-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="de71d-124">IIS consiste em sites, que são contêineres de aplicativos virtuais que contém diretórios virtuais.</span><span class="sxs-lookup"><span data-stu-id="de71d-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="de71d-125">O aplicativo em um site pode ser acessado por meio de um ou mais associação do IIS.</span><span class="sxs-lookup"><span data-stu-id="de71d-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="de71d-126">Uma associação IIS oferece dois tipos de informações: um protocolo de associação e informações de associação.</span><span class="sxs-lookup"><span data-stu-id="de71d-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="de71d-127">Protocolo de associação define o esquema durante o qual a comunicação ocorre, e informações de associação são as informações usadas para acessar o site.</span><span class="sxs-lookup"><span data-stu-id="de71d-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="de71d-128">Um exemplo de um protocolo de associação pode ser HTTP, enquanto as informações de associação podem conter um endereço IP, porta, o cabeçalho de host, etc.</span><span class="sxs-lookup"><span data-stu-id="de71d-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="de71d-129">O IIS oferece suporte à especificação várias associações IIS por site, o que resulta em vários endereços de base por esquema.</span><span class="sxs-lookup"><span data-stu-id="de71d-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="de71d-130">No entanto, um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço hospedado em um site permite que a associação baseAddress apenas uma por esquema.</span><span class="sxs-lookup"><span data-stu-id="de71d-130">However, a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="de71d-131">Para habilitar várias associações IIS por site para um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] de serviço, defina este atributo como `true`.</span><span class="sxs-lookup"><span data-stu-id="de71d-131">To enable multiple IIS bindings per site for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service, set this attribute to `true`.</span></span> <span data-ttu-id="de71d-132">Observe que várias associação de site só tem suporte para o protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="de71d-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="de71d-133">O endereço dos pontos de extremidade no arquivo de configuração deve ser um URI completo.</span><span class="sxs-lookup"><span data-stu-id="de71d-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de71d-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="de71d-134">Child Elements</span></span>  
  
|<span data-ttu-id="de71d-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="de71d-135">Element</span></span>|<span data-ttu-id="de71d-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="de71d-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de71d-137">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="de71d-137">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="de71d-138">Uma coleção de elementos de configuração que especificam filtros de prefixo para os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="de71d-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="de71d-139">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="de71d-139">\<serviceActivations></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|<span data-ttu-id="de71d-140">Uma seção de configuração que descreve as configurações de ativação.</span><span class="sxs-lookup"><span data-stu-id="de71d-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="de71d-141">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="de71d-141">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="de71d-142">Uma coleção de elementos de configuração que identificam o tipo de um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="de71d-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de71d-143">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="de71d-143">Parent Elements</span></span>  
  
|<span data-ttu-id="de71d-144">Elemento</span><span class="sxs-lookup"><span data-stu-id="de71d-144">Element</span></span>|<span data-ttu-id="de71d-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="de71d-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de71d-146">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="de71d-146">serviceModel</span></span>|<span data-ttu-id="de71d-147">O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="de71d-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de71d-148">Comentários</span><span class="sxs-lookup"><span data-stu-id="de71d-148">Remarks</span></span>  
 <span data-ttu-id="de71d-149">Por padrão, os serviços de WCF para execução lado a lado com o ASP.NET em domínios de aplicativo hospedado (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="de71d-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="de71d-150">Embora o WCF e ASP.NET podem coexistir no mesmo AppDomain, solicitações WCF não serão processadas pelo Pipeline de HTTP do ASP.NET por padrão.</span><span class="sxs-lookup"><span data-stu-id="de71d-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="de71d-151">Como resultado, vários elementos da plataforma do aplicativo ASP.NET não estão disponíveis para os serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="de71d-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="de71d-152">Esses incluem</span><span class="sxs-lookup"><span data-stu-id="de71d-152">These include</span></span>  
  
-   <span data-ttu-id="de71d-153">Autorização de URL da arquivo ASP.NET</span><span class="sxs-lookup"><span data-stu-id="de71d-153">ASP.NET File/URL Authorization</span></span>  
  
-   <span data-ttu-id="de71d-154">Representação do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="de71d-154">ASP.NET Impersonation</span></span>  
  
-   <span data-ttu-id="de71d-155">Estado da sessão baseada em cookie</span><span class="sxs-lookup"><span data-stu-id="de71d-155">Cookie-based Session State</span></span>  
  
-   <span data-ttu-id="de71d-156">HttpContext</span><span class="sxs-lookup"><span data-stu-id="de71d-156">HttpContext.Current</span></span>  
  
-   <span data-ttu-id="de71d-157">Extensibilidade de pipeline por meio de HttpModule personalizado</span><span class="sxs-lookup"><span data-stu-id="de71d-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="de71d-158">Se precisam de seus serviços WCF funcionar no contexto do ASP.NET e se comunicar somente por HTTP, você pode usar o modo de compatibilidade do ASP.NET do WCF.</span><span class="sxs-lookup"><span data-stu-id="de71d-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="de71d-159">Esse modo é ativado quando o `aspNetCompatibilityEnabled` atributo é definido como `true` no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de71d-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="de71d-160">Implementações de serviço devem declarar a capacidade de executar em modo de compatibilidade usando o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> classe.</span><span class="sxs-lookup"><span data-stu-id="de71d-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="de71d-161">Quando o modo de compatibilidade é habilitado,</span><span class="sxs-lookup"><span data-stu-id="de71d-161">When the compatibility mode is enabled,</span></span>  
  
-   <span data-ttu-id="de71d-162">Autorização de URL da arquivo ASP.NET é aplicada antes de autorização do WCF.</span><span class="sxs-lookup"><span data-stu-id="de71d-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="de71d-163">Uma decisão de autorização baseia-se a identidade de nível de transporte da solicitação.</span><span class="sxs-lookup"><span data-stu-id="de71d-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="de71d-164">Identidades no nível da mensagem são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="de71d-164">Identities at the message level are ignored.</span></span>  
  
-   <span data-ttu-id="de71d-165">Operações de serviço WCF começam a executar no contexto de representação do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="de71d-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="de71d-166">Se a representação do WCF e representação do ASP.NET estão habilitados para um serviço específico, o contexto de representação do WCF se aplica.</span><span class="sxs-lookup"><span data-stu-id="de71d-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
-   <span data-ttu-id="de71d-167">HttpContext pode ser usado no código de serviço do WCF e serviços são impedidos de expor pontos de extremidade HTTP não.</span><span class="sxs-lookup"><span data-stu-id="de71d-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
-   <span data-ttu-id="de71d-168">WCF são processadas pelo pipeline do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="de71d-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="de71d-169">HttpModules que foram configurados para atuar em solicitações de entrada também pode processar solicitações WCF.</span><span class="sxs-lookup"><span data-stu-id="de71d-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="de71d-170">Isso inclui componentes de plataforma do ASP.NET (por exemplo, <xref:System.Web.SessionState.SessionStateModule>), bem como módulos personalizados de terceiros.</span><span class="sxs-lookup"><span data-stu-id="de71d-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de71d-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de71d-171">Example</span></span>  
 <span data-ttu-id="de71d-172">O exemplo de código a seguir mostra como habilitar o modo de compatibilidade do ASP.</span><span class="sxs-lookup"><span data-stu-id="de71d-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="de71d-173">Código</span><span class="sxs-lookup"><span data-stu-id="de71d-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de71d-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de71d-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="de71d-175">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="de71d-175">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="de71d-176">Serviços WCF e ASP.NET</span><span class="sxs-lookup"><span data-stu-id="de71d-176">WCF Services and ASP.NET</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
