---
title: '&lt;segurança&gt; de &lt;msmqIntegrationBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
author: BrucePerlerMS
ms.openlocfilehash: 3f0810a705b5f46ee68a891f9b4ced42efdcb757
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48262468"
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="9c996-102">&lt;segurança&gt; de &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="9c996-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="9c996-103">Define as configurações de segurança de transporte para o canal de integração de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="9c996-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="9c996-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9c996-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9c996-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="9c996-105">\<bindings></span></span>  
<span data-ttu-id="9c996-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="9c996-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="9c996-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="9c996-107">\<binding></span></span>  
<span data-ttu-id="9c996-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="9c996-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c996-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c996-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c996-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9c996-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9c996-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9c996-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c996-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c996-112">Attributes</span></span>  
  
|<span data-ttu-id="9c996-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9c996-113">Attribute</span></span>|<span data-ttu-id="9c996-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c996-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c996-115">modo</span><span class="sxs-lookup"><span data-stu-id="9c996-115">mode</span></span>|<span data-ttu-id="9c996-116">Especifica o tipo de segurança que controles de integridade, confidencialidade e autenticação com o canal de integração de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9c996-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="9c996-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9c996-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9c996-118">-None: Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="9c996-118">-   None: This disables security.</span></span><br /><span data-ttu-id="9c996-119">-Transport: Autenticação e proteção são oferecidos pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="9c996-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="9c996-120">Isso se aplica a segurança de mensagem entre os gerenciadores de fila de dois.</span><span class="sxs-lookup"><span data-stu-id="9c996-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="9c996-121">Não há nenhuma segurança oferecida entre o aplicativo e o Gerenciador de fila.</span><span class="sxs-lookup"><span data-stu-id="9c996-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="9c996-122">Aplicativos existentes do Msmq são funcionalmente equivalentes com esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="9c996-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="9c996-123">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="9c996-123">The default value is `Transport`.</span></span> <span data-ttu-id="9c996-124">Esse atributo é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9c996-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c996-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c996-125">Child Elements</span></span>  
  
|<span data-ttu-id="9c996-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c996-126">Element</span></span>|<span data-ttu-id="9c996-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c996-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c996-128">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="9c996-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="9c996-129">Define as configurações de segurança para o transporte de integração de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9c996-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="9c996-130">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9c996-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c996-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9c996-131">Parent Elements</span></span>  
  
|<span data-ttu-id="9c996-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="9c996-132">Element</span></span>|<span data-ttu-id="9c996-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c996-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c996-134">\<associação ></span><span class="sxs-lookup"><span data-stu-id="9c996-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9c996-135">O elemento de associação do [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9c996-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c996-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c996-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="9c996-137">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="9c996-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="9c996-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9c996-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="9c996-139">Associações</span><span class="sxs-lookup"><span data-stu-id="9c996-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9c996-140">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="9c996-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="9c996-141">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9c996-141">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="9c996-142">\<associação ></span><span class="sxs-lookup"><span data-stu-id="9c996-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="9c996-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="9c996-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
