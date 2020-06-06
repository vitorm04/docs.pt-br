---
title: <security>elemento de<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738729"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="d3f99-102">\<security>elemento de\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d3f99-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="d3f99-103">Define as configurações de segurança do [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d3f99-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="d3f99-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3f99-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3f99-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d3f99-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d3f99-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d3f99-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3f99-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d3f99-107">Attributes</span></span>  
  
|<span data-ttu-id="d3f99-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d3f99-108">Attribute</span></span>|<span data-ttu-id="d3f99-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3f99-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d3f99-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3f99-110">Optional.</span></span> <span data-ttu-id="d3f99-111">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="d3f99-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d3f99-112">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="d3f99-112">The default value is `Message`.</span></span> <span data-ttu-id="d3f99-113">Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="d3f99-113">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d3f99-114">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="d3f99-114">mode Attribute</span></span>  
  
|<span data-ttu-id="d3f99-115">Valor</span><span class="sxs-lookup"><span data-stu-id="d3f99-115">Value</span></span>|<span data-ttu-id="d3f99-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3f99-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3f99-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d3f99-117">None</span></span>|<span data-ttu-id="d3f99-118">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="d3f99-118">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="d3f99-119">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d3f99-119">Message</span></span>|<span data-ttu-id="d3f99-120">São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="d3f99-120">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="d3f99-121">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="d3f99-121">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d3f99-122">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="d3f99-122">The service must be configured with a certificate.</span></span> <span data-ttu-id="d3f99-123">A autenticação de cliente baseia-se no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="d3f99-123">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="d3f99-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d3f99-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="d3f99-125">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d3f99-125">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="d3f99-126">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="d3f99-126">The service must be configured with a certificate.</span></span> <span data-ttu-id="d3f99-127">A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="d3f99-127">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3f99-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d3f99-128">Child Elements</span></span>  
  
|<span data-ttu-id="d3f99-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3f99-129">Element</span></span>|<span data-ttu-id="d3f99-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3f99-130">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="d3f99-131">Define as configurações para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3f99-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="d3f99-132">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="d3f99-132">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3f99-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d3f99-133">Parent Elements</span></span>  
  
|<span data-ttu-id="d3f99-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3f99-134">Element</span></span>|<span data-ttu-id="d3f99-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3f99-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d3f99-136">Define todos os recursos de associação do [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d3f99-136">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3f99-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="d3f99-137">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="d3f99-138">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d3f99-138">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="d3f99-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d3f99-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d3f99-140">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="d3f99-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="d3f99-141">Associações</span><span class="sxs-lookup"><span data-stu-id="d3f99-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d3f99-142">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="d3f99-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d3f99-143">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d3f99-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
