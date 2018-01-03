---
title: '&lt;clientCertificate&gt; de &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0bd36f0c13aebb75bb9d2147e871224c162b862
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="22d7a-102">&lt;clientCertificate&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="22d7a-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="22d7a-103">Define um certificado x. 509 usado para assinar e criptografar mensagens para um cliente de um serviço em um padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="22d7a-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="22d7a-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="22d7a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="22d7a-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="22d7a-105">\<behaviors></span></span>  
<span data-ttu-id="22d7a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="22d7a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="22d7a-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="22d7a-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="22d7a-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="22d7a-108">\<behavior></span></span>  
<span data-ttu-id="22d7a-109">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="22d7a-109">\<serviceCredentials></span></span>  
<span data-ttu-id="22d7a-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="22d7a-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d7a-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22d7a-111">Syntax</span></span>  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22d7a-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="22d7a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="22d7a-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="22d7a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22d7a-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="22d7a-114">Attributes</span></span>  
 <span data-ttu-id="22d7a-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="22d7a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="22d7a-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="22d7a-116">Child Elements</span></span>  
  
|<span data-ttu-id="22d7a-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="22d7a-117">Element</span></span>|<span data-ttu-id="22d7a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="22d7a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22d7a-119">\<autenticação ></span><span class="sxs-lookup"><span data-stu-id="22d7a-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="22d7a-120">Especifica opções de autenticação para o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="22d7a-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="22d7a-121">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="22d7a-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="22d7a-122">Especifica o certificado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="22d7a-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22d7a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="22d7a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="22d7a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="22d7a-124">Element</span></span>|<span data-ttu-id="22d7a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="22d7a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22d7a-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="22d7a-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="22d7a-127">Especifica as credenciais a ser usada na autenticação de serviço, e a validação de credencial de cliente as configurações relacionadas.</span><span class="sxs-lookup"><span data-stu-id="22d7a-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22d7a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="22d7a-128">Remarks</span></span>  
 <span data-ttu-id="22d7a-129">Esse elemento é usado quando o serviço deve ter o certificado do cliente com antecedência para comunicação segura com o cliente.</span><span class="sxs-lookup"><span data-stu-id="22d7a-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="22d7a-130">Isso ocorre ao usar o padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="22d7a-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="22d7a-131">No padrão de solicitação/resposta mais comum, o cliente inclui o seu certificado na solicitação, o serviço usa para criptografar e assinar sua resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="22d7a-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="22d7a-132">No padrão de comunicação duplex, no entanto, o serviço não tem uma solicitação do cliente e, portanto, é necessário que o certificado do cliente com antecedência para proteger a mensagem ao cliente.</span><span class="sxs-lookup"><span data-stu-id="22d7a-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="22d7a-133">Portanto você deve obter o certificado do cliente em uma negociação fora de banda e especificar o certificado usando esse elemento.</span><span class="sxs-lookup"><span data-stu-id="22d7a-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="22d7a-134">Para obter mais informações sobre serviços de duplex, consulte [como: criar um contrato Duplex](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="22d7a-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="22d7a-135">O certificado definido neste elemento é usado para criptografar mensagens para o cliente somente para associações que são configurados com `MutualCertificateDuplex` modo de autenticação de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="22d7a-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d7a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22d7a-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="22d7a-137">Como criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="22d7a-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="22d7a-138">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="22d7a-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="22d7a-139">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="22d7a-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
