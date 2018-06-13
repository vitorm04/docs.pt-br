---
title: '&lt;segurança&gt; de &lt;netHttpBinding'
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: f0795ba9095575411700fbde7d9b018c1250a164
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352646"
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="f9699-102">&lt;segurança&gt; de &lt;netHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f9699-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="f9699-103">Define os recursos de segurança de [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f9699-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="f9699-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f9699-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9699-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="f9699-105">\<bindings></span></span>  
<span data-ttu-id="f9699-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f9699-106">\<netHttpBinding></span></span>  
<span data-ttu-id="f9699-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f9699-107">\<binding></span></span>  
<span data-ttu-id="f9699-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="f9699-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9699-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9699-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9699-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f9699-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f9699-111">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="f9699-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9699-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f9699-112">Attributes</span></span>  
  
|<span data-ttu-id="f9699-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f9699-113">Attribute</span></span>|<span data-ttu-id="f9699-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9699-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9699-115">modo</span><span class="sxs-lookup"><span data-stu-id="f9699-115">mode</span></span>|<span data-ttu-id="f9699-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="f9699-116">Optional.</span></span> <span data-ttu-id="f9699-117">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="f9699-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="f9699-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="f9699-118">The default is `None`.</span></span> <span data-ttu-id="f9699-119">Esse atributo é do tipo <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="f9699-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="f9699-120">Atributo mode</span><span class="sxs-lookup"><span data-stu-id="f9699-120">mode Attribute</span></span>  
  
|<span data-ttu-id="f9699-121">Valor</span><span class="sxs-lookup"><span data-stu-id="f9699-121">Value</span></span>|<span data-ttu-id="f9699-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9699-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f9699-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f9699-123">None</span></span>|<span data-ttu-id="f9699-124">-Mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="f9699-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="f9699-125">Transporte</span><span class="sxs-lookup"><span data-stu-id="f9699-125">Transport</span></span>|<span data-ttu-id="f9699-126">A segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f9699-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="f9699-127">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f9699-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="f9699-128">O serviço é autenticado para o cliente usando o certificado de x. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="f9699-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="f9699-129">O cliente é autenticado usando ClientCredentialType fornecido.</span><span class="sxs-lookup"><span data-stu-id="f9699-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="f9699-130">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f9699-130">Message</span></span>|<span data-ttu-id="f9699-131">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="f9699-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="f9699-132">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="f9699-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="f9699-133">Para essa associação, o sistema requer que o certificado do servidor para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="f9699-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="f9699-134">Válido somente `ClientCredentialType` para essa associação é `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="f9699-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="f9699-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="f9699-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="f9699-136">Autenticação de integridade, confidencialidade e servidor são fornecidos pela segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="f9699-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="f9699-137">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="f9699-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="f9699-138">Esse modo é relevante quando o usuário estiver autenticando usando o nome de usuário/senha e há uma implantação existente de HTTP para transferência segura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f9699-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="f9699-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="f9699-139">TransportCredentialOnly</span></span>|<span data-ttu-id="f9699-140">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f9699-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="f9699-141">Ele fornece autenticação de cliente com base em http.</span><span class="sxs-lookup"><span data-stu-id="f9699-141">It provides http-based client authentication.</span></span> <span data-ttu-id="f9699-142">Esse modo deve ser usado com cuidado.</span><span class="sxs-lookup"><span data-stu-id="f9699-142">This mode should be used with caution.</span></span> <span data-ttu-id="f9699-143">Ele deve ser usado em ambientes onde a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="f9699-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9699-144">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f9699-144">Child Elements</span></span>  
  
|<span data-ttu-id="f9699-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9699-145">Element</span></span>|<span data-ttu-id="f9699-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9699-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9699-147">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="f9699-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="f9699-148">Define as configurações de segurança de transporte para um serviço básico de HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9699-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="f9699-149">Esse elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="f9699-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="f9699-150">\<message></span><span class="sxs-lookup"><span data-stu-id="f9699-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="f9699-151">Define as configurações de segurança de mensagem para um serviço básico de HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9699-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="f9699-152">Esse elemento corresponde a <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="f9699-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9699-153">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f9699-153">Parent Elements</span></span>  
  
|<span data-ttu-id="f9699-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9699-154">Element</span></span>|<span data-ttu-id="f9699-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9699-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9699-156">associação</span><span class="sxs-lookup"><span data-stu-id="f9699-156">binding</span></span>|<span data-ttu-id="f9699-157">O elemento de associação do [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f9699-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9699-158">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9699-158">Remarks</span></span>  
 <span data-ttu-id="f9699-159">Por padrão, a mensagem SOAP não é protegida e o cliente não está autenticado.</span><span class="sxs-lookup"><span data-stu-id="f9699-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="f9699-160">Esse elemento permite que você defina configurações de segurança adicionais para o `netHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="f9699-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9699-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9699-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>    
 [<span data-ttu-id="f9699-162">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f9699-162">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f9699-163">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="f9699-163">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="f9699-164">Associações</span><span class="sxs-lookup"><span data-stu-id="f9699-164">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f9699-165">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f9699-165">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f9699-166">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f9699-166">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f9699-167">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f9699-167">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
