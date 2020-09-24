---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 2236361316254d065abd1fb62fd2e509be289a4c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153853"
---
# \<serviceMetadata>

<span data-ttu-id="c01e5-101">Especifica a publicação de metadados de serviço e informações associadas.</span><span class="sxs-lookup"><span data-stu-id="c01e5-101">Specifies the publication of service metadata and associated information.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="c01e5-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="c01e5-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c01e5-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c01e5-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c01e5-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c01e5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c01e5-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="c01e5-105">Attributes</span></span>  
  
|<span data-ttu-id="c01e5-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="c01e5-106">Attribute</span></span>|<span data-ttu-id="c01e5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c01e5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c01e5-108">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="c01e5-108">externalMetadataLocation</span></span>|<span data-ttu-id="c01e5-109">Um URI que contém o local de um arquivo WSDL, que é retornado ao usuário em resposta às solicitações WSDL e MEX em vez do WSDL gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c01e5-109">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="c01e5-110">Quando esse atributo não é definido, o WSDL padrão é retornado.</span><span class="sxs-lookup"><span data-stu-id="c01e5-110">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="c01e5-111">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="c01e5-111">The default is an empty string.</span></span>|  
|<span data-ttu-id="c01e5-112">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="c01e5-112">httpGetBinding</span></span>|<span data-ttu-id="c01e5-113">Uma cadeia de caracteres que especifica o tipo de associação que será usado para recuperação de metadados via HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="c01e5-113">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="c01e5-114">Essa configuração é opcional.</span><span class="sxs-lookup"><span data-stu-id="c01e5-114">This setting is optional.</span></span> <span data-ttu-id="c01e5-115">Se não for especificado, as associações padrão serão usadas.</span><span class="sxs-lookup"><span data-stu-id="c01e5-115">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="c01e5-116">Somente associações com elementos de associação interna com suporte <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte.</span><span class="sxs-lookup"><span data-stu-id="c01e5-116">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="c01e5-117">Além disso, a <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="c01e5-117">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="c01e5-118">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c01e5-118">httpGetBindingConfiguration</span></span>|<span data-ttu-id="c01e5-119">Uma cadeia de caracteres que define o nome da associação que é especificada no `httpGetBinding` atributo, que faz referência às informações de configuração adicionais dessa associação.</span><span class="sxs-lookup"><span data-stu-id="c01e5-119">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="c01e5-120">O mesmo nome deve ser definido na `<bindings>` seção.</span><span class="sxs-lookup"><span data-stu-id="c01e5-120">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="c01e5-121">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="c01e5-121">httpGetEnabled</span></span>|<span data-ttu-id="c01e5-122">Um valor booliano que especifica se os metadados de serviço devem ser publicados para recuperação usando uma solicitação HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="c01e5-122">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="c01e5-123">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c01e5-123">The default is `false`.</span></span><br /><br /> <span data-ttu-id="c01e5-124">Se o atributo httpGetUrl não for especificado, o endereço no qual os metadados são publicados será o endereço de serviço mais um "? WSDL".</span><span class="sxs-lookup"><span data-stu-id="c01e5-124">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="c01e5-125">Por exemplo, se o endereço do serviço for `http://localhost:8080/CalculatorService` , o endereço de metadados http/Get será `http://localhost:8080/CalculatorService?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="c01e5-125">For example, if the service address is `http://localhost:8080/CalculatorService`, the HTTP/Get metadata address is `http://localhost:8080/CalculatorService?wsdl`.</span></span><br /><br /> <span data-ttu-id="c01e5-126">Se essa propriedade for `false` , ou o endereço do serviço não for baseado em http ou HTTPS, "? WSDL" será ignorado.</span><span class="sxs-lookup"><span data-stu-id="c01e5-126">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="c01e5-127">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="c01e5-127">httpGetUrl</span></span>|<span data-ttu-id="c01e5-128">Um URI que especifica o endereço no qual os metadados são publicados para recuperação usando uma solicitação HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="c01e5-128">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="c01e5-129">Se um URI relativo for especificado, ele será tratado como relativo ao endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="c01e5-129">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="c01e5-130">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="c01e5-130">httpsGetBinding</span></span>|<span data-ttu-id="c01e5-131">Uma cadeia de caracteres que especifica o tipo de associação que será usado para recuperação de metadados via HTTPS GET.</span><span class="sxs-lookup"><span data-stu-id="c01e5-131">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="c01e5-132">Essa configuração é opcional.</span><span class="sxs-lookup"><span data-stu-id="c01e5-132">This setting is optional.</span></span> <span data-ttu-id="c01e5-133">Se não for especificado, as associações padrão serão usadas.</span><span class="sxs-lookup"><span data-stu-id="c01e5-133">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="c01e5-134">Somente associações com elementos de associação interna com suporte <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte.</span><span class="sxs-lookup"><span data-stu-id="c01e5-134">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="c01e5-135">Além disso, a <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="c01e5-135">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="c01e5-136">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c01e5-136">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="c01e5-137">Uma cadeia de caracteres que define o nome da associação que é especificada no `httpsGetBinding` atributo, que faz referência às informações de configuração adicionais dessa associação.</span><span class="sxs-lookup"><span data-stu-id="c01e5-137">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="c01e5-138">O mesmo nome deve ser definido na `<bindings>` seção.</span><span class="sxs-lookup"><span data-stu-id="c01e5-138">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="c01e5-139">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="c01e5-139">httpsGetEnabled</span></span>|<span data-ttu-id="c01e5-140">Um valor booliano que especifica se os metadados de serviço devem ser publicados para recuperação usando uma solicitação HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="c01e5-140">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="c01e5-141">O padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="c01e5-141">The default is `false`.</span></span><br /><br /> <span data-ttu-id="c01e5-142">Se o atributo httpsGetUrl não for especificado, o endereço no qual os metadados são publicados será o endereço de serviço mais um "? WSDL".</span><span class="sxs-lookup"><span data-stu-id="c01e5-142">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="c01e5-143">Por exemplo, se o endereço do serviço for " https://localhost:8080/CalculatorService ", o endereço de metadados http/Get será " https://localhost:8080/CalculatorService?wsdl ".</span><span class="sxs-lookup"><span data-stu-id="c01e5-143">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="c01e5-144">Se essa propriedade for `false` , ou o endereço do serviço não for baseado em http ou HTTPS, "? WSDL" será ignorado.</span><span class="sxs-lookup"><span data-stu-id="c01e5-144">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="c01e5-145">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="c01e5-145">httpsGetUrl</span></span>|<span data-ttu-id="c01e5-146">Um URI que especifica o endereço no qual os metadados são publicados para recuperação usando uma solicitação HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="c01e5-146">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="c01e5-147">policyVersion</span><span class="sxs-lookup"><span data-stu-id="c01e5-147">policyVersion</span></span>|<span data-ttu-id="c01e5-148">Uma cadeia de caracteres que especifica a versão da especificação de WS-Policy que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="c01e5-148">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="c01e5-149">Esse atributo é do tipo <xref:System.ServiceModel.Description.PolicyVersion> .</span><span class="sxs-lookup"><span data-stu-id="c01e5-149">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c01e5-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c01e5-150">Child Elements</span></span>  

 <span data-ttu-id="c01e5-151">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c01e5-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c01e5-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c01e5-152">Parent Elements</span></span>  
  
