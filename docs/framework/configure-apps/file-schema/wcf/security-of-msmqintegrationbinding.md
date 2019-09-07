---
title: <security> de <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: e4f10ab994429c6cbb690caef38114b8340e6839
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399860"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="f180d-102">\<> de segurança \<do MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="f180d-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="f180d-103">Define as configurações de segurança de transporte para o canal de integração do serviço de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="f180d-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
<span data-ttu-id="f180d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f180d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f180d-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f180d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f180d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f180d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f180d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> msmqIntegrationBinding**](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f180d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="f180d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="f180d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f180d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**</span><span class="sxs-lookup"><span data-stu-id="f180d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f180d-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f180d-110">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f180d-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f180d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f180d-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f180d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f180d-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f180d-113">Attributes</span></span>  
  
|<span data-ttu-id="f180d-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="f180d-114">Attribute</span></span>|<span data-ttu-id="f180d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f180d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f180d-116">modo</span><span class="sxs-lookup"><span data-stu-id="f180d-116">mode</span></span>|<span data-ttu-id="f180d-117">Especifica o tipo de segurança que controla a integridade, a confidencialidade e a autenticação com o canal de integração do enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f180d-117">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="f180d-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f180d-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f180d-119">None Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="f180d-119">-   None: This disables security.</span></span><br /><span data-ttu-id="f180d-120">Porta A proteção e a autenticação são oferecidas pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="f180d-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="f180d-121">Isso se aplica à segurança de mensagem entre os dois gerenciadores de fila.</span><span class="sxs-lookup"><span data-stu-id="f180d-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="f180d-122">Não há nenhuma segurança oferecida entre o Gerenciador de aplicativos e filas.</span><span class="sxs-lookup"><span data-stu-id="f180d-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="f180d-123">Os aplicativos MSMQ existentes são funcionalmente equivalentes a esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="f180d-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="f180d-124">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="f180d-124">The default value is `Transport`.</span></span> <span data-ttu-id="f180d-125">Esse atributo é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f180d-125">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f180d-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f180d-126">Child Elements</span></span>  
  
|<span data-ttu-id="f180d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="f180d-127">Element</span></span>|<span data-ttu-id="f180d-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="f180d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f180d-129">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="f180d-129">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="f180d-130">Define as configurações de segurança para o transporte de integração do enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f180d-130">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="f180d-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f180d-131">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f180d-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f180d-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f180d-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="f180d-133">Element</span></span>|<span data-ttu-id="f180d-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="f180d-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f180d-135">\<binding></span><span class="sxs-lookup"><span data-stu-id="f180d-135">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="f180d-136">O elemento Binding da [ \<> MsmqIntegrationBinding](msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f180d-136">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f180d-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f180d-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="f180d-138">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="f180d-138">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f180d-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f180d-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f180d-140">Associações</span><span class="sxs-lookup"><span data-stu-id="f180d-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f180d-141">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f180d-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f180d-142">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f180d-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f180d-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="f180d-143">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="f180d-144">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="f180d-144">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
