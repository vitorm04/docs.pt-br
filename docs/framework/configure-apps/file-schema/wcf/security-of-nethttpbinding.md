---
title: '&lt;segurança&gt; de &lt;netHttpBinding'
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 6357593be17c2d008204598d51610fa3dbf77c27
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527455"
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="3ce01-102">&lt;segurança&gt; de &lt;netHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3ce01-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="3ce01-103">Define os recursos de segurança de [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3ce01-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="3ce01-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3ce01-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3ce01-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="3ce01-105">\<bindings></span></span>  
<span data-ttu-id="3ce01-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3ce01-106">\<netHttpBinding></span></span>  
<span data-ttu-id="3ce01-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="3ce01-107">\<binding></span></span>  
<span data-ttu-id="3ce01-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="3ce01-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce01-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ce01-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ce01-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3ce01-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ce01-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="3ce01-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ce01-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ce01-112">Attributes</span></span>  
  
|<span data-ttu-id="3ce01-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3ce01-113">Attribute</span></span>|<span data-ttu-id="3ce01-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ce01-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ce01-115">modo</span><span class="sxs-lookup"><span data-stu-id="3ce01-115">mode</span></span>|<span data-ttu-id="3ce01-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3ce01-116">Optional.</span></span> <span data-ttu-id="3ce01-117">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="3ce01-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="3ce01-118">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="3ce01-118">The default is `None`.</span></span> <span data-ttu-id="3ce01-119">Esse atributo é do tipo <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="3ce01-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="3ce01-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="3ce01-120">mode Attribute</span></span>  
  
|<span data-ttu-id="3ce01-121">Valor</span><span class="sxs-lookup"><span data-stu-id="3ce01-121">Value</span></span>|<span data-ttu-id="3ce01-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ce01-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ce01-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3ce01-123">None</span></span>|<span data-ttu-id="3ce01-124">-Mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="3ce01-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="3ce01-125">Transporte</span><span class="sxs-lookup"><span data-stu-id="3ce01-125">Transport</span></span>|<span data-ttu-id="3ce01-126">Segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3ce01-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="3ce01-127">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3ce01-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="3ce01-128">O serviço é autenticado para o cliente usando o certificado do serviço x. 509.</span><span class="sxs-lookup"><span data-stu-id="3ce01-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="3ce01-129">O cliente é autenticado usando o ClientCredentialType fornecido.</span><span class="sxs-lookup"><span data-stu-id="3ce01-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="3ce01-130">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3ce01-130">Message</span></span>|<span data-ttu-id="3ce01-131">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="3ce01-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="3ce01-132">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="3ce01-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="3ce01-133">Para essa associação, o sistema exige que o certificado do servidor ser fornecida para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="3ce01-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="3ce01-134">Válido somente `ClientCredentialType` para essa associação é `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="3ce01-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="3ce01-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3ce01-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="3ce01-136">Autenticação de integridade, confidencialidade e servidor são fornecidas pela segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="3ce01-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="3ce01-137">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="3ce01-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="3ce01-138">Esse modo é relevante quando o usuário está se autenticando usando o nome de usuário/senha e não há uma implantação existente de HTTP para transferência segura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3ce01-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="3ce01-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="3ce01-139">TransportCredentialOnly</span></span>|<span data-ttu-id="3ce01-140">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3ce01-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="3ce01-141">Ele fornece autenticação de cliente com base em http.</span><span class="sxs-lookup"><span data-stu-id="3ce01-141">It provides http-based client authentication.</span></span> <span data-ttu-id="3ce01-142">Esse modo deve ser usado com cuidado.</span><span class="sxs-lookup"><span data-stu-id="3ce01-142">This mode should be used with caution.</span></span> <span data-ttu-id="3ce01-143">Ele deve ser usado em ambientes onde a segurança do transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="3ce01-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ce01-144">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3ce01-144">Child Elements</span></span>  
  
|<span data-ttu-id="3ce01-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ce01-145">Element</span></span>|<span data-ttu-id="3ce01-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ce01-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ce01-147">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="3ce01-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="3ce01-148">Define as configurações de segurança de transporte para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="3ce01-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="3ce01-149">Esse elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="3ce01-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="3ce01-150">\<message></span><span class="sxs-lookup"><span data-stu-id="3ce01-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="3ce01-151">Define as configurações de segurança de mensagem para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="3ce01-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="3ce01-152">Esse elemento corresponde a <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="3ce01-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ce01-153">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3ce01-153">Parent Elements</span></span>  
  
|<span data-ttu-id="3ce01-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ce01-154">Element</span></span>|<span data-ttu-id="3ce01-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ce01-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ce01-156">associação</span><span class="sxs-lookup"><span data-stu-id="3ce01-156">binding</span></span>|<span data-ttu-id="3ce01-157">O elemento de associação do [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3ce01-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ce01-158">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ce01-158">Remarks</span></span>  
 <span data-ttu-id="3ce01-159">Por padrão, a mensagem SOAP não é protegida e o cliente não está autenticado.</span><span class="sxs-lookup"><span data-stu-id="3ce01-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="3ce01-160">Esse elemento permite que você defina as configurações de segurança adicional para o `netHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="3ce01-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce01-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ce01-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>    
 [<span data-ttu-id="3ce01-162">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3ce01-162">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3ce01-163">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="3ce01-163">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="3ce01-164">Associações</span><span class="sxs-lookup"><span data-stu-id="3ce01-164">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3ce01-165">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3ce01-165">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3ce01-166">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3ce01-166">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3ce01-167">\<associação ></span><span class="sxs-lookup"><span data-stu-id="3ce01-167">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
