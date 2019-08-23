---
title: <security> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: f84f6c0f9988dd2d07377bf694286922db9d8364
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936800"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="b934f-102">\<> de segurança \<de BasicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b934f-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="b934f-103">Define os recursos de segurança do [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b934f-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="b934f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b934f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b934f-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b934f-105">\<bindings></span></span>  
<span data-ttu-id="b934f-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b934f-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="b934f-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="b934f-107">\<binding></span></span>  
<span data-ttu-id="b934f-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="b934f-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b934f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b934f-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b934f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b934f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b934f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="b934f-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b934f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b934f-112">Attributes</span></span>  
  
|<span data-ttu-id="b934f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b934f-113">Attribute</span></span>|<span data-ttu-id="b934f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b934f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b934f-115">modo</span><span class="sxs-lookup"><span data-stu-id="b934f-115">mode</span></span>|<span data-ttu-id="b934f-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b934f-116">Optional.</span></span> <span data-ttu-id="b934f-117">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="b934f-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="b934f-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="b934f-118">The default is `None`.</span></span> <span data-ttu-id="b934f-119">Esse atributo é do tipo <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="b934f-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b934f-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="b934f-120">mode Attribute</span></span>  
  
|<span data-ttu-id="b934f-121">Valor</span><span class="sxs-lookup"><span data-stu-id="b934f-121">Value</span></span>|<span data-ttu-id="b934f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b934f-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b934f-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b934f-123">None</span></span>|<span data-ttu-id="b934f-124">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="b934f-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="b934f-125">Porta</span><span class="sxs-lookup"><span data-stu-id="b934f-125">Transport</span></span>|<span data-ttu-id="b934f-126">A segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b934f-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="b934f-127">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b934f-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="b934f-128">O serviço é autenticado para o cliente usando o certificado X. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="b934f-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="b934f-129">O cliente é autenticado usando o ClientCredentialtype fornecido.</span><span class="sxs-lookup"><span data-stu-id="b934f-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="b934f-130">Consulte o [ \<> de transporte](transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b934f-130">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="b934f-131">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b934f-131">Message</span></span>|<span data-ttu-id="b934f-132">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="b934f-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="b934f-133">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="b934f-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="b934f-134">Para essa associação, o sistema requer que o certificado do servidor seja fornecido para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="b934f-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="b934f-135">O único válido `ClientCredentialType` para essa associação é `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="b934f-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="b934f-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="b934f-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="b934f-137">A integridade, a confidencialidade e a autenticação do servidor são fornecidas pela segurança do transporte.</span><span class="sxs-lookup"><span data-stu-id="b934f-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="b934f-138">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="b934f-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="b934f-139">Esse modo é relevante quando o usuário está Autenticando usando o nome de usuário/senha e há uma implantação HTTP existente para proteger a transferência de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b934f-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="b934f-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="b934f-140">TransportCredentialOnly</span></span>|<span data-ttu-id="b934f-141">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b934f-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="b934f-142">Ele fornece autenticação de cliente baseada em http.</span><span class="sxs-lookup"><span data-stu-id="b934f-142">It provides http-based client authentication.</span></span> <span data-ttu-id="b934f-143">Esse modo deve ser usado com cautela.</span><span class="sxs-lookup"><span data-stu-id="b934f-143">This mode should be used with caution.</span></span> <span data-ttu-id="b934f-144">Ele deve ser usado em ambientes em que a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="b934f-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b934f-145">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b934f-145">Child Elements</span></span>  
  
|<span data-ttu-id="b934f-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="b934f-146">Element</span></span>|<span data-ttu-id="b934f-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="b934f-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b934f-148">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="b934f-148">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="b934f-149">Define as configurações de segurança de transporte para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="b934f-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="b934f-150">Este elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="b934f-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="b934f-151">\<message></span><span class="sxs-lookup"><span data-stu-id="b934f-151">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="b934f-152">Define as configurações de segurança da mensagem para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="b934f-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="b934f-153">Este elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="b934f-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b934f-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b934f-154">Parent Elements</span></span>  
  
|<span data-ttu-id="b934f-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="b934f-155">Element</span></span>|<span data-ttu-id="b934f-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="b934f-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b934f-157">associação</span><span class="sxs-lookup"><span data-stu-id="b934f-157">binding</span></span>|<span data-ttu-id="b934f-158">O elemento Binding do [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b934f-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b934f-159">Comentários</span><span class="sxs-lookup"><span data-stu-id="b934f-159">Remarks</span></span>  
 <span data-ttu-id="b934f-160">Por padrão, a mensagem SOAP não é protegida e o cliente não é autenticado.</span><span class="sxs-lookup"><span data-stu-id="b934f-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="b934f-161">Esse elemento permite que você defina configurações de segurança adicionais para `basicHttpBinding` o elemento.</span><span class="sxs-lookup"><span data-stu-id="b934f-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b934f-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b934f-162">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="b934f-163">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b934f-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b934f-164">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="b934f-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b934f-165">Associações</span><span class="sxs-lookup"><span data-stu-id="b934f-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b934f-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="b934f-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b934f-167">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b934f-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b934f-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="b934f-168">\<binding></span></span>](../../../misc/binding.md)
