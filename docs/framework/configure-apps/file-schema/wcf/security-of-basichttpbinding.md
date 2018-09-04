---
title: '&lt;segurança&gt; de &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2adb5736cca59d42ab3c62d61513bbfd80a4be04
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565210"
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="80490-102">&lt;segurança&gt; de &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="80490-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="80490-103">Define os recursos de segurança de [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="80490-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="80490-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80490-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80490-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="80490-105">\<bindings></span></span>  
<span data-ttu-id="80490-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="80490-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="80490-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="80490-107">\<binding></span></span>  
<span data-ttu-id="80490-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="80490-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80490-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80490-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80490-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="80490-110">Attributes and Elements</span></span>  
 <span data-ttu-id="80490-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="80490-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80490-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="80490-112">Attributes</span></span>  
  
|<span data-ttu-id="80490-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="80490-113">Attribute</span></span>|<span data-ttu-id="80490-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="80490-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80490-115">modo</span><span class="sxs-lookup"><span data-stu-id="80490-115">mode</span></span>|<span data-ttu-id="80490-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="80490-116">Optional.</span></span> <span data-ttu-id="80490-117">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="80490-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="80490-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="80490-118">The default is `None`.</span></span> <span data-ttu-id="80490-119">Esse atributo é do tipo <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="80490-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="80490-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="80490-120">mode Attribute</span></span>  
  
|<span data-ttu-id="80490-121">Valor</span><span class="sxs-lookup"><span data-stu-id="80490-121">Value</span></span>|<span data-ttu-id="80490-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="80490-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80490-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="80490-123">None</span></span>|<span data-ttu-id="80490-124">-Mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="80490-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="80490-125">Transporte</span><span class="sxs-lookup"><span data-stu-id="80490-125">Transport</span></span>|<span data-ttu-id="80490-126">Segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80490-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="80490-127">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80490-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="80490-128">O serviço é autenticado para o cliente usando o certificado do serviço x. 509.</span><span class="sxs-lookup"><span data-stu-id="80490-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="80490-129">O cliente é autenticado usando o ClientCredentialType fornecido.</span><span class="sxs-lookup"><span data-stu-id="80490-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="80490-130">Consulte a [ \<transporte >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="80490-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="80490-131">Mensagem</span><span class="sxs-lookup"><span data-stu-id="80490-131">Message</span></span>|<span data-ttu-id="80490-132">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="80490-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="80490-133">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="80490-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="80490-134">Para essa associação, o sistema exige que o certificado do servidor ser fornecida para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="80490-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="80490-135">Válido somente `ClientCredentialType` para essa associação é `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="80490-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="80490-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="80490-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="80490-137">Autenticação de integridade, confidencialidade e servidor são fornecidas pela segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="80490-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="80490-138">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="80490-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="80490-139">Esse modo é relevante quando o usuário está se autenticando usando o nome de usuário/senha e não há uma implantação existente de HTTP para transferência segura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="80490-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="80490-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="80490-140">TransportCredentialOnly</span></span>|<span data-ttu-id="80490-141">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="80490-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="80490-142">Ele fornece autenticação de cliente com base em http.</span><span class="sxs-lookup"><span data-stu-id="80490-142">It provides http-based client authentication.</span></span> <span data-ttu-id="80490-143">Esse modo deve ser usado com cuidado.</span><span class="sxs-lookup"><span data-stu-id="80490-143">This mode should be used with caution.</span></span> <span data-ttu-id="80490-144">Ele deve ser usado em ambientes onde a segurança do transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="80490-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80490-145">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="80490-145">Child Elements</span></span>  
  
|<span data-ttu-id="80490-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="80490-146">Element</span></span>|<span data-ttu-id="80490-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="80490-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80490-148">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="80490-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="80490-149">Define as configurações de segurança de transporte para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="80490-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="80490-150">Esse elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="80490-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="80490-151">\<message></span><span class="sxs-lookup"><span data-stu-id="80490-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="80490-152">Define as configurações de segurança de mensagem para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="80490-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="80490-153">Esse elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="80490-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80490-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="80490-154">Parent Elements</span></span>  
  
|<span data-ttu-id="80490-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="80490-155">Element</span></span>|<span data-ttu-id="80490-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="80490-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80490-157">associação</span><span class="sxs-lookup"><span data-stu-id="80490-157">binding</span></span>|<span data-ttu-id="80490-158">O elemento de associação do [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="80490-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80490-159">Comentários</span><span class="sxs-lookup"><span data-stu-id="80490-159">Remarks</span></span>  
 <span data-ttu-id="80490-160">Por padrão, a mensagem SOAP não é protegida e o cliente não está autenticado.</span><span class="sxs-lookup"><span data-stu-id="80490-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="80490-161">Esse elemento permite que você defina as configurações de segurança adicional para o `basicHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="80490-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80490-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80490-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="80490-163">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="80490-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="80490-164">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="80490-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="80490-165">Associações</span><span class="sxs-lookup"><span data-stu-id="80490-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="80490-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="80490-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="80490-167">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="80490-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="80490-168">\<associação ></span><span class="sxs-lookup"><span data-stu-id="80490-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
