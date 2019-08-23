---
title: <security> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: e627a63221d0013c89495d7ff81e02047a03df89
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936504"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="b9a31-102">\<> de segurança \<de WSHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b9a31-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="b9a31-103">Representa os recursos de segurança do [ \<> de WSHttpBinding](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b9a31-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="b9a31-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b9a31-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b9a31-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b9a31-105">\<bindings></span></span>  
<span data-ttu-id="b9a31-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b9a31-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="b9a31-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="b9a31-107">\<binding></span></span>  
<span data-ttu-id="b9a31-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="b9a31-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a31-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9a31-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9a31-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b9a31-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b9a31-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="b9a31-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9a31-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b9a31-112">Attributes</span></span>  
  
|<span data-ttu-id="b9a31-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b9a31-113">Attribute</span></span>|<span data-ttu-id="b9a31-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9a31-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9a31-115">modo</span><span class="sxs-lookup"><span data-stu-id="b9a31-115">mode</span></span>|<span data-ttu-id="b9a31-116">Adicional.</span><span class="sxs-lookup"><span data-stu-id="b9a31-116">-   Optional.</span></span> <span data-ttu-id="b9a31-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="b9a31-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b9a31-118">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="b9a31-118">The default is `Message`.</span></span><br /><span data-ttu-id="b9a31-119">-Este atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b9a31-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b9a31-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="b9a31-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="b9a31-121">Valor</span><span class="sxs-lookup"><span data-stu-id="b9a31-121">Value</span></span>|<span data-ttu-id="b9a31-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9a31-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b9a31-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b9a31-123">None</span></span>|<span data-ttu-id="b9a31-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="b9a31-124">Security is disabled.</span></span>|  
|<span data-ttu-id="b9a31-125">Porta</span><span class="sxs-lookup"><span data-stu-id="b9a31-125">Transport</span></span>|<span data-ttu-id="b9a31-126">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b9a31-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="b9a31-127">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="b9a31-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="b9a31-128">A mensagem é totalmente protegida usando HTTPS e é autenticada pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="b9a31-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="b9a31-129">A autenticação do cliente é controlada por `ClientCredentials` meio do atributo.</span><span class="sxs-lookup"><span data-stu-id="b9a31-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="b9a31-130">do > de [ transporte.\<](transport-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b9a31-130">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="b9a31-131">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b9a31-131">Message</span></span>|<span data-ttu-id="b9a31-132">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="b9a31-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="b9a31-133">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="b9a31-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="b9a31-134">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio da propriedade Security. Message.</span><span class="sxs-lookup"><span data-stu-id="b9a31-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="b9a31-135">A autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="b9a31-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="b9a31-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="b9a31-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="b9a31-137">Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="b9a31-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="b9a31-138">Por padrão, a autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="b9a31-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9a31-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b9a31-139">Child Elements</span></span>  
  
|<span data-ttu-id="b9a31-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="b9a31-140">Element</span></span>|<span data-ttu-id="b9a31-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9a31-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9a31-142">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="b9a31-142">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="b9a31-143">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="b9a31-143">Defines the transport security settings.</span></span> <span data-ttu-id="b9a31-144">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="b9a31-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="b9a31-145">\<message></span><span class="sxs-lookup"><span data-stu-id="b9a31-145">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="b9a31-146">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="b9a31-146">Defines the security settings for the message.</span></span> <span data-ttu-id="b9a31-147">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="b9a31-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9a31-148">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b9a31-148">Parent Elements</span></span>  
  
|<span data-ttu-id="b9a31-149">Elemento</span><span class="sxs-lookup"><span data-stu-id="b9a31-149">Element</span></span>|<span data-ttu-id="b9a31-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9a31-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9a31-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b9a31-151">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="b9a31-152">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="b9a31-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9a31-153">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9a31-153">Remarks</span></span>  
 <span data-ttu-id="b9a31-154">A classe WSHttpBinding foi projetada para interoperação com serviços que implementam especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="b9a31-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="b9a31-155">A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b9a31-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a31-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9a31-156">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="b9a31-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b9a31-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b9a31-158">Associações</span><span class="sxs-lookup"><span data-stu-id="b9a31-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b9a31-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="b9a31-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b9a31-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b9a31-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b9a31-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="b9a31-161">\<binding></span></span>](../../../misc/binding.md)
