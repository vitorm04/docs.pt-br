---
title: <security> de <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: a895df027bee7430e51e76c480136a49b6b2a0be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936568"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="34832-102">\<> de segurança \<do ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="34832-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="34832-103">Representa as configurações de segurança usadas com o [ \<elemento > ws2007HttpBinding](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="34832-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="34832-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="34832-104">\<system.serviceModel></span></span>  
<span data-ttu-id="34832-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="34832-105">\<bindings></span></span>  
<span data-ttu-id="34832-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="34832-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="34832-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="34832-107">\<binding></span></span>  
<span data-ttu-id="34832-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="34832-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34832-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34832-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34832-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="34832-110">Attributes and Elements</span></span>  
 <span data-ttu-id="34832-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="34832-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34832-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="34832-112">Attributes</span></span>  
  
|<span data-ttu-id="34832-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="34832-113">Attribute</span></span>|<span data-ttu-id="34832-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="34832-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="34832-115">Adicional.</span><span class="sxs-lookup"><span data-stu-id="34832-115">-   Optional.</span></span> <span data-ttu-id="34832-116">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="34832-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="34832-117">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="34832-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="34832-118">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="34832-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="34832-119">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="34832-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="34832-120">Valor</span><span class="sxs-lookup"><span data-stu-id="34832-120">Value</span></span>|<span data-ttu-id="34832-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="34832-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="34832-122">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="34832-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="34832-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="34832-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="34832-124">O serviço deve ser configurado com certificados de protocolo SSL (SSL).</span><span class="sxs-lookup"><span data-stu-id="34832-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="34832-125">A mensagem é totalmente protegida usando HTTPS e o serviço é autenticado pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="34832-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="34832-126">A autenticação do cliente é controlada por `ClientCredentials` meio do atributo [ \<](transport-of-ws2007httpbinding.md) do elemento de > de transporte.</span><span class="sxs-lookup"><span data-stu-id="34832-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="34832-127">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="34832-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="34832-128">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="34832-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="34832-129">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio <xref:System.ServiceModel.Security.SecurityMessageProperty>do.</span><span class="sxs-lookup"><span data-stu-id="34832-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="34832-130">A autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="34832-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="34832-131">Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="34832-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="34832-132">Por padrão, a autenticação do cliente é executada uma vez para cada sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="34832-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34832-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="34832-133">Child Elements</span></span>  
  
|<span data-ttu-id="34832-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="34832-134">Element</span></span>|<span data-ttu-id="34832-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="34832-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34832-136">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="34832-136">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="34832-137">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="34832-137">Defines the transport security settings.</span></span> <span data-ttu-id="34832-138">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="34832-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="34832-139">Essas configurações são aplicadas somente quando o modo é definido como transporte.</span><span class="sxs-lookup"><span data-stu-id="34832-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="34832-140">\<message></span><span class="sxs-lookup"><span data-stu-id="34832-140">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="34832-141">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="34832-141">Defines the security settings for the message.</span></span> <span data-ttu-id="34832-142">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="34832-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="34832-143">Essas configurações não são aplicadas quando o modo é definido como transporte.</span><span class="sxs-lookup"><span data-stu-id="34832-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34832-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="34832-144">Parent Elements</span></span>  
  
|<span data-ttu-id="34832-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="34832-145">Element</span></span>|<span data-ttu-id="34832-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="34832-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34832-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="34832-147">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="34832-148">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="34832-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34832-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="34832-149">Remarks</span></span>  
 <span data-ttu-id="34832-150">Esse elemento foi projetado para interoperação com serviços que implementam especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="34832-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="34832-151">A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="34832-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34832-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34832-152">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="34832-153">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="34832-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="34832-154">Associações</span><span class="sxs-lookup"><span data-stu-id="34832-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="34832-155">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="34832-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="34832-156">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="34832-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="34832-157">\<binding></span><span class="sxs-lookup"><span data-stu-id="34832-157">\<binding></span></span>](../../../misc/binding.md)
