---
title: <security> de <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 5b74c95ef2933fcf7e8d49aed89d95acbd288b80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936705"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="a3b67-102">\<> de segurança \<do MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="a3b67-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="a3b67-103">Define as configurações de segurança de transporte para o canal de integração do serviço de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="a3b67-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="a3b67-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a3b67-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a3b67-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a3b67-105">\<bindings></span></span>  
<span data-ttu-id="a3b67-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="a3b67-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="a3b67-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="a3b67-107">\<binding></span></span>  
<span data-ttu-id="a3b67-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="a3b67-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b67-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3b67-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3b67-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a3b67-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a3b67-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a3b67-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3b67-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3b67-112">Attributes</span></span>  
  
|<span data-ttu-id="a3b67-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a3b67-113">Attribute</span></span>|<span data-ttu-id="a3b67-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3b67-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3b67-115">modo</span><span class="sxs-lookup"><span data-stu-id="a3b67-115">mode</span></span>|<span data-ttu-id="a3b67-116">Especifica o tipo de segurança que controla a integridade, a confidencialidade e a autenticação com o canal de integração do enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a3b67-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="a3b67-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a3b67-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a3b67-118">None Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="a3b67-118">-   None: This disables security.</span></span><br /><span data-ttu-id="a3b67-119">Porta A proteção e a autenticação são oferecidas pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="a3b67-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="a3b67-120">Isso se aplica à segurança de mensagem entre os dois gerenciadores de fila.</span><span class="sxs-lookup"><span data-stu-id="a3b67-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="a3b67-121">Não há nenhuma segurança oferecida entre o Gerenciador de aplicativos e filas.</span><span class="sxs-lookup"><span data-stu-id="a3b67-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="a3b67-122">Os aplicativos MSMQ existentes são funcionalmente equivalentes a esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="a3b67-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="a3b67-123">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="a3b67-123">The default value is `Transport`.</span></span> <span data-ttu-id="a3b67-124">Esse atributo é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a3b67-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3b67-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a3b67-125">Child Elements</span></span>  
  
|<span data-ttu-id="a3b67-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3b67-126">Element</span></span>|<span data-ttu-id="a3b67-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3b67-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3b67-128">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="a3b67-128">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="a3b67-129">Define as configurações de segurança para o transporte de integração do enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a3b67-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="a3b67-130">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a3b67-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3b67-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a3b67-131">Parent Elements</span></span>  
  
|<span data-ttu-id="a3b67-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3b67-132">Element</span></span>|<span data-ttu-id="a3b67-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3b67-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3b67-134">\<binding></span><span class="sxs-lookup"><span data-stu-id="a3b67-134">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="a3b67-135">O elemento Binding da [ \<> MsmqIntegrationBinding](msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a3b67-135">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3b67-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3b67-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="a3b67-137">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="a3b67-137">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="a3b67-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a3b67-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a3b67-139">Associações</span><span class="sxs-lookup"><span data-stu-id="a3b67-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a3b67-140">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="a3b67-140">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a3b67-141">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a3b67-141">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a3b67-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="a3b67-142">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="a3b67-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="a3b67-143">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
