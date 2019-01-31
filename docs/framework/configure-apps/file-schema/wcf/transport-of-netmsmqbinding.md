---
title: <transport> De <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: c82a786fe8e4a2b2e3243db007f4f705d9fbd79a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277141"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="62082-102">\<transporte > de \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="62082-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="62082-103">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="62082-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="62082-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="62082-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="62082-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="62082-105">\<bindings></span></span>  
<span data-ttu-id="62082-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="62082-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="62082-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="62082-107">\<binding></span></span>  
<span data-ttu-id="62082-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="62082-108">\<security></span></span>  
<span data-ttu-id="62082-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="62082-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62082-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62082-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62082-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="62082-111">Attributes and Elements</span></span>  
 <span data-ttu-id="62082-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="62082-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62082-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="62082-113">Attributes</span></span>  
  
|<span data-ttu-id="62082-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="62082-114">Attribute</span></span>|<span data-ttu-id="62082-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="62082-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62082-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="62082-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="62082-117">Especifica como a mensagem deve ser autenticada pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="62082-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="62082-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="62082-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62082-119">-None: Nenhuma autenticação.</span><span class="sxs-lookup"><span data-stu-id="62082-119">-   None: No authentication.</span></span><br /><span data-ttu-id="62082-120">-   WindowsDomain: O mecanismo de autenticação usa o Active Directory para recuperar o certificado X.509 para o identificador de segurança associado à mensagem.</span><span class="sxs-lookup"><span data-stu-id="62082-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="62082-121">Em seguida, isso é usado para verificar a ACL da fila para garantir que o usuário tem permissão de gravação para a fila.</span><span class="sxs-lookup"><span data-stu-id="62082-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="62082-122">-Certificado: O canal recupera o certificado do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="62082-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="62082-123">O padrão é `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="62082-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="62082-124">Se esse atributo for definido como `None`, o `msmqProtectionLevel` atributo também deve ser definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="62082-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="62082-125">Esse atributo é do tipo<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="62082-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="62082-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="62082-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="62082-127">Especifica o algoritmo a ser usado para criptografia de mensagem no fio durante a transferência de mensagens entre os gerenciadores de fila de mensagem.</span><span class="sxs-lookup"><span data-stu-id="62082-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="62082-128">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="62082-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62082-129">-   RC4Stream</span><span class="sxs-lookup"><span data-stu-id="62082-129">-   RC4Stream</span></span><br /><span data-ttu-id="62082-130">-AES</span><span class="sxs-lookup"><span data-stu-id="62082-130">-   AES</span></span><br /><span data-ttu-id="62082-131">-O valor padrão é `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="62082-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="62082-132">Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="62082-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="62082-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="62082-133">msmqProtectionLevel</span></span>|<span data-ttu-id="62082-134">Especifica que as modo como as mensagens são protegidas no nível do transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="62082-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="62082-135">A criptografia assegura a mensagem de integridade, durante a entrada e criptografar garante a integridade da mensagem e não-repúdio.</span><span class="sxs-lookup"><span data-stu-id="62082-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="62082-136">Ou seja, a mensagem foi realmente enviado do remetente e o remetente é quem diz que ser.</span><span class="sxs-lookup"><span data-stu-id="62082-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="62082-137">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="62082-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62082-138">-None: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="62082-138">-   None: No protection.</span></span><br /><span data-ttu-id="62082-139">-Sinal: As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="62082-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="62082-140">-   EncryptAndSign: As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="62082-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="62082-141">-O padrão é `Sign`.</span><span class="sxs-lookup"><span data-stu-id="62082-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="62082-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="62082-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="62082-143">Especifica o algoritmo de hash a ser usado para calcular o resumo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="62082-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="62082-144">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="62082-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62082-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="62082-145">-   MD5</span></span><br /><span data-ttu-id="62082-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="62082-146">-   SHA1</span></span><br /><span data-ttu-id="62082-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="62082-147">-   SHA256</span></span><br /><span data-ttu-id="62082-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="62082-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="62082-149">O padrão é `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="62082-149">The default is `SHA1`.</span></span> <span data-ttu-id="62082-150">Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="62082-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62082-151">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="62082-151">Child Elements</span></span>  
 <span data-ttu-id="62082-152">Nenhum</span><span class="sxs-lookup"><span data-stu-id="62082-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62082-153">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="62082-153">Parent Elements</span></span>  
  
|<span data-ttu-id="62082-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="62082-154">Element</span></span>|<span data-ttu-id="62082-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="62082-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62082-156">\<security></span><span class="sxs-lookup"><span data-stu-id="62082-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="62082-157">Define as configurações de segurança de transporte para transportes na fila.</span><span class="sxs-lookup"><span data-stu-id="62082-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62082-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62082-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="62082-159">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="62082-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="62082-160">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="62082-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="62082-161">Associações</span><span class="sxs-lookup"><span data-stu-id="62082-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="62082-162">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="62082-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="62082-163">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="62082-163">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="62082-164">\<binding></span><span class="sxs-lookup"><span data-stu-id="62082-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
