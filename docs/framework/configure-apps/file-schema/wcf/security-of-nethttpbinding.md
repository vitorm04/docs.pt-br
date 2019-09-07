---
title: <security> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 890cee3271c410a921b3a88f78d0705ba8718252
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399852"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="3b863-102">\<> de segurança \<de NetHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3b863-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="3b863-103">Define os recursos de segurança do [ \<> NetHttpBinding](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3b863-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

<span data-ttu-id="3b863-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b863-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3b863-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3b863-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3b863-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3b863-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3b863-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> NetHttpBinding**](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3b863-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="3b863-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="3b863-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3b863-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**</span><span class="sxs-lookup"><span data-stu-id="3b863-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="3b863-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b863-110">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3b863-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3b863-111">Attributes and elements</span></span>

<span data-ttu-id="3b863-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3b863-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b863-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3b863-113">Attributes</span></span>

|<span data-ttu-id="3b863-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="3b863-114">Attribute</span></span>|<span data-ttu-id="3b863-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b863-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3b863-116">modo</span><span class="sxs-lookup"><span data-stu-id="3b863-116">mode</span></span>|<span data-ttu-id="3b863-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3b863-117">Optional.</span></span> <span data-ttu-id="3b863-118">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="3b863-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="3b863-119">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="3b863-119">The default is `None`.</span></span> <span data-ttu-id="3b863-120">Esse atributo é do tipo <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3b863-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="3b863-121">atributo de modo</span><span class="sxs-lookup"><span data-stu-id="3b863-121">mode attribute</span></span>

|<span data-ttu-id="3b863-122">Valor</span><span class="sxs-lookup"><span data-stu-id="3b863-122">Value</span></span>|<span data-ttu-id="3b863-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b863-123">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="3b863-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3b863-124">None</span></span>|<span data-ttu-id="3b863-125">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="3b863-125">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="3b863-126">Porta</span><span class="sxs-lookup"><span data-stu-id="3b863-126">Transport</span></span>|<span data-ttu-id="3b863-127">A segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3b863-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="3b863-128">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3b863-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="3b863-129">O serviço é autenticado para o cliente usando o certificado X. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="3b863-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="3b863-130">O cliente é autenticado usando o ClientCredentialtype fornecido.</span><span class="sxs-lookup"><span data-stu-id="3b863-130">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="3b863-131">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3b863-131">Message</span></span>|<span data-ttu-id="3b863-132">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="3b863-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="3b863-133">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="3b863-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="3b863-134">Para essa associação, o sistema requer que o certificado do servidor seja fornecido para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="3b863-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="3b863-135">O único válido `ClientCredentialType` para essa associação é `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="3b863-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="3b863-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3b863-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="3b863-137">A integridade, a confidencialidade e a autenticação do servidor são fornecidas pela segurança do transporte.</span><span class="sxs-lookup"><span data-stu-id="3b863-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="3b863-138">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="3b863-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="3b863-139">Esse modo é relevante quando o usuário está Autenticando usando o nome de usuário/senha e há uma implantação HTTP existente para proteger a transferência de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3b863-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="3b863-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="3b863-140">TransportCredentialOnly</span></span>|<span data-ttu-id="3b863-141">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3b863-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="3b863-142">Ele fornece autenticação de cliente baseada em http.</span><span class="sxs-lookup"><span data-stu-id="3b863-142">It provides http-based client authentication.</span></span> <span data-ttu-id="3b863-143">Esse modo deve ser usado com cautela.</span><span class="sxs-lookup"><span data-stu-id="3b863-143">This mode should be used with caution.</span></span> <span data-ttu-id="3b863-144">Ele deve ser usado em ambientes em que a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="3b863-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3b863-145">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3b863-145">Child elements</span></span>

|<span data-ttu-id="3b863-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="3b863-146">Element</span></span>|<span data-ttu-id="3b863-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b863-147">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b863-148">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="3b863-148">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="3b863-149">Define as configurações de segurança de transporte para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="3b863-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="3b863-150">Este elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="3b863-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="3b863-151">\<message></span><span class="sxs-lookup"><span data-stu-id="3b863-151">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="3b863-152">Define as configurações de segurança da mensagem para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="3b863-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="3b863-153">Este elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="3b863-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3b863-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3b863-154">Parent elements</span></span>

|<span data-ttu-id="3b863-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="3b863-155">Element</span></span>|<span data-ttu-id="3b863-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b863-156">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="3b863-157">associação</span><span class="sxs-lookup"><span data-stu-id="3b863-157">binding</span></span>|<span data-ttu-id="3b863-158">O elemento Binding do [ \<> BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3b863-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="3b863-159">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b863-159">Remarks</span></span>

 <span data-ttu-id="3b863-160">Por padrão, a mensagem SOAP não é protegida e o cliente não é autenticado.</span><span class="sxs-lookup"><span data-stu-id="3b863-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="3b863-161">Esse elemento permite que você defina configurações de segurança adicionais para `netHttpBinding` o elemento.</span><span class="sxs-lookup"><span data-stu-id="3b863-161">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b863-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b863-162">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="3b863-163">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3b863-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3b863-164">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="3b863-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="3b863-165">Associações</span><span class="sxs-lookup"><span data-stu-id="3b863-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3b863-166">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3b863-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3b863-167">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3b863-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3b863-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="3b863-168">\<binding></span></span>](../../../misc/binding.md)
