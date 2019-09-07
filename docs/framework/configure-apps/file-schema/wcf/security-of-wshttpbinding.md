---
title: <security> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: f7a4ef98637a7c966665fdd02ad26929bd4ba6ac
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399723"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="81644-102">\<> de segurança \<de WSHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="81644-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="81644-103">Representa os recursos de segurança do [ \<> de WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="81644-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
<span data-ttu-id="81644-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81644-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81644-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="81644-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="81644-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="81644-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="81644-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="81644-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="81644-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="81644-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="81644-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**</span><span class="sxs-lookup"><span data-stu-id="81644-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81644-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81644-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81644-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="81644-111">Attributes and Elements</span></span>  
 <span data-ttu-id="81644-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="81644-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81644-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="81644-113">Attributes</span></span>  
  
|<span data-ttu-id="81644-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="81644-114">Attribute</span></span>|<span data-ttu-id="81644-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="81644-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81644-116">modo</span><span class="sxs-lookup"><span data-stu-id="81644-116">mode</span></span>|<span data-ttu-id="81644-117">Adicional.</span><span class="sxs-lookup"><span data-stu-id="81644-117">-   Optional.</span></span> <span data-ttu-id="81644-118">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="81644-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="81644-119">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="81644-119">The default is `Message`.</span></span><br /><span data-ttu-id="81644-120">-Este atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="81644-120">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="81644-121">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="81644-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="81644-122">Valor</span><span class="sxs-lookup"><span data-stu-id="81644-122">Value</span></span>|<span data-ttu-id="81644-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="81644-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81644-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="81644-124">None</span></span>|<span data-ttu-id="81644-125">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="81644-125">Security is disabled.</span></span>|  
|<span data-ttu-id="81644-126">Porta</span><span class="sxs-lookup"><span data-stu-id="81644-126">Transport</span></span>|<span data-ttu-id="81644-127">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="81644-127">Security is provided using HTTPS.</span></span> <span data-ttu-id="81644-128">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="81644-128">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="81644-129">A mensagem é totalmente protegida usando HTTPS e é autenticada pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="81644-129">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="81644-130">A autenticação do cliente é controlada por `ClientCredentials` meio do atributo.</span><span class="sxs-lookup"><span data-stu-id="81644-130">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="81644-131">do > de [ transporte.\<](transport-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="81644-131">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="81644-132">Mensagem</span><span class="sxs-lookup"><span data-stu-id="81644-132">Message</span></span>|<span data-ttu-id="81644-133">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="81644-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="81644-134">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="81644-134">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="81644-135">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio da propriedade Security. Message.</span><span class="sxs-lookup"><span data-stu-id="81644-135">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="81644-136">A autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="81644-136">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="81644-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="81644-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="81644-138">Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="81644-138">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="81644-139">Por padrão, a autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="81644-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81644-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81644-140">Child Elements</span></span>  
  
|<span data-ttu-id="81644-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="81644-141">Element</span></span>|<span data-ttu-id="81644-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="81644-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81644-143">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="81644-143">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="81644-144">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="81644-144">Defines the transport security settings.</span></span> <span data-ttu-id="81644-145">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="81644-145">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="81644-146">\<message></span><span class="sxs-lookup"><span data-stu-id="81644-146">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="81644-147">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="81644-147">Defines the security settings for the message.</span></span> <span data-ttu-id="81644-148">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="81644-148">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81644-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81644-149">Parent Elements</span></span>  
  
|<span data-ttu-id="81644-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="81644-150">Element</span></span>|<span data-ttu-id="81644-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="81644-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81644-152">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="81644-152">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="81644-153">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="81644-153">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81644-154">Comentários</span><span class="sxs-lookup"><span data-stu-id="81644-154">Remarks</span></span>  
 <span data-ttu-id="81644-155">A classe WSHttpBinding foi projetada para interoperação com serviços que implementam especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="81644-155">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="81644-156">A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="81644-156">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81644-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81644-157">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="81644-158">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="81644-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="81644-159">Associações</span><span class="sxs-lookup"><span data-stu-id="81644-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81644-160">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="81644-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81644-161">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="81644-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="81644-162">\<binding></span><span class="sxs-lookup"><span data-stu-id="81644-162">\<binding></span></span>](../../../misc/binding.md)
