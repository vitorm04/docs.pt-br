---
title: '&lt;security&gt; of &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 836e920ef7c95d4a7a2b752c2f76f29d8c880e7c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="ca215-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ca215-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="ca215-103">Representa os recursos de segurança de [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ca215-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="ca215-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ca215-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ca215-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="ca215-105">\<bindings></span></span>  
<span data-ttu-id="ca215-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ca215-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="ca215-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ca215-107">\<binding></span></span>  
<span data-ttu-id="ca215-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="ca215-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca215-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca215-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">  
   <transport  
         clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string"   
      defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      defaultRealm="string" />  
   <message  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
       establishSecurityContext="Boolean"   
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca215-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ca215-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ca215-111">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca215-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca215-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca215-112">Attributes</span></span>  
  
|<span data-ttu-id="ca215-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ca215-113">Attribute</span></span>|<span data-ttu-id="ca215-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca215-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ca215-115">modo</span><span class="sxs-lookup"><span data-stu-id="ca215-115">mode</span></span>|<span data-ttu-id="ca215-116">-Opcional.</span><span class="sxs-lookup"><span data-stu-id="ca215-116">-   Optional.</span></span> <span data-ttu-id="ca215-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="ca215-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="ca215-118">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="ca215-118">The default is `Message`.</span></span><br /><span data-ttu-id="ca215-119">-Este atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ca215-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ca215-120">Atributo mode</span><span class="sxs-lookup"><span data-stu-id="ca215-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="ca215-121">Valor</span><span class="sxs-lookup"><span data-stu-id="ca215-121">Value</span></span>|<span data-ttu-id="ca215-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca215-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ca215-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ca215-123">None</span></span>|<span data-ttu-id="ca215-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="ca215-124">Security is disabled.</span></span>|  
|<span data-ttu-id="ca215-125">Transporte</span><span class="sxs-lookup"><span data-stu-id="ca215-125">Transport</span></span>|<span data-ttu-id="ca215-126">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ca215-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="ca215-127">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="ca215-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="ca215-128">A mensagem é totalmente protegida usando HTTPS e é autenticada pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="ca215-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="ca215-129">A autenticação do cliente é controlada por meio de `ClientCredentials` atributo.</span><span class="sxs-lookup"><span data-stu-id="ca215-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="ca215-130">do [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ca215-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="ca215-131">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ca215-131">Message</span></span>|<span data-ttu-id="ca215-132">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="ca215-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="ca215-133">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="ca215-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="ca215-134">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o conjunto de algoritmos para usar e o nível de proteção para aplicar ao corpo da mensagem por meio da propriedade Security.Message.</span><span class="sxs-lookup"><span data-stu-id="ca215-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="ca215-135">Autenticação de cliente é executada uma vez por sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.</span><span class="sxs-lookup"><span data-stu-id="ca215-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="ca215-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="ca215-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="ca215-137">Nesse modo, HTTPS fornece autenticação de servidor, integridade e confidencialidade e segurança de mensagens SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="ca215-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="ca215-138">Por padrão, autenticação de cliente é executada uma vez por sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.</span><span class="sxs-lookup"><span data-stu-id="ca215-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca215-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca215-139">Child Elements</span></span>  
  
|<span data-ttu-id="ca215-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca215-140">Element</span></span>|<span data-ttu-id="ca215-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca215-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca215-142">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="ca215-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="ca215-143">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="ca215-143">Defines the transport security settings.</span></span> <span data-ttu-id="ca215-144">Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="ca215-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="ca215-145">\<message></span><span class="sxs-lookup"><span data-stu-id="ca215-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="ca215-146">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="ca215-146">Defines the security settings for the message.</span></span> <span data-ttu-id="ca215-147">Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="ca215-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca215-148">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca215-148">Parent Elements</span></span>  
  
|<span data-ttu-id="ca215-149">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca215-149">Element</span></span>|<span data-ttu-id="ca215-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca215-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca215-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ca215-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="ca215-152">Uma associação de segurança para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="ca215-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca215-153">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca215-153">Remarks</span></span>  
 <span data-ttu-id="ca215-154">A classe WSHttpBinding destina-se a interoperação com os serviços que implementam o WS-\* especificações.</span><span class="sxs-lookup"><span data-stu-id="ca215-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="ca215-155">A segurança de transporte para essa associação é o protocolo (SSL) via HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ca215-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca215-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca215-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="ca215-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ca215-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ca215-158">Associações</span><span class="sxs-lookup"><span data-stu-id="ca215-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ca215-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ca215-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ca215-160">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ca215-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ca215-161">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ca215-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
