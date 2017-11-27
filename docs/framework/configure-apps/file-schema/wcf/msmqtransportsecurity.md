---
title: '&lt;msmqTransportSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: eee2cb916d79bf3b79e882cd757b10344121f6b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmsmqtransportsecuritygt"></a><span data-ttu-id="1abd8-102">&lt;msmqTransportSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="1abd8-102">&lt;msmqTransportSecurity&gt;</span></span>
<span data-ttu-id="1abd8-103">Especifica as configurações de segurança de transporte MSMQ para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1abd8-103">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="1abd8-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1abd8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1abd8-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="1abd8-105">\<bindings></span></span>  
<span data-ttu-id="1abd8-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1abd8-106">\<customBinding></span></span>  
<span data-ttu-id="1abd8-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="1abd8-107">\<binding></span></span>  
<span data-ttu-id="1abd8-108">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="1abd8-108">\<msmqIntegration></span></span>  
<span data-ttu-id="1abd8-109">\<msmqTransportSecurity ></span><span class="sxs-lookup"><span data-stu-id="1abd8-109">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1abd8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1abd8-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity>  
   msmqAuthenticationMode="None/Windows/Certificate"  
   msmqEncryptionAlgorithm="RC4Stream/AES"  
   msmqProtectionLevel="None/Sign/EncryptAndSign"  
   msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</msmqTransportSecurity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1abd8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1abd8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1abd8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1abd8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1abd8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="1abd8-113">Attributes</span></span>  
  
|<span data-ttu-id="1abd8-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="1abd8-114">Attribute</span></span>|<span data-ttu-id="1abd8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1abd8-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="1abd8-116">Especifica como a mensagem deve ser autenticada pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1abd8-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="1abd8-117">Se isso for definido como `None`, o valor de `msmqProtectionLevel` atributo também deve ser definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="1abd8-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="1abd8-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1abd8-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1abd8-119">-Nenhum: Nenhuma autenticação.</span><span class="sxs-lookup"><span data-stu-id="1abd8-119">-   None: No authentication.</span></span><br /><span data-ttu-id="1abd8-120">-Windows: O mecanismo de autenticação usa o Active Directory para obter o certificado x. 509 para o SID associado à mensagem.</span><span class="sxs-lookup"><span data-stu-id="1abd8-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="1abd8-121">Isso é usado para verificar a ACL da fila para garantir que o usuário tem permissão para gravar na fila.</span><span class="sxs-lookup"><span data-stu-id="1abd8-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="1abd8-122">-O certificado: O canal obtém o certificado do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="1abd8-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="1abd8-123">O valor padrão é Windows.</span><span class="sxs-lookup"><span data-stu-id="1abd8-123">The default value is Windows.</span></span> <span data-ttu-id="1abd8-124">Esse atributo é do tipo <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="1abd8-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="1abd8-125">Especifica o algoritmo a ser usado para criptografia de mensagem no fio durante a transferência de mensagens entre os gerenciadores de fila de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1abd8-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="1abd8-126">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1abd8-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1abd8-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="1abd8-127">-   RC4Stream</span></span><br /><span data-ttu-id="1abd8-128">-AES</span><span class="sxs-lookup"><span data-stu-id="1abd8-128">-   AES</span></span><br /><br /> <span data-ttu-id="1abd8-129">O valor padrão é RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="1abd8-129">The default value is RC4Stream.</span></span> <span data-ttu-id="1abd8-130">Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="1abd8-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="1abd8-131">Especifica como a mensagem é protegida no nível de transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1abd8-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="1abd8-132">A criptografia assegura a integridade da mensagem enquanto EncryptAndSign garante a integridade da mensagem e não-repúdio; ou seja, a mensagem é realmente do remetente e o remetente é quem diz que ser.</span><span class="sxs-lookup"><span data-stu-id="1abd8-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="1abd8-133">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1abd8-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1abd8-134">-Nenhum: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="1abd8-134">-   None: No protection.</span></span><br /><span data-ttu-id="1abd8-135">-Sign: Mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="1abd8-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1abd8-136">-EncryptAndSign: Mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="1abd8-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="1abd8-137">O valor padrão é o sinal.</span><span class="sxs-lookup"><span data-stu-id="1abd8-137">The default value is Sign.</span></span> <span data-ttu-id="1abd8-138">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="1abd8-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="1abd8-139">Especifica o algoritmo a ser usado no cálculo do resumo como parte das assinaturas.</span><span class="sxs-lookup"><span data-stu-id="1abd8-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="1abd8-140">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1abd8-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1abd8-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="1abd8-141">-   MD5</span></span><br /><span data-ttu-id="1abd8-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="1abd8-142">-   SHA1</span></span><br /><span data-ttu-id="1abd8-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="1abd8-143">-   SHA256</span></span><br /><span data-ttu-id="1abd8-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="1abd8-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="1abd8-145">O valor padrão é SHA1.</span><span class="sxs-lookup"><span data-stu-id="1abd8-145">The default value is SHA1.</span></span> <span data-ttu-id="1abd8-146">Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="1abd8-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1abd8-147">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1abd8-147">Child Elements</span></span>  
 <span data-ttu-id="1abd8-148">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1abd8-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1abd8-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1abd8-149">Parent Elements</span></span>  
  
|<span data-ttu-id="1abd8-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="1abd8-150">Element</span></span>|<span data-ttu-id="1abd8-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="1abd8-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1abd8-152">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="1abd8-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="1abd8-153">Especifica as configurações necessárias para interação com um remetente de enfileiramento de mensagens (MSMQ) ou do destinatário.</span><span class="sxs-lookup"><span data-stu-id="1abd8-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="1abd8-154">\<msmqTransport ></span><span class="sxs-lookup"><span data-stu-id="1abd8-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="1abd8-155">Especifica as propriedades de comunicação de enfileiramento de mensagens para um serviço do Windows Communication Foundation (WCF) que usa o protocolo nativo do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1abd8-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1abd8-156">Comentários</span><span class="sxs-lookup"><span data-stu-id="1abd8-156">Remarks</span></span>  
 <span data-ttu-id="1abd8-157">Para obter mais informações sobre segurança de transporte, consulte [segurança de transporte](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="1abd8-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1abd8-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1abd8-158">See Also</span></span>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="1abd8-159">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="1abd8-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="1abd8-160">Transportes</span><span class="sxs-lookup"><span data-stu-id="1abd8-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="1abd8-161">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="1abd8-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="1abd8-162">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="1abd8-162">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="1abd8-163">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="1abd8-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1abd8-164">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="1abd8-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1abd8-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1abd8-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="1abd8-166">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="1abd8-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
