---
title: '&lt;serviceMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a771b3b89c9031a011185a579e70767081d20597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicemetadatagt"></a><span data-ttu-id="7d58c-102">&lt;serviceMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="7d58c-102">&lt;serviceMetadata&gt;</span></span>
<span data-ttu-id="7d58c-103">Especifica a publicação de metadados de serviço e as informações associadas.</span><span class="sxs-lookup"><span data-stu-id="7d58c-103">Specifies the publication of service metadata and associated information.</span></span>  
  
<span data-ttu-id="7d58c-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7d58c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7d58c-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7d58c-105">\<behaviors></span></span>  
<span data-ttu-id="7d58c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7d58c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7d58c-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="7d58c-107">\<behavior></span></span>  
<span data-ttu-id="7d58c-108">\<serviceMetadata ></span><span class="sxs-lookup"><span data-stu-id="7d58c-108">\<serviceMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d58c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d58c-109">Syntax</span></span>  
  
```xml
<serviceMetadata externalMetadataLocation="String"  
                 httpGetBinding="String" 
                 httpGetBindingConfiguration="String"  
                 httpGetEnabled="Boolean" 
                 httpGetUrl="String" 
                 httpsGetBinding="String" 
                 httpsGetBindingConfiguration="String"  
                 httpsGetEnabled="Boolean"   
                 httpsGetUrl="String"  
                 policyVersion="Policy12/Policy15" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d58c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7d58c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d58c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7d58c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d58c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7d58c-112">Attributes</span></span>  
  
|<span data-ttu-id="7d58c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="7d58c-113">Attribute</span></span>|<span data-ttu-id="7d58c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d58c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d58c-115">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="7d58c-115">externalMetadataLocation</span></span>|<span data-ttu-id="7d58c-116">Um Uri que contém o local de um arquivo WSDL, que é retornado para o usuário em resposta a solicitações WSDL e MEX em vez do WSDL gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7d58c-116">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="7d58c-117">Quando esse atributo não for definido, o padrão WSDL é retornado.</span><span class="sxs-lookup"><span data-stu-id="7d58c-117">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="7d58c-118">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="7d58c-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="7d58c-119">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="7d58c-119">httpGetBinding</span></span>|<span data-ttu-id="7d58c-120">Uma cadeia de caracteres que especifica o tipo de associação que será usado para recuperação de metadados via HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="7d58c-120">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="7d58c-121">Essa configuração é opcional.</span><span class="sxs-lookup"><span data-stu-id="7d58c-121">This setting is optional.</span></span> <span data-ttu-id="7d58c-122">Se não for especificado, as associações padrão serão usadas.</span><span class="sxs-lookup"><span data-stu-id="7d58c-122">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="7d58c-123">Somente associações com elementos de associação interna que suportam <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte.</span><span class="sxs-lookup"><span data-stu-id="7d58c-123">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="7d58c-124">Além disso, o <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d58c-124">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="7d58c-125">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d58c-125">httpGetBindingConfiguration</span></span>|<span data-ttu-id="7d58c-126">Uma cadeia de caracteres que define o nome da associação que é especificado no `httpGetBinding` atributo, o que faz referência às informações de configuração adicionais desta associação.</span><span class="sxs-lookup"><span data-stu-id="7d58c-126">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="7d58c-127">O mesmo nome deve ser definido na `<bindings>` seção.</span><span class="sxs-lookup"><span data-stu-id="7d58c-127">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="7d58c-128">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="7d58c-128">httpGetEnabled</span></span>|<span data-ttu-id="7d58c-129">Um valor booleano que especifica se deve publicar metadados de serviço para recuperação usando uma solicitação HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="7d58c-129">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="7d58c-130">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="7d58c-130">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7d58c-131">Se o atributo httpGetUrl não for especificado, o endereço no qual os metadados são publicados é o endereço de serviço mais um "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="7d58c-131">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="7d58c-132">Por exemplo, se o endereço do serviço é "http://localhost:8080/CalculatorService", o endereço de metadados HTTP/Get é "http://localhost:8080/CalculatorService? wsdl".</span><span class="sxs-lookup"><span data-stu-id="7d58c-132">For example, if the service address is "http://localhost:8080/CalculatorService", the HTTP/Get metadata address is "http://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="7d58c-133">Se essa propriedade for `false`, ou o endereço do serviço não é baseado em HTTP ou HTTPS, "? wsdl" será ignorado.</span><span class="sxs-lookup"><span data-stu-id="7d58c-133">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="7d58c-134">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="7d58c-134">httpGetUrl</span></span>|<span data-ttu-id="7d58c-135">Um Uri que especifica o endereço no qual os metadados são publicados para recuperação usando uma solicitação HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="7d58c-135">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="7d58c-136">Se um Uri relativo for especificado será tratado como relativo ao endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="7d58c-136">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="7d58c-137">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="7d58c-137">httpsGetBinding</span></span>|<span data-ttu-id="7d58c-138">Uma cadeia de caracteres que especifica o tipo de associação que será usado para recuperação de metadados via HTTPS GET.</span><span class="sxs-lookup"><span data-stu-id="7d58c-138">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="7d58c-139">Essa configuração é opcional.</span><span class="sxs-lookup"><span data-stu-id="7d58c-139">This setting is optional.</span></span> <span data-ttu-id="7d58c-140">Se não for especificado, as associações padrão serão usadas.</span><span class="sxs-lookup"><span data-stu-id="7d58c-140">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="7d58c-141">Somente associações com elementos de associação interna que suportam <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte.</span><span class="sxs-lookup"><span data-stu-id="7d58c-141">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="7d58c-142">Além disso, o <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d58c-142">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="7d58c-143">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d58c-143">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="7d58c-144">Uma cadeia de caracteres que define o nome da associação que é especificado no `httpsGetBinding` atributo, o que faz referência às informações de configuração adicionais desta associação.</span><span class="sxs-lookup"><span data-stu-id="7d58c-144">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="7d58c-145">O mesmo nome deve ser definido na `<bindings>` seção.</span><span class="sxs-lookup"><span data-stu-id="7d58c-145">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="7d58c-146">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="7d58c-146">httpsGetEnabled</span></span>|<span data-ttu-id="7d58c-147">Um valor booleano que especifica se deve publicar metadados de serviço para recuperação usando uma solicitação HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="7d58c-147">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="7d58c-148">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="7d58c-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7d58c-149">Se o atributo httpsGetUrl não for especificado, o endereço no qual os metadados são publicados é o endereço de serviço mais um "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="7d58c-149">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="7d58c-150">Por exemplo, se o endereço do serviço é "https://localhost:8080/CalculatorService", o endereço de metadados HTTP/Get é "https://localhost:8080/CalculatorService? wsdl".</span><span class="sxs-lookup"><span data-stu-id="7d58c-150">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="7d58c-151">Se essa propriedade for `false`, ou o endereço do serviço não é baseado em HTTP ou HTTPS, "? wsdl" será ignorado.</span><span class="sxs-lookup"><span data-stu-id="7d58c-151">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="7d58c-152">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="7d58c-152">httpsGetUrl</span></span>|<span data-ttu-id="7d58c-153">Um Uri que especifica o endereço no qual os metadados são publicados para recuperação usando uma solicitação HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="7d58c-153">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="7d58c-154">PolicyVersion</span><span class="sxs-lookup"><span data-stu-id="7d58c-154">policyVersion</span></span>|<span data-ttu-id="7d58c-155">Uma cadeia de caracteres que especifica a versão da especificação WS-Policy sendo usada.</span><span class="sxs-lookup"><span data-stu-id="7d58c-155">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="7d58c-156">Esse atributo é do tipo <xref:System.ServiceModel.Description.PolicyVersion>.</span><span class="sxs-lookup"><span data-stu-id="7d58c-156">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d58c-157">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7d58c-157">Child Elements</span></span>  
 <span data-ttu-id="7d58c-158">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7d58c-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d58c-159">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7d58c-159">Parent Elements</span></span>  
  
|<span data-ttu-id="7d58c-160">Elemento</span><span class="sxs-lookup"><span data-stu-id="7d58c-160">Element</span></span>|<span data-ttu-id="7d58c-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d58c-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d58c-162">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="7d58c-162">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7d58c-163">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="7d58c-163">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d58c-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="7d58c-164">Remarks</span></span>  
 <span data-ttu-id="7d58c-165">Este elemento de configuração permite que você controle os recursos de publicação de metadados de um serviço.</span><span class="sxs-lookup"><span data-stu-id="7d58c-165">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="7d58c-166">Para evitar a divulgação acidental de metadados de serviço potencialmente confidenciais, a configuração padrão para [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviços desabilita a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="7d58c-166">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="7d58c-167">Esse comportamento é seguro por padrão, mas também significa que você não pode usar metadados importa ferramenta (como Svcutil.exe) para gerar o código de cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço é explicitamente habilitado na configuração.</span><span class="sxs-lookup"><span data-stu-id="7d58c-167">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="7d58c-168">Usando este elemento de configuração, você pode habilitar o comportamento de publicação para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7d58c-168">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="7d58c-169">Para obter um exemplo detalhado de como configurar esse comportamento, consulte [comportamento de publicação de metadados](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="7d58c-169">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="7d58c-170">Opcional `httpGetBinding` e `httpsGetBinding` atributos permitem que você configure as ligações usadas para recuperação de metadados via HTTP GET (ou HTTPS GET).</span><span class="sxs-lookup"><span data-stu-id="7d58c-170">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="7d58c-171">Se não forem especificadas, as associações padrão (`HttpTransportBindingElement`, no caso de HTTP e `HttpsTransportBindingElement`, no caso HTTPS) são usados para recuperação de metadados conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="7d58c-171">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="7d58c-172">Observe que você não pode usar esses atributos com associações do WCF internas.</span><span class="sxs-lookup"><span data-stu-id="7d58c-172">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="7d58c-173">Somente associações com elementos de associação interna que suportam <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte.</span><span class="sxs-lookup"><span data-stu-id="7d58c-173">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="7d58c-174">Além disso, o <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d58c-174">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="7d58c-175">Para reduzir a exposição de um serviço a usuários mal-intencionados, é possível proteger a transferência usando o SSL em mecanismo de HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="7d58c-175">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="7d58c-176">Para fazer isso, primeiro você deve ligar um certificado x. 509 apropriado para uma porta específica no computador que hospeda o serviço.</span><span class="sxs-lookup"><span data-stu-id="7d58c-176">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="7d58c-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Em seguida, adicionar esse elemento para a configuração do serviço e defina o `httpsGetEnabled` atributo `true`.</span><span class="sxs-lookup"><span data-stu-id="7d58c-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="7d58c-178">Finalmente, defina o `httpsGetUrl` atributo para a URL do ponto de extremidade de metadados de serviço, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d58c-178">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml
<behaviors>  
  <serviceBehaviors>  
    <behavior name="NewBehavior">  
      <serviceMetadata httpsGetEnabled="true"   
                       httpsGetUrl="https://myComputerName/myEndpoint" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="example"></a><span data-ttu-id="7d58c-179">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d58c-179">Example</span></span>  
 <span data-ttu-id="7d58c-180">O exemplo a seguir configurar um serviço para expor metadados usando o \<serviceMetadata > elemento.</span><span class="sxs-lookup"><span data-stu-id="7d58c-180">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="7d58c-181">Ele também configura um ponto de extremidade para expor o `IMetadataExchange` contrato como uma implementação de um protocolo de WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="7d58c-181">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="7d58c-182">O exemplo usa o `mexHttpBinding`, que é uma conveniência padrão de associação que é equivalente a `wsHttpBinding` com o modo de segurança definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="7d58c-182">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="7d58c-183">Um endereço relativo da "mex" é usado no ponto de extremidade, que, quando resolvido em relação aos serviços base endereço resulta em um endereço de ponto de extremidade de http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="7d58c-183">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService" 
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex   
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d58c-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d58c-184">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="7d58c-185">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="7d58c-185">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7d58c-186">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="7d58c-186">Metadata Publishing Behavior</span></span>](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
