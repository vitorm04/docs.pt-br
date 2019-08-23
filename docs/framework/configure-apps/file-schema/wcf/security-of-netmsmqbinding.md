---
title: <security> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1bbc3a460ce707e71b72a469af2e03acd8dc79e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936696"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="82a70-102">\<> de segurança \<do NetMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="82a70-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="82a70-103">Define as configurações de segurança para uma associação MSMQ.</span><span class="sxs-lookup"><span data-stu-id="82a70-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="82a70-104">Especifica se a segurança de transporte ou de SOAP está habilitada e, em caso afirmativo, qual modo de autenticação e níveis de proteção estão em uso.</span><span class="sxs-lookup"><span data-stu-id="82a70-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="82a70-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="82a70-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="82a70-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="82a70-106">\<bindings></span></span>  
<span data-ttu-id="82a70-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="82a70-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="82a70-108">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="82a70-108">\<binding></span></span>  
<span data-ttu-id="82a70-109">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="82a70-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82a70-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82a70-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82a70-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="82a70-111">Attributes and Elements</span></span>  
 <span data-ttu-id="82a70-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="82a70-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82a70-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="82a70-113">Attributes</span></span>  
  
|<span data-ttu-id="82a70-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="82a70-114">Attribute</span></span>|<span data-ttu-id="82a70-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="82a70-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82a70-116">modo</span><span class="sxs-lookup"><span data-stu-id="82a70-116">mode</span></span>|<span data-ttu-id="82a70-117">Especifica o tipo de segurança que controla a integridade, a confidencialidade e a autenticação.</span><span class="sxs-lookup"><span data-stu-id="82a70-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="82a70-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="82a70-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="82a70-119">None Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="82a70-119">-   None: This disables security.</span></span><br /><span data-ttu-id="82a70-120">Porta A proteção e a autenticação são oferecidas pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="82a70-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="82a70-121">Isso se aplica à segurança de mensagem entre os dois gerenciadores de fila.</span><span class="sxs-lookup"><span data-stu-id="82a70-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="82a70-122">Não há nenhuma segurança oferecida entre o Gerenciador de aplicativos e filas.</span><span class="sxs-lookup"><span data-stu-id="82a70-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="82a70-123">Os aplicativos MSMQ existentes são funcionalmente equivalentes a esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="82a70-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="82a70-124">Exibida Especifica a segurança de aplicativo final.</span><span class="sxs-lookup"><span data-stu-id="82a70-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="82a70-125">Não há nenhuma segurança oferecida na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="82a70-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="82a70-126">Isso é semelhante à segurança oferecida por outras associações padrão.</span><span class="sxs-lookup"><span data-stu-id="82a70-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="82a70-127">Mesmo Oferece segurança na camada de mensagens de transporte e SOAP.</span><span class="sxs-lookup"><span data-stu-id="82a70-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="82a70-128">A mesma credencial é necessária nos dois níveis.</span><span class="sxs-lookup"><span data-stu-id="82a70-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="82a70-129">O valor padrão é transporte.</span><span class="sxs-lookup"><span data-stu-id="82a70-129">The default value is Transport.</span></span> <span data-ttu-id="82a70-130">Esse atributo é do tipo <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="82a70-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82a70-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="82a70-131">Child Elements</span></span>  
  
|<span data-ttu-id="82a70-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="82a70-132">Element</span></span>|<span data-ttu-id="82a70-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="82a70-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82a70-134">\<message></span><span class="sxs-lookup"><span data-stu-id="82a70-134">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="82a70-135">Define as configurações de segurança da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="82a70-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="82a70-136">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="82a70-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="82a70-137">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="82a70-137">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="82a70-138">Define as configurações de segurança para o transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="82a70-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="82a70-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="82a70-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82a70-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="82a70-140">Parent Elements</span></span>  
  
|<span data-ttu-id="82a70-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="82a70-141">Element</span></span>|<span data-ttu-id="82a70-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="82a70-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82a70-143">associação</span><span class="sxs-lookup"><span data-stu-id="82a70-143">binding</span></span>|<span data-ttu-id="82a70-144">O elemento Binding da [ \<> NetMsmqBinding](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="82a70-144">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82a70-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82a70-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="82a70-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="82a70-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="82a70-147">Associações</span><span class="sxs-lookup"><span data-stu-id="82a70-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="82a70-148">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="82a70-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="82a70-149">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="82a70-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="82a70-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="82a70-150">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="82a70-151">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="82a70-151">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
