---
title: '&lt;segurança&gt; de &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: fb92e7549b86a2c4a4a8453d13f6c4f08d696348
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129773"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="d930f-102">&lt;segurança&gt; de &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d930f-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="d930f-103">Representa as configurações de segurança usadas com o [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d930f-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="d930f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d930f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d930f-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="d930f-105">\<bindings></span></span>  
<span data-ttu-id="d930f-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="d930f-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="d930f-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d930f-107">\<binding></span></span>  
<span data-ttu-id="d930f-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="d930f-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d930f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d930f-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d930f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d930f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d930f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d930f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d930f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d930f-112">Attributes</span></span>  
  
|<span data-ttu-id="d930f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d930f-113">Attribute</span></span>|<span data-ttu-id="d930f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d930f-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d930f-115">-Opcional.</span><span class="sxs-lookup"><span data-stu-id="d930f-115">-   Optional.</span></span> <span data-ttu-id="d930f-116">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="d930f-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d930f-117">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="d930f-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="d930f-118">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d930f-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d930f-119">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="d930f-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="d930f-120">Valor</span><span class="sxs-lookup"><span data-stu-id="d930f-120">Value</span></span>|<span data-ttu-id="d930f-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d930f-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="d930f-122">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="d930f-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="d930f-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d930f-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="d930f-124">O serviço deve ser configurado com certificados Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="d930f-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="d930f-125">A mensagem é totalmente protegida usando o HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="d930f-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="d930f-126">A autenticação do cliente é controlada por meio de `ClientCredentials` atributo do [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d930f-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="d930f-127">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="d930f-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="d930f-128">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="d930f-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="d930f-129">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e o nível de proteção a ser aplicado ao corpo da mensagem por meio de <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="d930f-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="d930f-130">Autenticação de cliente é executada uma vez para cada sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.</span><span class="sxs-lookup"><span data-stu-id="d930f-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="d930f-131">Nesse modo, HTTPS fornece integridade, confidencialidade e autenticação de servidor e segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="d930f-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="d930f-132">Por padrão, autenticação de cliente é executada uma vez para cada sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.</span><span class="sxs-lookup"><span data-stu-id="d930f-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d930f-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d930f-133">Child Elements</span></span>  
  
|<span data-ttu-id="d930f-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="d930f-134">Element</span></span>|<span data-ttu-id="d930f-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="d930f-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d930f-136">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="d930f-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="d930f-137">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="d930f-137">Defines the transport security settings.</span></span> <span data-ttu-id="d930f-138">Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="d930f-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="d930f-139">Essas configurações são aplicadas somente quando o modo é definido como o transporte.</span><span class="sxs-lookup"><span data-stu-id="d930f-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="d930f-140">\<message></span><span class="sxs-lookup"><span data-stu-id="d930f-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="d930f-141">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="d930f-141">Defines the security settings for the message.</span></span> <span data-ttu-id="d930f-142">Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="d930f-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="d930f-143">Essas configurações não são aplicadas quando o modo é definido como o transporte.</span><span class="sxs-lookup"><span data-stu-id="d930f-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d930f-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d930f-144">Parent Elements</span></span>  
  
|<span data-ttu-id="d930f-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="d930f-145">Element</span></span>|<span data-ttu-id="d930f-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="d930f-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d930f-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="d930f-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="d930f-148">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="d930f-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d930f-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="d930f-149">Remarks</span></span>  
 <span data-ttu-id="d930f-150">Esse elemento foi projetado para interoperação com serviços que implementam o WS-\* especificações.</span><span class="sxs-lookup"><span data-stu-id="d930f-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="d930f-151">A segurança de transporte para essa associação é Secure Sockets Layer (SSL) via HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d930f-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d930f-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d930f-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="d930f-153">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d930f-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d930f-154">Associações</span><span class="sxs-lookup"><span data-stu-id="d930f-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d930f-155">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="d930f-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d930f-156">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d930f-156">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="d930f-157">\<associação ></span><span class="sxs-lookup"><span data-stu-id="d930f-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
