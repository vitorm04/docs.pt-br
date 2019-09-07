---
title: <security> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: c780b157d0d566e24c6826c253401a51fbfab69d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399837"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="667ce-102">\<> de segurança \<do NetMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="667ce-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="667ce-103">Define as configurações de segurança para uma associação MSMQ.</span><span class="sxs-lookup"><span data-stu-id="667ce-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="667ce-104">Especifica se a segurança de transporte ou de SOAP está habilitada e, em caso afirmativo, qual modo de autenticação e níveis de proteção estão em uso.</span><span class="sxs-lookup"><span data-stu-id="667ce-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
<span data-ttu-id="667ce-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="667ce-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="667ce-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="667ce-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="667ce-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="667ce-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="667ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> netMsmqBinding**](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="667ce-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="667ce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="667ce-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="667ce-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de segurança**</span><span class="sxs-lookup"><span data-stu-id="667ce-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="667ce-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="667ce-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="667ce-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="667ce-112">Attributes and Elements</span></span>  
 <span data-ttu-id="667ce-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="667ce-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="667ce-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="667ce-114">Attributes</span></span>  
  
|<span data-ttu-id="667ce-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="667ce-115">Attribute</span></span>|<span data-ttu-id="667ce-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="667ce-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="667ce-117">modo</span><span class="sxs-lookup"><span data-stu-id="667ce-117">mode</span></span>|<span data-ttu-id="667ce-118">Especifica o tipo de segurança que controla a integridade, a confidencialidade e a autenticação.</span><span class="sxs-lookup"><span data-stu-id="667ce-118">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="667ce-119">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="667ce-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="667ce-120">None Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="667ce-120">-   None: This disables security.</span></span><br /><span data-ttu-id="667ce-121">Porta A proteção e a autenticação são oferecidas pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="667ce-121">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="667ce-122">Isso se aplica à segurança de mensagem entre os dois gerenciadores de fila.</span><span class="sxs-lookup"><span data-stu-id="667ce-122">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="667ce-123">Não há nenhuma segurança oferecida entre o Gerenciador de aplicativos e filas.</span><span class="sxs-lookup"><span data-stu-id="667ce-123">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="667ce-124">Os aplicativos MSMQ existentes são funcionalmente equivalentes a esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="667ce-124">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="667ce-125">Exibida Especifica a segurança de aplicativo final.</span><span class="sxs-lookup"><span data-stu-id="667ce-125">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="667ce-126">Não há nenhuma segurança oferecida na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="667ce-126">There is no security offered at the transport layer.</span></span> <span data-ttu-id="667ce-127">Isso é semelhante à segurança oferecida por outras associações padrão.</span><span class="sxs-lookup"><span data-stu-id="667ce-127">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="667ce-128">Mesmo Oferece segurança na camada de mensagens de transporte e SOAP.</span><span class="sxs-lookup"><span data-stu-id="667ce-128">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="667ce-129">A mesma credencial é necessária nos dois níveis.</span><span class="sxs-lookup"><span data-stu-id="667ce-129">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="667ce-130">O valor padrão é transporte.</span><span class="sxs-lookup"><span data-stu-id="667ce-130">The default value is Transport.</span></span> <span data-ttu-id="667ce-131">Esse atributo é do tipo <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="667ce-131">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="667ce-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="667ce-132">Child Elements</span></span>  
  
|<span data-ttu-id="667ce-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="667ce-133">Element</span></span>|<span data-ttu-id="667ce-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="667ce-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="667ce-135">\<message></span><span class="sxs-lookup"><span data-stu-id="667ce-135">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="667ce-136">Define as configurações de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="667ce-136">Defines the SOAP message security settings.</span></span> <span data-ttu-id="667ce-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="667ce-137">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="667ce-138">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="667ce-138">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="667ce-139">Define as configurações de segurança para o transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="667ce-139">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="667ce-140">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="667ce-140">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="667ce-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="667ce-141">Parent Elements</span></span>  
  
|<span data-ttu-id="667ce-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="667ce-142">Element</span></span>|<span data-ttu-id="667ce-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="667ce-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="667ce-144">associação</span><span class="sxs-lookup"><span data-stu-id="667ce-144">binding</span></span>|<span data-ttu-id="667ce-145">O elemento Binding da [ \<> NetMsmqBinding](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="667ce-145">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="667ce-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="667ce-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="667ce-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="667ce-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="667ce-148">Associações</span><span class="sxs-lookup"><span data-stu-id="667ce-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="667ce-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="667ce-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="667ce-150">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="667ce-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="667ce-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="667ce-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="667ce-152">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="667ce-152">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