|<span data-ttu-id="c01e5-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="c01e5-153">Element</span></span>|<span data-ttu-id="c01e5-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="c01e5-154">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c01e5-155">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="c01e5-155">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c01e5-156">Comentários</span><span class="sxs-lookup"><span data-stu-id="c01e5-156">Remarks</span></span>  

 <span data-ttu-id="c01e5-157">Este elemento de configuração permite que você controle os recursos de publicação de metadados de um serviço.</span><span class="sxs-lookup"><span data-stu-id="c01e5-157">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="c01e5-158">Para evitar a divulgação não intencional de metadados de serviço potencialmente confidenciais, a configuração padrão para Windows Communication Foundation (WCF) Services desabilita a publicação de metadados.</span><span class="sxs-lookup"><span data-stu-id="c01e5-158">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="c01e5-159">Esse comportamento é seguro por padrão, mas também significa que você não pode usar uma ferramenta de importação de metadados (como Svcutil.exe) para gerar o código do cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço esteja explicitamente habilitado na configuração.</span><span class="sxs-lookup"><span data-stu-id="c01e5-159">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="c01e5-160">Usando esse elemento de configuração, você pode habilitar esse comportamento de publicação para seu serviço.</span><span class="sxs-lookup"><span data-stu-id="c01e5-160">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="c01e5-161">Para obter um exemplo detalhado de como configurar esse comportamento, consulte [comportamento de publicação de metadados](../../../wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="c01e5-161">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="c01e5-162">Os `httpGetBinding` atributos e opcionais `httpsGetBinding` permitem configurar as associações usadas para recuperação de metadados via HTTP Get (ou HTTPS Get).</span><span class="sxs-lookup"><span data-stu-id="c01e5-162">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="c01e5-163">Se não forem especificadas, as associações padrão ( `HttpTransportBindingElement` , no caso de http e `HttpsTransportBindingElement` , no caso de HTTPS) serão usadas para recuperação de metadados, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="c01e5-163">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="c01e5-164">Observe que você não pode usar esses atributos com as associações internas do WCF.</span><span class="sxs-lookup"><span data-stu-id="c01e5-164">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="c01e5-165">Somente associações com elementos de associação interna com suporte <xref:System.ServiceModel.Channels.IReplyChannel> terão suporte.</span><span class="sxs-lookup"><span data-stu-id="c01e5-165">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="c01e5-166">Além disso, a <xref:System.ServiceModel.Channels.MessageVersion> propriedade da associação deve ser <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="c01e5-166">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="c01e5-167">Para reduzir a exposição de um serviço a usuários mal-intencionados, é possível proteger a transferência usando o mecanismo SSL sobre HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="c01e5-167">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="c01e5-168">Para fazer isso, primeiro você deve associar um certificado X. 509 adequado a uma porta específica no computador que está hospedando o serviço.</span><span class="sxs-lookup"><span data-stu-id="c01e5-168">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="c01e5-169">(Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).) Em segundo lugar, adicione esse elemento à configuração do serviço e defina o `httpsGetEnabled` atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="c01e5-169">(For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="c01e5-170">Por fim, defina o `httpsGetUrl` atributo como a URL do ponto de extremidade de metadados de serviço, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c01e5-170">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c01e5-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c01e5-171">Example</span></span>  

 <span data-ttu-id="c01e5-172">O exemplo a seguir configura um serviço para expor metadados usando o \<serviceMetadata> elemento.</span><span class="sxs-lookup"><span data-stu-id="c01e5-172">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="c01e5-173">Ele também configura um ponto de extremidade para expor o `IMetadataExchange` contrato como uma implementação de um protocolo de WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="c01e5-173">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="c01e5-174">O exemplo usa o `mexHttpBinding` , que é uma associação padrão de conveniência equivalente ao `wsHttpBinding` com o modo de segurança definido como `None` .</span><span class="sxs-lookup"><span data-stu-id="c01e5-174">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="c01e5-175">Um endereço relativo de "MEX" é usado no ponto de extremidade, que, quando resolvido em relação ao endereço base de serviços, resulta em um endereço de ponto de extremidade de `http://localhost/servicemodelsamples/service.svc/mex` .</span><span class="sxs-lookup"><span data-stu-id="c01e5-175">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span>  
  
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
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="c01e5-176">Confira também</span><span class="sxs-lookup"><span data-stu-id="c01e5-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="c01e5-177">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="c01e5-177">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c01e5-178">Comportamento de publicação de metadados</span><span class="sxs-lookup"><span data-stu-id="c01e5-178">Metadata Publishing Behavior</span></span>](../../../wcf/samples/metadata-publishing-behavior.md)
