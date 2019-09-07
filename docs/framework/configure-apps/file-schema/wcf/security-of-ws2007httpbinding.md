---
title: <security> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ab5969da6a2d7cb59c057fd5bb909add6b6398a4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399780"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="72d98-102">\<> de segurança \<do ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="72d98-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="72d98-103">Representa as configurações de segurança usadas com o [ \<elemento > ws2007HttpBinding](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="72d98-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="72d98-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="72d98-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="72d98-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="72d98-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="72d98-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="72d98-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="72d98-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ws2007HttpBinding**](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="72d98-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="72d98-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="72d98-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="72d98-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**</span><span class="sxs-lookup"><span data-stu-id="72d98-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72d98-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72d98-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72d98-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="72d98-111">Attributes and Elements</span></span>  
 <span data-ttu-id="72d98-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="72d98-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72d98-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="72d98-113">Attributes</span></span>  
  
|<span data-ttu-id="72d98-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="72d98-114">Attribute</span></span>|<span data-ttu-id="72d98-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="72d98-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="72d98-116">Adicional.</span><span class="sxs-lookup"><span data-stu-id="72d98-116">-   Optional.</span></span> <span data-ttu-id="72d98-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="72d98-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="72d98-118">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="72d98-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="72d98-119">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="72d98-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="72d98-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="72d98-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="72d98-121">Valor</span><span class="sxs-lookup"><span data-stu-id="72d98-121">Value</span></span>|<span data-ttu-id="72d98-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="72d98-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="72d98-123">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="72d98-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="72d98-124">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="72d98-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="72d98-125">O serviço deve ser configurado com certificados de protocolo SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="72d98-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="72d98-126">A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="72d98-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="72d98-127">A autenticação do cliente é controlada por `ClientCredentials` meio do atributo [ \<](transport-of-ws2007httpbinding.md) do elemento de > de transporte.</span><span class="sxs-lookup"><span data-stu-id="72d98-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="72d98-128">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="72d98-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="72d98-129">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="72d98-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="72d98-130">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio <xref:System.ServiceModel.Security.SecurityMessageProperty>do.</span><span class="sxs-lookup"><span data-stu-id="72d98-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="72d98-131">A autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="72d98-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="72d98-132">Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="72d98-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="72d98-133">Por padrão, a autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="72d98-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72d98-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="72d98-134">Child Elements</span></span>  
  
|<span data-ttu-id="72d98-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="72d98-135">Element</span></span>|<span data-ttu-id="72d98-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="72d98-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72d98-137">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="72d98-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="72d98-138">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="72d98-138">Defines the transport security settings.</span></span> <span data-ttu-id="72d98-139">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="72d98-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="72d98-140">Essas configurações são aplicadas somente quando o modo é definido como transporte.</span><span class="sxs-lookup"><span data-stu-id="72d98-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="72d98-141">\<message></span><span class="sxs-lookup"><span data-stu-id="72d98-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="72d98-142">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="72d98-142">Defines the security settings for the message.</span></span> <span data-ttu-id="72d98-143">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="72d98-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="72d98-144">Essas configurações não são aplicadas quando o modo é definido como transporte.</span><span class="sxs-lookup"><span data-stu-id="72d98-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72d98-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="72d98-145">Parent Elements</span></span>  
  
|<span data-ttu-id="72d98-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="72d98-146">Element</span></span>|<span data-ttu-id="72d98-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="72d98-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72d98-148">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="72d98-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="72d98-149">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="72d98-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72d98-150">Comentários</span><span class="sxs-lookup"><span data-stu-id="72d98-150">Remarks</span></span>  
 <span data-ttu-id="72d98-151">Esse elemento foi projetado para interoperação com serviços que implementam especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="72d98-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="72d98-152">A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="72d98-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d98-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72d98-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="72d98-154">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="72d98-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="72d98-155">Associações</span><span class="sxs-lookup"><span data-stu-id="72d98-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="72d98-156">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="72d98-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="72d98-157">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="72d98-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="72d98-158">\<binding></span><span class="sxs-lookup"><span data-stu-id="72d98-158">\<binding></span></span>](../../../misc/binding.md)
