---
title: <security> de <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: be2f48f7d9c3be4ea0a5fe95436930b3f23c7551
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170058"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="f30c8-102">\<security> de \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="f30c8-102">\<security> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="f30c8-103">Define as configurações de segurança de transporte para o canal de integração do serviço de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="f30c8-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f30c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f30c8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f30c8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f30c8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f30c8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f30c8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f30c8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f30c8-107">Attributes</span></span>  
  
|<span data-ttu-id="f30c8-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="f30c8-108">Attribute</span></span>|<span data-ttu-id="f30c8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f30c8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f30c8-110">mode</span><span class="sxs-lookup"><span data-stu-id="f30c8-110">mode</span></span>|<span data-ttu-id="f30c8-111">Especifica o tipo de segurança que controla a integridade, a confidencialidade e a autenticação com o canal de integração do enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f30c8-111">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="f30c8-112">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="f30c8-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f30c8-113">-Nenhum: isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="f30c8-113">-   None: This disables security.</span></span><br /><span data-ttu-id="f30c8-114">-Transporte: a proteção e a autenticação são oferecidas pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="f30c8-114">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="f30c8-115">Isso se aplica à segurança de mensagem entre os dois gerenciadores de fila.</span><span class="sxs-lookup"><span data-stu-id="f30c8-115">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="f30c8-116">Não há nenhuma segurança oferecida entre o Gerenciador de aplicativos e filas.</span><span class="sxs-lookup"><span data-stu-id="f30c8-116">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="f30c8-117">Os aplicativos MSMQ existentes são funcionalmente equivalentes a esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="f30c8-117">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="f30c8-118">O valor padrão é `Transport`.</span><span class="sxs-lookup"><span data-stu-id="f30c8-118">The default value is `Transport`.</span></span> <span data-ttu-id="f30c8-119">Esse atributo é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="f30c8-119">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f30c8-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f30c8-120">Child Elements</span></span>  
  
|<span data-ttu-id="f30c8-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f30c8-121">Element</span></span>|<span data-ttu-id="f30c8-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f30c8-122">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="f30c8-123">Define as configurações de segurança para o transporte de integração do enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f30c8-123">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="f30c8-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="f30c8-124">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f30c8-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f30c8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f30c8-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="f30c8-126">Element</span></span>|<span data-ttu-id="f30c8-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="f30c8-127">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f30c8-128">O elemento Binding do [\<msmqIntegrationBinding>](msmqintegrationbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f30c8-128">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f30c8-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="f30c8-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="f30c8-130">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="f30c8-130">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f30c8-131">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f30c8-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f30c8-132">Associações</span><span class="sxs-lookup"><span data-stu-id="f30c8-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f30c8-133">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f30c8-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f30c8-134">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f30c8-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
