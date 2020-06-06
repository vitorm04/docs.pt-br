---
title: <security> de <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736484"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="c77ae-102">\<security> de \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c77ae-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="c77ae-103">Define os recursos de segurança do [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c77ae-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="c77ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c77ae-104">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c77ae-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c77ae-105">Attributes and elements</span></span>

<span data-ttu-id="c77ae-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c77ae-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c77ae-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c77ae-107">Attributes</span></span>

|<span data-ttu-id="c77ae-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="c77ae-108">Attribute</span></span>|<span data-ttu-id="c77ae-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c77ae-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c77ae-110">mode</span><span class="sxs-lookup"><span data-stu-id="c77ae-110">mode</span></span>|<span data-ttu-id="c77ae-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c77ae-111">Optional.</span></span> <span data-ttu-id="c77ae-112">Especifica o tipo de segurança que é usado.</span><span class="sxs-lookup"><span data-stu-id="c77ae-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="c77ae-113">O padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="c77ae-113">The default is `None`.</span></span> <span data-ttu-id="c77ae-114">Esse atributo é do tipo <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="c77ae-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="c77ae-115">atributo de modo</span><span class="sxs-lookup"><span data-stu-id="c77ae-115">mode attribute</span></span>

|<span data-ttu-id="c77ae-116">Valor</span><span class="sxs-lookup"><span data-stu-id="c77ae-116">Value</span></span>|<span data-ttu-id="c77ae-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c77ae-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="c77ae-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c77ae-118">None</span></span>|<span data-ttu-id="c77ae-119">-As mensagens não são protegidas durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="c77ae-119">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="c77ae-120">Transport</span><span class="sxs-lookup"><span data-stu-id="c77ae-120">Transport</span></span>|<span data-ttu-id="c77ae-121">A segurança é fornecida usando o transporte HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c77ae-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="c77ae-122">As mensagens SOAP são protegidas usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c77ae-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="c77ae-123">O serviço é autenticado para o cliente usando o certificado X. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="c77ae-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="c77ae-124">O cliente é autenticado usando o ClientCredentialtype fornecido.</span><span class="sxs-lookup"><span data-stu-id="c77ae-124">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="c77ae-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c77ae-125">Message</span></span>|<span data-ttu-id="c77ae-126">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="c77ae-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="c77ae-127">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="c77ae-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="c77ae-128">Para essa associação, o sistema requer que o certificado do servidor seja fornecido para o cliente fora da banda.</span><span class="sxs-lookup"><span data-stu-id="c77ae-128">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="c77ae-129">O único válido `ClientCredentialType` para essa associação é `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="c77ae-129">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="c77ae-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c77ae-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="c77ae-131">A integridade, a confidencialidade e a autenticação do servidor são fornecidas pela segurança do transporte.</span><span class="sxs-lookup"><span data-stu-id="c77ae-131">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="c77ae-132">A autenticação de cliente é fornecida por meio de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="c77ae-132">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="c77ae-133">Esse modo é relevante quando o usuário está Autenticando usando o nome de usuário/senha e há uma implantação HTTP existente para proteger a transferência de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c77ae-133">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="c77ae-134">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="c77ae-134">TransportCredentialOnly</span></span>|<span data-ttu-id="c77ae-135">Esse modo não fornece confidencialidade e integridade de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c77ae-135">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="c77ae-136">Ele fornece autenticação de cliente baseada em http.</span><span class="sxs-lookup"><span data-stu-id="c77ae-136">It provides http-based client authentication.</span></span> <span data-ttu-id="c77ae-137">Esse modo deve ser usado com cautela.</span><span class="sxs-lookup"><span data-stu-id="c77ae-137">This mode should be used with caution.</span></span> <span data-ttu-id="c77ae-138">Ele deve ser usado em ambientes em que a segurança de transporte está sendo fornecida por outros meios (como IPSec) e somente a autenticação do cliente é fornecida pela infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="c77ae-138">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c77ae-139">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c77ae-139">Child elements</span></span>

|<span data-ttu-id="c77ae-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="c77ae-140">Element</span></span>|<span data-ttu-id="c77ae-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="c77ae-141">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="c77ae-142">Define as configurações de segurança de transporte para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="c77ae-142">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="c77ae-143">Este elemento corresponde a <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="c77ae-143">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="c77ae-144">Define as configurações de segurança da mensagem para um serviço HTTP básico.</span><span class="sxs-lookup"><span data-stu-id="c77ae-144">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="c77ae-145">Este elemento corresponde a <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="c77ae-145">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c77ae-146">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c77ae-146">Parent elements</span></span>

|<span data-ttu-id="c77ae-147">Elemento</span><span class="sxs-lookup"><span data-stu-id="c77ae-147">Element</span></span>|<span data-ttu-id="c77ae-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="c77ae-148">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="c77ae-149">associação</span><span class="sxs-lookup"><span data-stu-id="c77ae-149">binding</span></span>|<span data-ttu-id="c77ae-150">O elemento Binding do [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c77ae-150">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="c77ae-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="c77ae-151">Remarks</span></span>

 <span data-ttu-id="c77ae-152">Por padrão, a mensagem SOAP não é protegida e o cliente não é autenticado.</span><span class="sxs-lookup"><span data-stu-id="c77ae-152">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="c77ae-153">Esse elemento permite que você defina configurações de segurança adicionais para o `netHttpBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="c77ae-153">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c77ae-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="c77ae-154">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="c77ae-155">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c77ae-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c77ae-156">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="c77ae-156">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c77ae-157">Associações</span><span class="sxs-lookup"><span data-stu-id="c77ae-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c77ae-158">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c77ae-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c77ae-159">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c77ae-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
