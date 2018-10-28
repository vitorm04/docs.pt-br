---
title: '&lt;security&gt; of &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: f552e12e98e1fd760a9b36f6984a41a32f96533f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192519"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="4311a-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="4311a-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="4311a-103">Representa os recursos de segurança de [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4311a-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="4311a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4311a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4311a-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="4311a-105">\<bindings></span></span>  
<span data-ttu-id="4311a-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4311a-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="4311a-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="4311a-107">\<binding></span></span>  
<span data-ttu-id="4311a-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="4311a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4311a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4311a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4311a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4311a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4311a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="4311a-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4311a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4311a-112">Attributes</span></span>  
  
|<span data-ttu-id="4311a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="4311a-113">Attribute</span></span>|<span data-ttu-id="4311a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4311a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4311a-115">modo</span><span class="sxs-lookup"><span data-stu-id="4311a-115">mode</span></span>|<span data-ttu-id="4311a-116">-Opcional.</span><span class="sxs-lookup"><span data-stu-id="4311a-116">-   Optional.</span></span> <span data-ttu-id="4311a-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="4311a-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="4311a-118">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="4311a-118">The default is `Message`.</span></span><br /><span data-ttu-id="4311a-119">-Este atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="4311a-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4311a-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="4311a-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="4311a-121">Valor</span><span class="sxs-lookup"><span data-stu-id="4311a-121">Value</span></span>|<span data-ttu-id="4311a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="4311a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4311a-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4311a-123">None</span></span>|<span data-ttu-id="4311a-124">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="4311a-124">Security is disabled.</span></span>|  
|<span data-ttu-id="4311a-125">Transporte</span><span class="sxs-lookup"><span data-stu-id="4311a-125">Transport</span></span>|<span data-ttu-id="4311a-126">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4311a-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="4311a-127">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="4311a-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="4311a-128">A mensagem totalmente protegida usando HTTPS e é autenticada pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="4311a-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="4311a-129">A autenticação do cliente é controlada por meio de `ClientCredentials` atributo.</span><span class="sxs-lookup"><span data-stu-id="4311a-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="4311a-130">dos [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4311a-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="4311a-131">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4311a-131">Message</span></span>|<span data-ttu-id="4311a-132">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="4311a-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="4311a-133">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="4311a-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="4311a-134">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e o nível de proteção a ser aplicado ao corpo da mensagem por meio da propriedade Security.Message.</span><span class="sxs-lookup"><span data-stu-id="4311a-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="4311a-135">Autenticação de cliente é executada uma vez por sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.</span><span class="sxs-lookup"><span data-stu-id="4311a-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="4311a-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="4311a-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="4311a-137">Nesse modo, HTTPS fornece integridade, confidencialidade e autenticação de servidor e segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="4311a-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="4311a-138">Por padrão, autenticação de cliente é executada uma vez por sessão e os resultados de autenticação são armazenados em cache para a duração da sessão.</span><span class="sxs-lookup"><span data-stu-id="4311a-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4311a-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4311a-139">Child Elements</span></span>  
  
|<span data-ttu-id="4311a-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="4311a-140">Element</span></span>|<span data-ttu-id="4311a-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="4311a-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4311a-142">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="4311a-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="4311a-143">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="4311a-143">Defines the transport security settings.</span></span> <span data-ttu-id="4311a-144">Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="4311a-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="4311a-145">\<message></span><span class="sxs-lookup"><span data-stu-id="4311a-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="4311a-146">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="4311a-146">Defines the security settings for the message.</span></span> <span data-ttu-id="4311a-147">Esse elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="4311a-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4311a-148">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4311a-148">Parent Elements</span></span>  
  
|<span data-ttu-id="4311a-149">Elemento</span><span class="sxs-lookup"><span data-stu-id="4311a-149">Element</span></span>|<span data-ttu-id="4311a-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="4311a-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4311a-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4311a-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="4311a-152">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="4311a-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4311a-153">Comentários</span><span class="sxs-lookup"><span data-stu-id="4311a-153">Remarks</span></span>  
 <span data-ttu-id="4311a-154">A classe de WSHttpBinding é projetada para interoperação com serviços que implementam o WS-\* especificações.</span><span class="sxs-lookup"><span data-stu-id="4311a-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="4311a-155">A segurança de transporte para essa associação é Secure Sockets Layer (SSL) via HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4311a-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4311a-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4311a-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="4311a-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4311a-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="4311a-158">Associações</span><span class="sxs-lookup"><span data-stu-id="4311a-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4311a-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="4311a-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="4311a-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4311a-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="4311a-161">\<associação ></span><span class="sxs-lookup"><span data-stu-id="4311a-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
