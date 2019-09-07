---
title: <clientCertificate> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: a8a78bbfcd9dfbf6975503a845d5bb4e2d24b13d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398131"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="deb72-102">\<clientCertificate > de \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="deb72-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="deb72-103">Define um certificado X. 509 usado para assinar e criptografar mensagens para um cliente forma um serviço em um padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="deb72-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
<span data-ttu-id="deb72-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="deb72-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="deb72-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="deb72-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="deb72-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="deb72-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="deb72-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="deb72-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="deb72-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="deb72-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="deb72-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="deb72-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="deb72-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> clientCertificate**</span><span class="sxs-lookup"><span data-stu-id="deb72-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deb72-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="deb72-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="deb72-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="deb72-112">Attributes and Elements</span></span>  
 <span data-ttu-id="deb72-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="deb72-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="deb72-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="deb72-114">Attributes</span></span>  
 <span data-ttu-id="deb72-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="deb72-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="deb72-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="deb72-116">Child Elements</span></span>  
  
|<span data-ttu-id="deb72-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="deb72-117">Element</span></span>|<span data-ttu-id="deb72-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="deb72-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="deb72-119">\<authentication></span><span class="sxs-lookup"><span data-stu-id="deb72-119">\<authentication></span></span>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="deb72-120">Especifica as opções de autenticação para o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="deb72-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="deb72-121">\<certificate></span><span class="sxs-lookup"><span data-stu-id="deb72-121">\<certificate></span></span>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="deb72-122">Especifica o certificado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="deb72-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="deb72-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="deb72-123">Parent Elements</span></span>  
  
|<span data-ttu-id="deb72-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="deb72-124">Element</span></span>|<span data-ttu-id="deb72-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="deb72-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="deb72-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="deb72-126">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="deb72-127">Especifica as credenciais a serem usadas na autenticação do serviço e as configurações relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="deb72-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deb72-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="deb72-128">Remarks</span></span>  
 <span data-ttu-id="deb72-129">Esse elemento é usado quando o serviço deve ter o certificado do cliente com antecedência para se comunicar com segurança com o cliente.</span><span class="sxs-lookup"><span data-stu-id="deb72-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="deb72-130">Isso ocorre ao usar o padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="deb72-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="deb72-131">No padrão de solicitação/resposta mais comum, o cliente inclui seu certificado na solicitação, que o serviço usa para criptografar e assinar sua resposta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="deb72-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="deb72-132">No padrão de comunicação duplex, no entanto, o serviço não tem uma solicitação do cliente e, portanto, precisa do certificado do cliente com antecedência para proteger a mensagem para o cliente.</span><span class="sxs-lookup"><span data-stu-id="deb72-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="deb72-133">Portanto, você deve obter o certificado do cliente em uma negociação fora de banda e especificar o certificado usando esse elemento.</span><span class="sxs-lookup"><span data-stu-id="deb72-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="deb72-134">Para obter mais informações sobre os serviços duplex [, consulte Como: Crie um contrato](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)duplex.</span><span class="sxs-lookup"><span data-stu-id="deb72-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="deb72-135">O conjunto de certificados neste elemento é usado para criptografar mensagens para o cliente somente para associações que são configuradas com `MutualCertificateDuplex` o modo de autenticação de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="deb72-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb72-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="deb72-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="deb72-137">Como: Criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="deb72-137">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="deb72-138">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="deb72-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="deb72-139">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="deb72-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
