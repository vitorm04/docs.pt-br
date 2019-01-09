---
title: '&lt;clientCertificate&gt; de &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 7f777fd0e09a1bb9491f346a8e9806627aa63441
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145491"
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="7cf76-102">&lt;clientCertificate&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="7cf76-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="7cf76-103">Define um certificado X.509 usado para assinar e criptografar mensagens para um cliente de um serviço em um padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="7cf76-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="7cf76-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7cf76-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7cf76-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7cf76-105">\<behaviors></span></span>  
<span data-ttu-id="7cf76-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7cf76-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7cf76-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7cf76-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="7cf76-108">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="7cf76-108">\<behavior></span></span>  
<span data-ttu-id="7cf76-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7cf76-109">\<serviceCredentials></span></span>  
<span data-ttu-id="7cf76-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="7cf76-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf76-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7cf76-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cf76-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7cf76-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7cf76-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="7cf76-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cf76-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7cf76-114">Attributes</span></span>  
 <span data-ttu-id="7cf76-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7cf76-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7cf76-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7cf76-116">Child Elements</span></span>  
  
|<span data-ttu-id="7cf76-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="7cf76-117">Element</span></span>|<span data-ttu-id="7cf76-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cf76-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cf76-119">\<authentication></span><span class="sxs-lookup"><span data-stu-id="7cf76-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="7cf76-120">Especifica opções de autenticação para o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="7cf76-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="7cf76-121">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="7cf76-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="7cf76-122">Especifica o certificado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="7cf76-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cf76-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7cf76-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7cf76-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="7cf76-124">Element</span></span>|<span data-ttu-id="7cf76-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cf76-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cf76-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7cf76-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="7cf76-127">Especifica as credenciais a serem usadas ao autenticar o serviço, e configurações relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="7cf76-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cf76-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="7cf76-128">Remarks</span></span>  
 <span data-ttu-id="7cf76-129">Esse elemento é usado quando o serviço deve ter o certificado do cliente com antecedência para se comunicar com segurança com o cliente.</span><span class="sxs-lookup"><span data-stu-id="7cf76-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="7cf76-130">Isso ocorre ao usar o padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="7cf76-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="7cf76-131">No padrão mais comum de solicitação/resposta, o cliente inclui seu certificado na solicitação, o serviço usa para criptografar e assinar sua resposta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="7cf76-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="7cf76-132">No padrão de comunicação duplex, no entanto, o serviço não tem uma solicitação do cliente e, portanto, ele precisa que o certificado do cliente com antecedência para proteger a mensagem ao cliente.</span><span class="sxs-lookup"><span data-stu-id="7cf76-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="7cf76-133">Portanto você deve obter o certificado do cliente em uma negociação de out-of-band e especificar o certificado usando esse elemento.</span><span class="sxs-lookup"><span data-stu-id="7cf76-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="7cf76-134">Para obter mais informações sobre serviços duplex, consulte [como: Criar um contrato Duplex](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="7cf76-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="7cf76-135">O certificado definido neste elemento é usado para criptografar mensagens para o cliente somente para associações que estão configurados com `MutualCertificateDuplex` modo de autenticação de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7cf76-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf76-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7cf76-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="7cf76-137">Como: Criar um contrato Duplex</span><span class="sxs-lookup"><span data-stu-id="7cf76-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="7cf76-138">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="7cf76-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7cf76-139">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="7cf76-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
