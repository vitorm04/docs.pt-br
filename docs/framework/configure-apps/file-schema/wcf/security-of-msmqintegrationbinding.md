---
title: '&lt;segurança&gt; de &lt;msmqIntegrationBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: db263148a5a0993b546ffdd565ae7cf2edef580c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493775"
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="81511-102">&lt;segurança&gt; de &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="81511-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="81511-103">Define as configurações de segurança de transporte para o canal de integração de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="81511-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="81511-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="81511-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="81511-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="81511-105">\<bindings></span></span>  
<span data-ttu-id="81511-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="81511-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="81511-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="81511-107">\<binding></span></span>  
<span data-ttu-id="81511-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="81511-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81511-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81511-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81511-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="81511-110">Attributes and Elements</span></span>  
 <span data-ttu-id="81511-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="81511-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81511-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="81511-112">Attributes</span></span>  
  
|<span data-ttu-id="81511-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="81511-113">Attribute</span></span>|<span data-ttu-id="81511-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="81511-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81511-115">modo</span><span class="sxs-lookup"><span data-stu-id="81511-115">mode</span></span>|<span data-ttu-id="81511-116">Especifica o tipo de segurança que controles de integridade, confidencialidade e autenticação com o canal de integração de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="81511-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="81511-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="81511-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="81511-118">-None: Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="81511-118">-   None: This disables security.</span></span><br /><span data-ttu-id="81511-119">-Transporte: Proteção e a autenticação são oferecidos pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="81511-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="81511-120">Isso se aplica a segurança de mensagem entre os gerenciadores de fila de dois.</span><span class="sxs-lookup"><span data-stu-id="81511-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="81511-121">Não há nenhuma segurança oferecida entre o aplicativo e o Gerenciador de fila.</span><span class="sxs-lookup"><span data-stu-id="81511-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="81511-122">Aplicativos existentes do Msmq são funcionalmente equivalentes com esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="81511-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="81511-123">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="81511-123">The default value is `Transport`.</span></span> <span data-ttu-id="81511-124">Esse atributo é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="81511-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81511-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81511-125">Child Elements</span></span>  
  
|<span data-ttu-id="81511-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="81511-126">Element</span></span>|<span data-ttu-id="81511-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="81511-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81511-128">\<transport></span><span class="sxs-lookup"><span data-stu-id="81511-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="81511-129">Define as configurações de segurança para o transporte de integração de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="81511-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="81511-130">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="81511-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81511-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81511-131">Parent Elements</span></span>  
  
|<span data-ttu-id="81511-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="81511-132">Element</span></span>|<span data-ttu-id="81511-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="81511-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81511-134">\<binding></span><span class="sxs-lookup"><span data-stu-id="81511-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="81511-135">O elemento de associação do [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="81511-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81511-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81511-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="81511-137">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="81511-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="81511-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="81511-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="81511-139">Associações</span><span class="sxs-lookup"><span data-stu-id="81511-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="81511-140">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="81511-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="81511-141">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="81511-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="81511-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="81511-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="81511-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="81511-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
