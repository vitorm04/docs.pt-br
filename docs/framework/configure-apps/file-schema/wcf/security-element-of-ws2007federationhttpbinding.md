---
title: <security>elemento de<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 450b2403b8cd4ec43a41fd27bccb3b77202820bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399900"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="5c285-102">\<elemento de > de \<segurança de ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5c285-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="5c285-103">Define as configurações de segurança do [ \<elemento > ws2007FederationHttpBinding](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="5c285-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="5c285-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5c285-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5c285-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5c285-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5c285-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5c285-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5c285-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ws2007FederationHttpBinding**](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5c285-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="5c285-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="5c285-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5c285-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**</span><span class="sxs-lookup"><span data-stu-id="5c285-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c285-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c285-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c285-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5c285-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5c285-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5c285-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c285-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5c285-113">Attributes</span></span>  
  
|<span data-ttu-id="5c285-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="5c285-114">Attribute</span></span>|<span data-ttu-id="5c285-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c285-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="5c285-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5c285-116">Optional.</span></span> <span data-ttu-id="5c285-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="5c285-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="5c285-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="5c285-118">The default value is `Message`.</span></span> <span data-ttu-id="5c285-119">Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5c285-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5c285-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="5c285-120">mode Attribute</span></span>  
  
|<span data-ttu-id="5c285-121">Valor</span><span class="sxs-lookup"><span data-stu-id="5c285-121">Value</span></span>|<span data-ttu-id="5c285-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c285-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c285-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5c285-123">None</span></span>|<span data-ttu-id="5c285-124">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="5c285-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="5c285-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5c285-125">Message</span></span>|<span data-ttu-id="5c285-126">São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="5c285-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="5c285-127">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="5c285-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="5c285-128">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="5c285-128">The service must be configured with a certificate.</span></span> <span data-ttu-id="5c285-129">A autenticação de cliente baseia-se no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5c285-129">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="5c285-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="5c285-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="5c285-131">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5c285-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="5c285-132">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="5c285-132">The service must be configured with a certificate.</span></span> <span data-ttu-id="5c285-133">A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5c285-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c285-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5c285-134">Child Elements</span></span>  
  
|<span data-ttu-id="5c285-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c285-135">Element</span></span>|<span data-ttu-id="5c285-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c285-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c285-137">\<message></span><span class="sxs-lookup"><span data-stu-id="5c285-137">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="5c285-138">Define as configurações para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5c285-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="5c285-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="5c285-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c285-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5c285-140">Parent Elements</span></span>  
  
|<span data-ttu-id="5c285-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c285-141">Element</span></span>|<span data-ttu-id="5c285-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c285-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c285-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="5c285-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="5c285-144">Define todos os recursos de associação do [ \<> WSDualHttpBinding](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5c285-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c285-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c285-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="5c285-146">Como: Criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5c285-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="5c285-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5c285-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5c285-148">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="5c285-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="5c285-149">Associações</span><span class="sxs-lookup"><span data-stu-id="5c285-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5c285-150">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="5c285-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5c285-151">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5c285-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5c285-152">\<binding></span><span class="sxs-lookup"><span data-stu-id="5c285-152">\<binding></span></span>](../../../misc/binding.md)
