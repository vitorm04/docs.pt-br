---
title: '&lt;transporte&gt; de &lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dc4f3cb08436f0f1af2e559c924446faa7b870c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="599f0-102">&lt;transporte&gt; de &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="599f0-102">&lt;transport&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="599f0-103">Define as configurações de segurança para o transporte de integração de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="599f0-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="599f0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="599f0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="599f0-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="599f0-105">\<bindings></span></span>  
<span data-ttu-id="599f0-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="599f0-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="599f0-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="599f0-107">\<binding></span></span>  
<span data-ttu-id="599f0-108">\<security></span><span class="sxs-lookup"><span data-stu-id="599f0-108">\<security></span></span>  
<span data-ttu-id="599f0-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="599f0-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599f0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="599f0-110">Syntax</span></span>  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="599f0-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="599f0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="599f0-112">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="599f0-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="599f0-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="599f0-113">Attributes</span></span>  
  
|<span data-ttu-id="599f0-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="599f0-114">Attribute</span></span>|<span data-ttu-id="599f0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="599f0-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="599f0-116">Especifica como a mensagem deve ser autenticada pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="599f0-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="599f0-117">Se isso for definido como `None`, o valor de `msmqProtectionLevel` atributo também deve ser definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="599f0-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="599f0-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="599f0-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="599f0-119">-Nenhum: Nenhuma autenticação.</span><span class="sxs-lookup"><span data-stu-id="599f0-119">-   None: No authentication.</span></span><br /><span data-ttu-id="599f0-120">-WindowsDomain: O mecanismo de autenticação usa o Active Directory para obter o certificado x. 509 para o SID associado à mensagem.</span><span class="sxs-lookup"><span data-stu-id="599f0-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="599f0-121">Isso é usado para verificar a ACL da fila para garantir que o usuário tem permissão para gravar na fila.</span><span class="sxs-lookup"><span data-stu-id="599f0-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="599f0-122">-O certificado: O canal obtém o certificado do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="599f0-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="599f0-123">O valor padrão é WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="599f0-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="599f0-124">Esse atributo é do tipo <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="599f0-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="599f0-125">Especifica o algoritmo a ser usado para criptografia de mensagem no fio durante a transferência de mensagens entre os gerenciadores de fila de mensagem.</span><span class="sxs-lookup"><span data-stu-id="599f0-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="599f0-126">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="599f0-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="599f0-127">-   RC4Stream</span><span class="sxs-lookup"><span data-stu-id="599f0-127">-   RC4Stream</span></span><br /><span data-ttu-id="599f0-128">-   AES</span><span class="sxs-lookup"><span data-stu-id="599f0-128">-   AES</span></span><br /><br /> <span data-ttu-id="599f0-129">O valor padrão é RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="599f0-129">The default value is RC4Stream.</span></span> <span data-ttu-id="599f0-130">Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="599f0-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="599f0-131">Especifica como a mensagem é protegida no nível de transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="599f0-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="599f0-132">A criptografia assegura a integridade da mensagem enquanto EncryptAndSign garante a integridade da mensagem e não-repúdio; ou seja, a mensagem é realmente do remetente e o remetente é quem diz que ser.</span><span class="sxs-lookup"><span data-stu-id="599f0-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="599f0-133">-Valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="599f0-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="599f0-134">-Nenhum: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="599f0-134">-   None: No protection.</span></span><br /><span data-ttu-id="599f0-135">-Sign: Mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="599f0-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="599f0-136">-EncryptAndSign: Mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="599f0-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="599f0-137">O valor padrão é o sinal.</span><span class="sxs-lookup"><span data-stu-id="599f0-137">The default value is Sign.</span></span> <span data-ttu-id="599f0-138">Esse atributo é do tipo ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="599f0-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="599f0-139">-Especifica o algoritmo a ser usado no cálculo do resumo como parte das assinaturas.</span><span class="sxs-lookup"><span data-stu-id="599f0-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="599f0-140">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="599f0-140">Valid values include the following:</span></span><br /><span data-ttu-id="599f0-141">-   MD5</span><span class="sxs-lookup"><span data-stu-id="599f0-141">-   MD5</span></span><br /><span data-ttu-id="599f0-142">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="599f0-142">-   SHA1</span></span><br /><span data-ttu-id="599f0-143">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="599f0-143">-   SHA256</span></span><br /><span data-ttu-id="599f0-144">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="599f0-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="599f0-145">O valor padrão é SHA1.</span><span class="sxs-lookup"><span data-stu-id="599f0-145">The default value is SHA1.</span></span> <span data-ttu-id="599f0-146">Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="599f0-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="599f0-147">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="599f0-147">Child Elements</span></span>  
 <span data-ttu-id="599f0-148">Nenhum</span><span class="sxs-lookup"><span data-stu-id="599f0-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="599f0-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="599f0-149">Parent Elements</span></span>  
  
|<span data-ttu-id="599f0-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="599f0-150">Element</span></span>|<span data-ttu-id="599f0-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="599f0-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="599f0-152">\<security></span><span class="sxs-lookup"><span data-stu-id="599f0-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="599f0-153">Define as configurações de segurança para uma associação de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="599f0-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="599f0-154">Comentários</span><span class="sxs-lookup"><span data-stu-id="599f0-154">Remarks</span></span>  
 <span data-ttu-id="599f0-155">Esse elemento encapsula as configurações de segurança para o transporte de integração de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="599f0-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="599f0-156">As configurações são as mesmas para a integração de enfileiramento de mensagens e de transportes na fila.</span><span class="sxs-lookup"><span data-stu-id="599f0-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="599f0-157">Ele permite que você defina o modo de autenticação, o algoritmo de criptografia, algoritmo de Hash seguro e nível de proteção.</span><span class="sxs-lookup"><span data-stu-id="599f0-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599f0-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="599f0-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="599f0-159">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="599f0-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="599f0-160">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="599f0-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="599f0-161">Associações</span><span class="sxs-lookup"><span data-stu-id="599f0-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="599f0-162">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="599f0-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="599f0-163">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="599f0-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="599f0-164">\<binding></span><span class="sxs-lookup"><span data-stu-id="599f0-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
