---
title: '&lt;segurança&gt; de &lt;msmqIntegrationBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 861942ac3ce84d75be61d7b4125ab0e17c6d86e1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="87905-102">&lt;segurança&gt; de &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="87905-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="87905-103">Define as configurações de segurança de transporte para o canal de integração de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="87905-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="87905-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87905-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87905-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="87905-105">\<bindings></span></span>  
<span data-ttu-id="87905-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="87905-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="87905-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="87905-107">\<binding></span></span>  
<span data-ttu-id="87905-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="87905-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87905-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87905-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>  
   <binding>   
       <security mode="None/Transport">  
         <transport msmqAuthenticationMode="None/Windows/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                        clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
            defaultProtectionLevel="None/Sign/EncryptAndSign" />  
       </security>  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87905-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="87905-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87905-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="87905-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87905-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="87905-112">Attributes</span></span>  
  
|<span data-ttu-id="87905-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="87905-113">Attribute</span></span>|<span data-ttu-id="87905-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="87905-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87905-115">modo</span><span class="sxs-lookup"><span data-stu-id="87905-115">mode</span></span>|<span data-ttu-id="87905-116">Especifica o tipo de segurança que controla a integridade, a confidencialidade e a autenticação com o canal de integração de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="87905-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="87905-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="87905-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="87905-118">-Nenhum: Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="87905-118">-   None: This disables security.</span></span><br /><span data-ttu-id="87905-119">-Transporte: Autenticação e proteção são oferecidos pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="87905-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="87905-120">Isso se aplica à segurança de mensagem entre os gerenciadores de fila de dois.</span><span class="sxs-lookup"><span data-stu-id="87905-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="87905-121">Não há nenhuma segurança oferecida entre o aplicativo e o Gerenciador de fila.</span><span class="sxs-lookup"><span data-stu-id="87905-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="87905-122">Os aplicativos Msmq existentes são funcionalmente equivalentes com esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="87905-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="87905-123">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="87905-123">The default value is `Transport`.</span></span> <span data-ttu-id="87905-124">Esse atributo é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="87905-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87905-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="87905-125">Child Elements</span></span>  
  
|<span data-ttu-id="87905-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="87905-126">Element</span></span>|<span data-ttu-id="87905-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="87905-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87905-128">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="87905-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="87905-129">Define as configurações de segurança para o transporte de integração de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="87905-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="87905-130">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="87905-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87905-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="87905-131">Parent Elements</span></span>  
  
|<span data-ttu-id="87905-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="87905-132">Element</span></span>|<span data-ttu-id="87905-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="87905-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87905-134">\<associação ></span><span class="sxs-lookup"><span data-stu-id="87905-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="87905-135">O elemento de associação do [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="87905-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87905-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87905-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="87905-137">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="87905-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="87905-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="87905-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="87905-139">Associações</span><span class="sxs-lookup"><span data-stu-id="87905-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="87905-140">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="87905-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="87905-141">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="87905-141">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="87905-142">\<associação ></span><span class="sxs-lookup"><span data-stu-id="87905-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="87905-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="87905-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
