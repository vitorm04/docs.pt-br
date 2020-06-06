---
title: <security> de <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738586"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="cb68d-102">\<security> de \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cb68d-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="cb68d-103">Representa os recursos de segurança do [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="cb68d-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="cb68d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb68d-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb68d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cb68d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cb68d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="cb68d-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb68d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="cb68d-107">Attributes</span></span>  
  
|<span data-ttu-id="cb68d-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="cb68d-108">Attribute</span></span>|<span data-ttu-id="cb68d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb68d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb68d-110">mode</span><span class="sxs-lookup"><span data-stu-id="cb68d-110">mode</span></span>|<span data-ttu-id="cb68d-111">Adicional.</span><span class="sxs-lookup"><span data-stu-id="cb68d-111">-   Optional.</span></span> <span data-ttu-id="cb68d-112">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="cb68d-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="cb68d-113">O padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="cb68d-113">The default is `Message`.</span></span><br /><span data-ttu-id="cb68d-114">-Este atributo é do tipo <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="cb68d-114">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="cb68d-115">Atributo Mode</span><span class="sxs-lookup"><span data-stu-id="cb68d-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="cb68d-116">Valor</span><span class="sxs-lookup"><span data-stu-id="cb68d-116">Value</span></span>|<span data-ttu-id="cb68d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb68d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cb68d-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cb68d-118">None</span></span>|<span data-ttu-id="cb68d-119">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="cb68d-119">Security is disabled.</span></span>|  
|<span data-ttu-id="cb68d-120">Transport</span><span class="sxs-lookup"><span data-stu-id="cb68d-120">Transport</span></span>|<span data-ttu-id="cb68d-121">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cb68d-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="cb68d-122">O serviço precisa ser configurado com certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="cb68d-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="cb68d-123">A mensagem é totalmente protegida usando HTTPS e é autenticada pelo cliente usando o certificado SSL do serviço.</span><span class="sxs-lookup"><span data-stu-id="cb68d-123">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="cb68d-124">A autenticação do cliente é controlada por meio do `ClientCredentials` atributo.</span><span class="sxs-lookup"><span data-stu-id="cb68d-124">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="cb68d-125">do [\<transport>](transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="cb68d-125">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="cb68d-126">Mensagem</span><span class="sxs-lookup"><span data-stu-id="cb68d-126">Message</span></span>|<span data-ttu-id="cb68d-127">A segurança é fornecida usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="cb68d-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="cb68d-128">Por padrão, o corpo SOAP é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="cb68d-128">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="cb68d-129">Esse modo oferece uma variedade de recursos, como se as credenciais de serviço estão disponíveis no cliente fora da banda, o pacote de algoritmos a ser usado e qual nível de proteção aplicar ao corpo da mensagem por meio da propriedade Security. Message.</span><span class="sxs-lookup"><span data-stu-id="cb68d-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="cb68d-130">A autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="cb68d-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="cb68d-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="cb68d-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="cb68d-132">Nesse modo, o HTTPS fornece integridade, confidencialidade e autenticação de servidor, e a segurança de mensagem SOAP fornece autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="cb68d-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="cb68d-133">Por padrão, a autenticação do cliente é executada uma vez por sessão e os resultados da autenticação são armazenados em cache durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="cb68d-133">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb68d-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cb68d-134">Child Elements</span></span>  
  
|<span data-ttu-id="cb68d-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb68d-135">Element</span></span>|<span data-ttu-id="cb68d-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb68d-136">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="cb68d-137">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="cb68d-137">Defines the transport security settings.</span></span> <span data-ttu-id="cb68d-138">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="cb68d-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="cb68d-139">Define as configurações de segurança para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="cb68d-139">Defines the security settings for the message.</span></span> <span data-ttu-id="cb68d-140">Este elemento corresponde ao <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> tipo.</span><span class="sxs-lookup"><span data-stu-id="cb68d-140">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb68d-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cb68d-141">Parent Elements</span></span>  
  
|<span data-ttu-id="cb68d-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="cb68d-142">Element</span></span>|<span data-ttu-id="cb68d-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb68d-143">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="cb68d-144">Uma associação segura para aplicativos de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb68d-144">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb68d-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb68d-145">Remarks</span></span>  
 <span data-ttu-id="cb68d-146">A classe WSHttpBinding foi projetada para interoperação com serviços que implementam especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="cb68d-146">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="cb68d-147">A segurança de transporte para essa associação é protocolo SSL (SSL) sobre HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cb68d-147">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb68d-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="cb68d-148">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="cb68d-149">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="cb68d-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cb68d-150">Associações</span><span class="sxs-lookup"><span data-stu-id="cb68d-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cb68d-151">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="cb68d-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cb68d-152">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="cb68d-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
