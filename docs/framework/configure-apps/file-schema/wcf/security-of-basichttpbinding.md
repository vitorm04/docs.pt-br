---
title: "&lt;segurança&gt; de &lt;basicHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 8d61075bc96427736f7e6f5a39302bbd59d434f9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="a4b72-102">&lt;segurança&gt; de &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a4b72-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="a4b72-103">Define os recursos de segurança de [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a4b72-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="a4b72-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a4b72-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4b72-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a4b72-105">\<bindings></span></span>  
<span data-ttu-id="a4b72-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a4b72-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="a4b72-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="a4b72-107">\<binding></span></span>  
<span data-ttu-id="a4b72-108">\<security></span><span class="sxs-lookup"><span data-stu-id="a4b72-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b72-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4b72-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4b72-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a4b72-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a4b72-111">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="a4b72-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4b72-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a4b72-112">Attributes</span></span>  
  
|<span data-ttu-id="a4b72-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a4b72-113">Attribute</span></span>|<span data-ttu-id="a4b72-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4b72-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4b72-115">modo</span><span class="sxs-lookup"><span data-stu-id="a4b72-115">mode</span></span>|<span data-ttu-id="a4b72-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a4b72-116">Optional.</span></span> <span data-ttu-id="a4b72-117">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="a4b72-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="a4b72-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="a4b72-118">The default is `None`.</span></span> <span data-ttu-id="a4b72-119">Esse atributo é do tipo <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a4b72-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a4b72-120">Atributo mode</span><span class="sxs-lookup"><span data-stu-id="a4b72-120">mode Attribute</span></span>  
  
|<span data-ttu-id="a4b72-121">Valor</span><span class="sxs-lookup"><span data-stu-id="a4b72-121">Value</span></span>|<span data-ttu-id="a4b72-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4b72-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4b72-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a4b72-123">None</span></span>|<span data-ttu-id="a4b72-124">-Mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="a4b72-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="a4b72-125">Transporte</span><span class="sxs-lookup"><span data-stu-id="a4b72-125">Transport</span></span>|<span data-ttu-id="a4b72-126">A segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a4b72-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="a4b72-127">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a4b72-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="a4b72-128">O serviço é autenticado para o cliente usando o certificado de x. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="a4b72-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="a4b72-129">O cliente é autenticado usando ClientCredentialType fornecido.</span><span class="sxs-lookup"><span data-stu-id="a4b72-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="a4b72-130">Consulte o [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a4b72-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="a4b72-131">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a4b72-131">Message</span></span>|<span data-ttu-id="a4b72-132">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="a4b72-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="a4b72-133">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="a4b72-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="a4b72-134">Para essa associação, o sistema requer que o certificado do servidor para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="a4b72-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="a4b72-135">Válido somente `ClientCredentialType` para essa associação é `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="a4b72-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="a4b72-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a4b72-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="a4b72-137">Autenticação de integridade, confidencialidade e servidor são fornecidos pela segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="a4b72-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="a4b72-138">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="a4b72-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="a4b72-139">Esse modo é relevante quando o usuário estiver autenticando usando o nome de usuário/senha e há uma implantação existente de HTTP para transferência segura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a4b72-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="a4b72-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="a4b72-140">TransportCredentialOnly</span></span>|<span data-ttu-id="a4b72-141">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a4b72-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="a4b72-142">Ele fornece autenticação de cliente com base em http.</span><span class="sxs-lookup"><span data-stu-id="a4b72-142">It provides http-based client authentication.</span></span> <span data-ttu-id="a4b72-143">Esse modo deve ser usado com cuidado.</span><span class="sxs-lookup"><span data-stu-id="a4b72-143">This mode should be used with caution.</span></span> <span data-ttu-id="a4b72-144">Ele deve ser usado em ambientes onde a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="a4b72-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4b72-145">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a4b72-145">Child Elements</span></span>  
  
|<span data-ttu-id="a4b72-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4b72-146">Element</span></span>|<span data-ttu-id="a4b72-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4b72-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4b72-148">\<transport></span><span class="sxs-lookup"><span data-stu-id="a4b72-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="a4b72-149">Define as configurações de segurança de transporte para um serviço básico de HTTP.</span><span class="sxs-lookup"><span data-stu-id="a4b72-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="a4b72-150">Esse elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="a4b72-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="a4b72-151">\<message></span><span class="sxs-lookup"><span data-stu-id="a4b72-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="a4b72-152">Define as configurações de segurança de mensagem para um serviço básico de HTTP.</span><span class="sxs-lookup"><span data-stu-id="a4b72-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="a4b72-153">Esse elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="a4b72-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4b72-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a4b72-154">Parent Elements</span></span>  
  
|<span data-ttu-id="a4b72-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="a4b72-155">Element</span></span>|<span data-ttu-id="a4b72-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4b72-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4b72-157">associação</span><span class="sxs-lookup"><span data-stu-id="a4b72-157">binding</span></span>|<span data-ttu-id="a4b72-158">O elemento de associação do [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a4b72-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4b72-159">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4b72-159">Remarks</span></span>  
 <span data-ttu-id="a4b72-160">Por padrão, a mensagem SOAP não é protegida e o cliente não está autenticado.</span><span class="sxs-lookup"><span data-stu-id="a4b72-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="a4b72-161">Esse elemento permite que você defina configurações de segurança adicionais para o `basicHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="a4b72-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b72-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4b72-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="a4b72-163">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a4b72-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a4b72-164">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="a4b72-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="a4b72-165">Associações</span><span class="sxs-lookup"><span data-stu-id="a4b72-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a4b72-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="a4b72-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a4b72-167">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a4b72-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a4b72-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="a4b72-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
