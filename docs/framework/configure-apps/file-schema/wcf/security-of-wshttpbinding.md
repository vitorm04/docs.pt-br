---
title: <security> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738586"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="4efb4-102">\<> de segurança do \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="4efb4-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="4efb4-103">Representa os recursos de segurança do [\<wsHttpBinding >](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4efb4-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
<span data-ttu-id="4efb4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4efb4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4efb4-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="4efb4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4efb4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="4efb4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4efb4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4efb4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="4efb4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="4efb4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4efb4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**</span><span class="sxs-lookup"><span data-stu-id="4efb4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4efb4-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4efb4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4efb4-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4efb4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4efb4-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="4efb4-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4efb4-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="4efb4-113">Attributes</span></span>  
  
|<span data-ttu-id="4efb4-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="4efb4-114">Attribute</span></span>|<span data-ttu-id="4efb4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efb4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4efb4-116">modo</span><span class="sxs-lookup"><span data-stu-id="4efb4-116">mode</span></span>|<span data-ttu-id="4efb4-117">Adicional.</span><span class="sxs-lookup"><span data-stu-id="4efb4-117">-   Optional.</span></span> <span data-ttu-id="4efb4-118">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="4efb4-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="4efb4-119">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="4efb4-119">The default is `Message`.</span></span><br /><span data-ttu-id="4efb4-120">-Este atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="4efb4-120">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4efb4-121">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="4efb4-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="4efb4-122">Valor</span><span class="sxs-lookup"><span data-stu-id="4efb4-122">Value</span></span>|<span data-ttu-id="4efb4-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efb4-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4efb4-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4efb4-124">None</span></span>|<span data-ttu-id="4efb4-125">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="4efb4-125">Security is disabled.</span></span>|  
|<span data-ttu-id="4efb4-126">Porta</span><span class="sxs-lookup"><span data-stu-id="4efb4-126">Transport</span></span>|<span data-ttu-id="4efb4-127">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4efb4-127">Security is provided using HTTPS.</span></span> <span data-ttu-id="4efb4-128">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="4efb4-128">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="4efb4-129">A mensagem é totalmente protegida usando HTTPS e é autenticada pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="4efb4-129">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="4efb4-130">A autenticação do cliente é controlada por meio do atributo `ClientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="4efb4-130">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="4efb4-131">do [> de transporte\<](transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4efb4-131">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="4efb4-132">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4efb4-132">Message</span></span>|<span data-ttu-id="4efb4-133">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="4efb4-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="4efb4-134">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="4efb4-134">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="4efb4-135">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio da propriedade Security. Message.</span><span class="sxs-lookup"><span data-stu-id="4efb4-135">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="4efb4-136">A autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="4efb4-136">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="4efb4-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="4efb4-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="4efb4-138">Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="4efb4-138">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="4efb4-139">Por padrão, a autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="4efb4-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4efb4-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4efb4-140">Child Elements</span></span>  
  
|<span data-ttu-id="4efb4-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="4efb4-141">Element</span></span>|<span data-ttu-id="4efb4-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efb4-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4efb4-143">> de transporte de \<</span><span class="sxs-lookup"><span data-stu-id="4efb4-143">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="4efb4-144">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="4efb4-144">Defines the transport security settings.</span></span> <span data-ttu-id="4efb4-145">Esse elemento corresponde ao tipo de <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4efb4-145">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="4efb4-146">\<message ></span><span class="sxs-lookup"><span data-stu-id="4efb4-146">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="4efb4-147">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="4efb4-147">Defines the security settings for the message.</span></span> <span data-ttu-id="4efb4-148">Esse elemento corresponde ao tipo de <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="4efb4-148">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4efb4-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4efb4-149">Parent Elements</span></span>  
  
|<span data-ttu-id="4efb4-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="4efb4-150">Element</span></span>|<span data-ttu-id="4efb4-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efb4-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4efb4-152">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4efb4-152">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="4efb4-153">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="4efb4-153">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4efb4-154">Comentários</span><span class="sxs-lookup"><span data-stu-id="4efb4-154">Remarks</span></span>  
 <span data-ttu-id="4efb4-155">A classe WSHttpBinding foi projetada para interoperação com serviços que implementam especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="4efb4-155">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="4efb4-156">A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4efb4-156">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4efb4-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4efb4-157">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="4efb4-158">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4efb4-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4efb4-159">Associações</span><span class="sxs-lookup"><span data-stu-id="4efb4-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4efb4-160">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="4efb4-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4efb4-161">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4efb4-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4efb4-162">\<binding ></span><span class="sxs-lookup"><span data-stu-id="4efb4-162">\<binding></span></span>](bindings.md)
