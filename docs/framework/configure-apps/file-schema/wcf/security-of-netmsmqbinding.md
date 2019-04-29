---
title: <security> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: acb4d04663d841a9b494153caa180855959c145e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670502"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="86cf2-102">\<security> of \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="86cf2-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="86cf2-103">Define as configurações de segurança para uma associação de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="86cf2-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="86cf2-104">Especifica se o transporte ou segurança SOAP está habilitada e, em caso afirmativo, quais níveis de proteção e o modo de autenticação estão em uso.</span><span class="sxs-lookup"><span data-stu-id="86cf2-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="86cf2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="86cf2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="86cf2-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="86cf2-106">\<bindings></span></span>  
<span data-ttu-id="86cf2-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="86cf2-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="86cf2-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="86cf2-108">\<binding></span></span>  
<span data-ttu-id="86cf2-109">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="86cf2-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86cf2-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86cf2-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86cf2-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="86cf2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="86cf2-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="86cf2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86cf2-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="86cf2-113">Attributes</span></span>  
  
|<span data-ttu-id="86cf2-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="86cf2-114">Attribute</span></span>|<span data-ttu-id="86cf2-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="86cf2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86cf2-116">modo</span><span class="sxs-lookup"><span data-stu-id="86cf2-116">mode</span></span>|<span data-ttu-id="86cf2-117">Especifica o tipo de segurança que controla a integridade, confidencialidade e autenticação.</span><span class="sxs-lookup"><span data-stu-id="86cf2-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="86cf2-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="86cf2-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="86cf2-119">-None: Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="86cf2-119">-   None: This disables security.</span></span><br /><span data-ttu-id="86cf2-120">-Transporte: Proteção e a autenticação são oferecidos pelo transporte.</span><span class="sxs-lookup"><span data-stu-id="86cf2-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="86cf2-121">Isso se aplica a segurança de mensagem entre os gerenciadores de fila de dois.</span><span class="sxs-lookup"><span data-stu-id="86cf2-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="86cf2-122">Não há nenhuma segurança oferecida entre o aplicativo e o Gerenciador de fila.</span><span class="sxs-lookup"><span data-stu-id="86cf2-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="86cf2-123">Aplicativos existentes do Msmq são funcionalmente equivalentes com esse tipo de modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="86cf2-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="86cf2-124">-Mensagem: Especifica a segurança de aplicativo de ponta.</span><span class="sxs-lookup"><span data-stu-id="86cf2-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="86cf2-125">Não há nenhuma segurança oferecida na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="86cf2-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="86cf2-126">Isso é semelhante para a segurança oferecida pelo outras associações padrão.</span><span class="sxs-lookup"><span data-stu-id="86cf2-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="86cf2-127">-Ambos: Oferece segurança de transporte e de camada de mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="86cf2-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="86cf2-128">A mesma credencial é necessária nos dois níveis.</span><span class="sxs-lookup"><span data-stu-id="86cf2-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="86cf2-129">O valor padrão é o transporte.</span><span class="sxs-lookup"><span data-stu-id="86cf2-129">The default value is Transport.</span></span> <span data-ttu-id="86cf2-130">Esse atributo é do tipo <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="86cf2-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86cf2-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="86cf2-131">Child Elements</span></span>  
  
|<span data-ttu-id="86cf2-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="86cf2-132">Element</span></span>|<span data-ttu-id="86cf2-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="86cf2-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86cf2-134">\<message></span><span class="sxs-lookup"><span data-stu-id="86cf2-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="86cf2-135">Define as configurações de segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="86cf2-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="86cf2-136">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="86cf2-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="86cf2-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="86cf2-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="86cf2-138">Define as configurações de segurança do transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="86cf2-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="86cf2-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="86cf2-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86cf2-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="86cf2-140">Parent Elements</span></span>  
  
|<span data-ttu-id="86cf2-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="86cf2-141">Element</span></span>|<span data-ttu-id="86cf2-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="86cf2-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86cf2-143">associação</span><span class="sxs-lookup"><span data-stu-id="86cf2-143">binding</span></span>|<span data-ttu-id="86cf2-144">O elemento de associação do [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="86cf2-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86cf2-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86cf2-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="86cf2-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="86cf2-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="86cf2-147">Associações</span><span class="sxs-lookup"><span data-stu-id="86cf2-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="86cf2-148">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="86cf2-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="86cf2-149">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="86cf2-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="86cf2-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="86cf2-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="86cf2-151">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="86cf2-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
