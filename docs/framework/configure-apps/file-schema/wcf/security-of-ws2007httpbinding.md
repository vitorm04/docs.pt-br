---
title: <security> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736396"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="dd4c6-102">\<> de segurança do \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="dd4c6-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="dd4c6-103">Representa as configurações de segurança usadas com o elemento [\<ws2007HttpBinding >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dd4c6-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="dd4c6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dd4c6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dd4c6-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="dd4c6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dd4c6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="dd4c6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="dd4c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dd4c6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="dd4c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="dd4c6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="dd4c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**</span><span class="sxs-lookup"><span data-stu-id="dd4c6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd4c6-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd4c6-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd4c6-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dd4c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dd4c6-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd4c6-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="dd4c6-113">Attributes</span></span>  
  
|<span data-ttu-id="dd4c6-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="dd4c6-114">Attribute</span></span>|<span data-ttu-id="dd4c6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd4c6-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="dd4c6-116">Adicional.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-116">-   Optional.</span></span> <span data-ttu-id="dd4c6-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="dd4c6-118">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="dd4c6-119">Este atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="dd4c6-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="dd4c6-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="dd4c6-121">Valor</span><span class="sxs-lookup"><span data-stu-id="dd4c6-121">Value</span></span>|<span data-ttu-id="dd4c6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd4c6-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="dd4c6-123">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="dd4c6-124">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="dd4c6-125">O serviço deve ser configurado com certificados de protocolo SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="dd4c6-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="dd4c6-126">A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="dd4c6-127">A autenticação do cliente é controlada por meio do atributo `ClientCredentials` do elemento [> de transporte\<](transport-of-ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dd4c6-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="dd4c6-128">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="dd4c6-129">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="dd4c6-130">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio do <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="dd4c6-131">A autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="dd4c6-132">Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="dd4c6-133">Por padrão, a autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd4c6-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dd4c6-134">Child Elements</span></span>  
  
|<span data-ttu-id="dd4c6-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd4c6-135">Element</span></span>|<span data-ttu-id="dd4c6-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd4c6-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd4c6-137">> de transporte de \<</span><span class="sxs-lookup"><span data-stu-id="dd4c6-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="dd4c6-138">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-138">Defines the transport security settings.</span></span> <span data-ttu-id="dd4c6-139">Esse elemento corresponde ao tipo de <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="dd4c6-140">Essas configurações são aplicadas somente quando o modo é definido como transporte.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="dd4c6-141">\<message ></span><span class="sxs-lookup"><span data-stu-id="dd4c6-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="dd4c6-142">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-142">Defines the security settings for the message.</span></span> <span data-ttu-id="dd4c6-143">Esse elemento corresponde ao tipo de <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="dd4c6-144">Essas configurações não são aplicadas quando o modo é definido como transporte.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd4c6-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dd4c6-145">Parent Elements</span></span>  
  
|<span data-ttu-id="dd4c6-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="dd4c6-146">Element</span></span>|<span data-ttu-id="dd4c6-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd4c6-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd4c6-148">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="dd4c6-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="dd4c6-149">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd4c6-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd4c6-150">Remarks</span></span>  
 <span data-ttu-id="dd4c6-151">Esse elemento foi projetado para interoperação com serviços que implementam especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="dd4c6-152">A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="dd4c6-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd4c6-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd4c6-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="dd4c6-154">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="dd4c6-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dd4c6-155">Associações</span><span class="sxs-lookup"><span data-stu-id="dd4c6-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dd4c6-156">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="dd4c6-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dd4c6-157">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="dd4c6-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dd4c6-158">\<binding ></span><span class="sxs-lookup"><span data-stu-id="dd4c6-158">\<binding></span></span>](bindings.md)
