---
title: <clientCertificate> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 9df49777efc80f425cad3b353f95db523a027214
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148911"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="b1015-102">\<clientCertificate> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="b1015-102">\<clientCertificate> of \<serviceCredentials></span></span>

<span data-ttu-id="b1015-103">Define um certificado X. 509 usado para assinar e criptografar mensagens para um cliente forma um serviço em um padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="b1015-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="b1015-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1015-104">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1015-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1015-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b1015-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1015-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1015-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1015-107">Attributes</span></span>  

 <span data-ttu-id="b1015-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b1015-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1015-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1015-109">Child Elements</span></span>  
  
|<span data-ttu-id="b1015-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1015-110">Element</span></span>|<span data-ttu-id="b1015-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1015-111">Description</span></span>|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="b1015-112">Especifica as opções de autenticação para o certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="b1015-112">Specifies authentication options for the client certificate.</span></span>|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="b1015-113">Especifica o certificado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b1015-113">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1015-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1015-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b1015-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1015-115">Element</span></span>|<span data-ttu-id="b1015-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1015-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="b1015-117">Especifica as credenciais a serem usadas na autenticação do serviço e as configurações relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="b1015-117">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1015-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1015-118">Remarks</span></span>  

 <span data-ttu-id="b1015-119">Esse elemento é usado quando o serviço deve ter o certificado do cliente com antecedência para se comunicar com segurança com o cliente.</span><span class="sxs-lookup"><span data-stu-id="b1015-119">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="b1015-120">Isso ocorre ao usar o padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="b1015-120">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="b1015-121">No padrão de solicitação/resposta mais comum, o cliente inclui seu certificado na solicitação, que o serviço usa para criptografar e assinar sua resposta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="b1015-121">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="b1015-122">No padrão de comunicação duplex, no entanto, o serviço não tem uma solicitação do cliente e, portanto, precisa do certificado do cliente com antecedência para proteger a mensagem para o cliente.</span><span class="sxs-lookup"><span data-stu-id="b1015-122">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="b1015-123">Portanto, você deve obter o certificado do cliente em uma negociação fora de banda e especificar o certificado usando esse elemento.</span><span class="sxs-lookup"><span data-stu-id="b1015-123">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="b1015-124">Para obter mais informações sobre os serviços duplex, consulte [como: criar um contrato duplex](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b1015-124">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="b1015-125">O conjunto de certificados neste elemento é usado para criptografar mensagens para o cliente somente para associações que são configuradas com o `MutualCertificateDuplex` modo de autenticação de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b1015-125">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1015-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="b1015-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="b1015-127">Como: criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="b1015-127">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="b1015-128">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b1015-128">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b1015-129">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="b1015-129">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
