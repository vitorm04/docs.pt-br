---
title: <security> de <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 6144e5448526d7f2a7c89693f70f71a7f26c4a22
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183657"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="4984a-102">\<security> de \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4984a-102">\<security> of \<basicHttpBinding></span></span>

<span data-ttu-id="4984a-103">Define os recursos de segurança do [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4984a-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="4984a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4984a-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4984a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4984a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4984a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="4984a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4984a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="4984a-107">Attributes</span></span>  
  
|<span data-ttu-id="4984a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="4984a-108">Attribute</span></span>|<span data-ttu-id="4984a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4984a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4984a-110">mode</span><span class="sxs-lookup"><span data-stu-id="4984a-110">mode</span></span>|<span data-ttu-id="4984a-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4984a-111">Optional.</span></span> <span data-ttu-id="4984a-112">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="4984a-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="4984a-113">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="4984a-113">The default is `None`.</span></span> <span data-ttu-id="4984a-114">Esse atributo é do tipo <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="4984a-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4984a-115">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="4984a-115">mode Attribute</span></span>  
  
|<span data-ttu-id="4984a-116">Valor</span><span class="sxs-lookup"><span data-stu-id="4984a-116">Value</span></span>|<span data-ttu-id="4984a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="4984a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4984a-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4984a-118">None</span></span>|<span data-ttu-id="4984a-119">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="4984a-119">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="4984a-120">Transport</span><span class="sxs-lookup"><span data-stu-id="4984a-120">Transport</span></span>|<span data-ttu-id="4984a-121">A segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4984a-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="4984a-122">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4984a-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="4984a-123">O serviço é autenticado para o cliente usando o certificado X. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="4984a-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="4984a-124">O cliente é autenticado usando o ClientCredentialtype fornecido.</span><span class="sxs-lookup"><span data-stu-id="4984a-124">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="4984a-125">Consulte o [\<transport>](transport-of-basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4984a-125">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="4984a-126">Mensagem</span><span class="sxs-lookup"><span data-stu-id="4984a-126">Message</span></span>|<span data-ttu-id="4984a-127">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="4984a-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="4984a-128">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="4984a-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="4984a-129">Para essa associação, o sistema requer que o certificado do servidor seja fornecido para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="4984a-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="4984a-130">O único válido `ClientCredentialType` para essa associação é `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="4984a-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="4984a-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="4984a-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="4984a-132">A integridade, a confidencialidade e a autenticação do servidor são fornecidas pela segurança do transporte.</span><span class="sxs-lookup"><span data-stu-id="4984a-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="4984a-133">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="4984a-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="4984a-134">Esse modo é relevante quando o usuário está Autenticando usando o nome de usuário/senha e há uma implantação HTTP existente para proteger a transferência de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4984a-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="4984a-135">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="4984a-135">TransportCredentialOnly</span></span>|<span data-ttu-id="4984a-136">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4984a-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="4984a-137">Ele fornece autenticação de cliente baseada em http.</span><span class="sxs-lookup"><span data-stu-id="4984a-137">It provides http-based client authentication.</span></span> <span data-ttu-id="4984a-138">Esse modo deve ser usado com cautela.</span><span class="sxs-lookup"><span data-stu-id="4984a-138">This mode should be used with caution.</span></span> <span data-ttu-id="4984a-139">Ele deve ser usado em ambientes em que a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="4984a-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4984a-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4984a-140">Child Elements</span></span>  
  
|<span data-ttu-id="4984a-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="4984a-141">Element</span></span>|<span data-ttu-id="4984a-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="4984a-142">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="4984a-143">Define as configurações de segurança de transporte para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="4984a-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="4984a-144">Este elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="4984a-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="4984a-145">Define as configurações de segurança da mensagem para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="4984a-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="4984a-146">Este elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="4984a-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4984a-147">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4984a-147">Parent Elements</span></span>  
  
|<span data-ttu-id="4984a-148">Elemento</span><span class="sxs-lookup"><span data-stu-id="4984a-148">Element</span></span>|<span data-ttu-id="4984a-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="4984a-149">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4984a-150">associação</span><span class="sxs-lookup"><span data-stu-id="4984a-150">binding</span></span>|<span data-ttu-id="4984a-151">O elemento Binding do [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4984a-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4984a-152">Comentários</span><span class="sxs-lookup"><span data-stu-id="4984a-152">Remarks</span></span>  

 <span data-ttu-id="4984a-153">Por padrão, a mensagem SOAP não é protegida e o cliente não é autenticado.</span><span class="sxs-lookup"><span data-stu-id="4984a-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="4984a-154">Esse elemento permite que você defina configurações de segurança adicionais para o `basicHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="4984a-154">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4984a-155">Veja também</span><span class="sxs-lookup"><span data-stu-id="4984a-155">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="4984a-156">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4984a-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4984a-157">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="4984a-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="4984a-158">Associações</span><span class="sxs-lookup"><span data-stu-id="4984a-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4984a-159">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="4984a-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4984a-160">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="4984a-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
