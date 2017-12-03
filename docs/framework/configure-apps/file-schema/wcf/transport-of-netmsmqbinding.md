---
title: '&lt;transporte&gt; de &lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51dcdc268a012cb8298dbc380c9c5d33a9db8d02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="1e3e3-102">&lt;transporte&gt; de &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="1e3e3-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="1e3e3-103">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="1e3e3-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1e3e3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1e3e3-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="1e3e3-105">\<bindings></span></span>  
<span data-ttu-id="1e3e3-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="1e3e3-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="1e3e3-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="1e3e3-107">\<binding></span></span>  
<span data-ttu-id="1e3e3-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="1e3e3-108">\<security></span></span>  
<span data-ttu-id="1e3e3-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="1e3e3-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e3e3-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e3e3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e3e3-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1e3e3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1e3e3-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e3e3-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e3e3-113">Attributes</span></span>  
  
|<span data-ttu-id="1e3e3-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="1e3e3-114">Attribute</span></span>|<span data-ttu-id="1e3e3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e3e3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e3e3-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="1e3e3-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="1e3e3-117">Especifica como a mensagem deve ser autenticada pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="1e3e3-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1e3e3-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1e3e3-119">-Nenhum: Nenhuma autenticação.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-119">-   None: No authentication.</span></span><br /><span data-ttu-id="1e3e3-120">-WindowsDomain: O mecanismo de autenticação usa o Active Directory para recuperar o certificado x. 509 para o identificador de segurança associado à mensagem.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="1e3e3-121">Isso é usado para verificar a ACL da fila para garantir que o usuário tem permissão de gravação para a fila.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="1e3e3-122">-O certificado: O canal recupera o certificado do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="1e3e3-123">O padrão é `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="1e3e3-124">Se esse atributo é definido como `None`, o `msmqProtectionLevel` atributo também deve ser definido como `None`.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="1e3e3-125">Esse atributo é do tipo<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="1e3e3-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="1e3e3-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="1e3e3-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="1e3e3-127">Especifica o algoritmo a ser usado para criptografia de mensagem no fio durante a transferência de mensagens entre os gerenciadores de fila de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="1e3e3-128">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1e3e3-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1e3e3-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="1e3e3-129">-   RC4Stream</span></span><br /><span data-ttu-id="1e3e3-130">-AES</span><span class="sxs-lookup"><span data-stu-id="1e3e3-130">-   AES</span></span><br /><span data-ttu-id="1e3e3-131">-O valor padrão é `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="1e3e3-132">Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="1e3e3-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="1e3e3-133">msmqProtectionLevel</span></span>|<span data-ttu-id="1e3e3-134">Especifica que as modo como as mensagens são protegidas no nível de transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="1e3e3-135">A criptografia assegura a mensagem de integridade, durante o logon e criptografar garante a integridade da mensagem e não-repúdio.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="1e3e3-136">Ou seja, a mensagem veio realmente o remetente e o remetente é quem diz que ser.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="1e3e3-137">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1e3e3-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1e3e3-138">-Nenhum: Sem proteção.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-138">-   None: No protection.</span></span><br /><span data-ttu-id="1e3e3-139">-Sign: Mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1e3e3-140">-EncryptAndSign: Mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="1e3e3-141">-O padrão é `Sign`.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="1e3e3-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="1e3e3-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="1e3e3-143">Especifica o algoritmo de hash a ser usado para computar Resumo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="1e3e3-144">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1e3e3-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1e3e3-145">-MD5</span><span class="sxs-lookup"><span data-stu-id="1e3e3-145">-   MD5</span></span><br /><span data-ttu-id="1e3e3-146">-SHA1</span><span class="sxs-lookup"><span data-stu-id="1e3e3-146">-   SHA1</span></span><br /><span data-ttu-id="1e3e3-147">-SHA256</span><span class="sxs-lookup"><span data-stu-id="1e3e3-147">-   SHA256</span></span><br /><span data-ttu-id="1e3e3-148">-SHA512</span><span class="sxs-lookup"><span data-stu-id="1e3e3-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="1e3e3-149">O padrão é `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-149">The default is `SHA1`.</span></span> <span data-ttu-id="1e3e3-150">Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e3e3-151">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e3e3-151">Child Elements</span></span>  
 <span data-ttu-id="1e3e3-152">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1e3e3-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e3e3-153">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1e3e3-153">Parent Elements</span></span>  
  
|<span data-ttu-id="1e3e3-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e3e3-154">Element</span></span>|<span data-ttu-id="1e3e3-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e3e3-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e3e3-156">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="1e3e3-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="1e3e3-157">Define as configurações de segurança de transporte para transportes na fila.</span><span class="sxs-lookup"><span data-stu-id="1e3e3-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e3e3-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e3e3-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="1e3e3-159">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="1e3e3-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="1e3e3-160">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1e3e3-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="1e3e3-161">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="1e3e3-161">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="1e3e3-162">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="1e3e3-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1e3e3-163">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1e3e3-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="1e3e3-164">\<associação ></span><span class="sxs-lookup"><span data-stu-id="1e3e3-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
