---
title: <transport> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ede4103f9c8f2f73ac34036fe7a58242e32350e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934687"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="b7264-102">\<> de transporte \<do NetMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="b7264-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="b7264-103">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="b7264-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="b7264-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7264-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7264-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b7264-105">\<bindings></span></span>  
<span data-ttu-id="b7264-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="b7264-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="b7264-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="b7264-107">\<binding></span></span>  
<span data-ttu-id="b7264-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="b7264-108">\<security></span></span>  
<span data-ttu-id="b7264-109">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="b7264-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7264-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7264-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7264-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7264-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b7264-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7264-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7264-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7264-113">Attributes</span></span>  
  
|<span data-ttu-id="b7264-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7264-114">Attribute</span></span>|<span data-ttu-id="b7264-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7264-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7264-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="b7264-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="b7264-117">Especifica como a mensagem deve ser autenticada pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="b7264-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="b7264-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b7264-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b7264-119">None Sem autenticação.</span><span class="sxs-lookup"><span data-stu-id="b7264-119">-   None: No authentication.</span></span><br /><span data-ttu-id="b7264-120">- WindowsDomain: O mecanismo de autenticação usa Active Directory para recuperar o certificado X. 509 para o identificador de segurança associado à mensagem.</span><span class="sxs-lookup"><span data-stu-id="b7264-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="b7264-121">Isso é usado para verificar a ACL da fila para garantir que o usuário tenha permissão de gravação para a fila.</span><span class="sxs-lookup"><span data-stu-id="b7264-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="b7264-122">Certificate O canal recupera o certificado do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="b7264-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="b7264-123">O padrão é `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="b7264-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="b7264-124">Se esse atributo for definido como `None`, o `msmqProtectionLevel` atributo também deverá ser definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="b7264-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="b7264-125">Esse atributo é do tipo<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="b7264-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="b7264-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="b7264-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="b7264-127">Especifica o algoritmo a ser usado para criptografia de mensagem na conexão ao transferir mensagens entre gerenciadores de filas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b7264-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="b7264-128">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b7264-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b7264-129">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="b7264-129">-   RC4Stream</span></span><br /><span data-ttu-id="b7264-130">-AES</span><span class="sxs-lookup"><span data-stu-id="b7264-130">-   AES</span></span><br /><span data-ttu-id="b7264-131">-O valor padrão é `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="b7264-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="b7264-132">Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="b7264-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="b7264-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="b7264-133">msmqProtectionLevel</span></span>|<span data-ttu-id="b7264-134">Especifica a maneira como as mensagens são protegidas no nível do transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="b7264-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="b7264-135">A criptografia garante a integridade da mensagem, enquanto a assinatura e a criptografia garantem a integridade da mensagem e o não-repúdio.</span><span class="sxs-lookup"><span data-stu-id="b7264-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="b7264-136">Ou seja, a mensagem realmente veio do remetente e o remetente é quem ele diz.</span><span class="sxs-lookup"><span data-stu-id="b7264-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="b7264-137">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b7264-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b7264-138">None Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="b7264-138">-   None: No protection.</span></span><br /><span data-ttu-id="b7264-139">Assine As mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="b7264-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="b7264-140">EncryptAndSign As mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="b7264-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="b7264-141">-O padrão é `Sign`.</span><span class="sxs-lookup"><span data-stu-id="b7264-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="b7264-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="b7264-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="b7264-143">Especifica o algoritmo de hash a ser usado para computar o resumo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b7264-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="b7264-144">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b7264-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b7264-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="b7264-145">-   MD5</span></span><br /><span data-ttu-id="b7264-146">-SHA1</span><span class="sxs-lookup"><span data-stu-id="b7264-146">-   SHA1</span></span><br /><span data-ttu-id="b7264-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="b7264-147">-   SHA256</span></span><br /><span data-ttu-id="b7264-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="b7264-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="b7264-149">O padrão é `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="b7264-149">The default is `SHA1`.</span></span> <span data-ttu-id="b7264-150">Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="b7264-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="b7264-151">Devido a problemas de colisão com MD5 e SHA1, a Microsoft recomenda SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="b7264-151">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7264-152">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7264-152">Child Elements</span></span>  
 <span data-ttu-id="b7264-153">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b7264-153">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7264-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7264-154">Parent Elements</span></span>  
  
|<span data-ttu-id="b7264-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7264-155">Element</span></span>|<span data-ttu-id="b7264-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7264-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7264-157">\<security></span><span class="sxs-lookup"><span data-stu-id="b7264-157">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="b7264-158">Define as configurações de segurança de transporte para transportes em fila.</span><span class="sxs-lookup"><span data-stu-id="b7264-158">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7264-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7264-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="b7264-160">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="b7264-160">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="b7264-161">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b7264-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b7264-162">Associações</span><span class="sxs-lookup"><span data-stu-id="b7264-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b7264-163">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="b7264-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b7264-164">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b7264-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b7264-165">\<binding></span><span class="sxs-lookup"><span data-stu-id="b7264-165">\<binding></span></span>](../../../misc/binding.md)
