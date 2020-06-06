---
title: <security> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 7877fd59aff581eee5b62a1ca224dbf51c956069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738671"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="8e533-102">\<security> de \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="8e533-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="8e533-103">Define as configurações de segurança para uma associação MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8e533-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="8e533-104">Especifica se a segurança de transporte ou de SOAP está habilitada e, em caso afirmativo, qual modo de autenticação e níveis de proteção estão em uso.</span><span class="sxs-lookup"><span data-stu-id="8e533-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="8e533-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e533-105">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e533-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e533-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8e533-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e533-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e533-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e533-108">Attributes</span></span>  
  
|<span data-ttu-id="8e533-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e533-109">Attribute</span></span>|<span data-ttu-id="8e533-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e533-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e533-111">mode</span><span class="sxs-lookup"><span data-stu-id="8e533-111">mode</span></span>|<span data-ttu-id="8e533-112">Especifica o tipo de segurança que controla a integridade, a confidencialidade e a autenticação.</span><span class="sxs-lookup"><span data-stu-id="8e533-112">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="8e533-113">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="8e533-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8e533-114">-Nenhum: isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="8e533-114">-   None: This disables security.</span></span><br /><span data-ttu-id="8e533-115">-Transporte: a proteção e a autenticação são oferecidas pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="8e533-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="8e533-116">Isso se aplica à segurança de mensagem entre os dois gerenciadores de fila.</span><span class="sxs-lookup"><span data-stu-id="8e533-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="8e533-117">Não há nenhuma segurança oferecida entre o Gerenciador de aplicativos e filas.</span><span class="sxs-lookup"><span data-stu-id="8e533-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="8e533-118">Os aplicativos MSMQ existentes são funcionalmente equivalentes a esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="8e533-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="8e533-119">-Mensagem: especifica a segurança de aplicativo final.</span><span class="sxs-lookup"><span data-stu-id="8e533-119">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="8e533-120">Não há nenhuma segurança oferecida na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="8e533-120">There is no security offered at the transport layer.</span></span> <span data-ttu-id="8e533-121">Isso é semelhante à segurança oferecida por outras associações padrão.</span><span class="sxs-lookup"><span data-stu-id="8e533-121">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="8e533-122">-Both: oferece segurança na camada de mensagens de transporte e SOAP.</span><span class="sxs-lookup"><span data-stu-id="8e533-122">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="8e533-123">A mesma credencial é necessária nos dois níveis.</span><span class="sxs-lookup"><span data-stu-id="8e533-123">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="8e533-124">O valor padrão é transporte.</span><span class="sxs-lookup"><span data-stu-id="8e533-124">The default value is Transport.</span></span> <span data-ttu-id="8e533-125">Esse atributo é do tipo <xref:System.ServiceModel.NetMsmqSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="8e533-125">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e533-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e533-126">Child Elements</span></span>  
  
|<span data-ttu-id="8e533-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e533-127">Element</span></span>|<span data-ttu-id="8e533-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e533-128">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="8e533-129">Define as configurações de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="8e533-129">Defines the SOAP message security settings.</span></span> <span data-ttu-id="8e533-130">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> .</span><span class="sxs-lookup"><span data-stu-id="8e533-130">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="8e533-131">Define as configurações de segurança para o transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8e533-131">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="8e533-132">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="8e533-132">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e533-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e533-133">Parent Elements</span></span>  
  
|<span data-ttu-id="8e533-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e533-134">Element</span></span>|<span data-ttu-id="8e533-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e533-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e533-136">associação</span><span class="sxs-lookup"><span data-stu-id="8e533-136">binding</span></span>|<span data-ttu-id="8e533-137">O elemento Binding da[\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8e533-137">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e533-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="8e533-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="8e533-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8e533-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8e533-140">Associações</span><span class="sxs-lookup"><span data-stu-id="8e533-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8e533-141">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="8e533-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8e533-142">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="8e533-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="8e533-143">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="8e533-143">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
