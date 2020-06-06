---
title: <transport> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152925"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="0138c-102">\<transport> de \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="0138c-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="0138c-103">Define as configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="0138c-103">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="0138c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0138c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0138c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0138c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0138c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0138c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0138c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0138c-107">Attributes</span></span>  
  
|<span data-ttu-id="0138c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="0138c-108">Attribute</span></span>|<span data-ttu-id="0138c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0138c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0138c-110">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="0138c-110">msmqAuthenticationMode</span></span>|<span data-ttu-id="0138c-111">Especifica como a mensagem deve ser autenticada pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0138c-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="0138c-112">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0138c-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0138c-113">-Nenhum: nenhuma autenticação.</span><span class="sxs-lookup"><span data-stu-id="0138c-113">-   None: No authentication.</span></span><br /><span data-ttu-id="0138c-114">-WindowsDomain: o mecanismo de autenticação usa Active Directory para recuperar o certificado X. 509 para o identificador de segurança associado à mensagem.</span><span class="sxs-lookup"><span data-stu-id="0138c-114">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="0138c-115">Isso é usado para verificar a ACL da fila para garantir que o usuário tenha permissão de gravação para a fila.</span><span class="sxs-lookup"><span data-stu-id="0138c-115">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="0138c-116">-Certificate: o canal recupera o certificado do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="0138c-116">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="0138c-117">O padrão é `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="0138c-117">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="0138c-118">Se esse atributo for definido como `None` , o `msmqProtectionLevel` atributo também deverá ser definido como `None` .</span><span class="sxs-lookup"><span data-stu-id="0138c-118">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="0138c-119">Esse atributo é do tipo<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="0138c-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="0138c-120">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="0138c-120">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="0138c-121">Especifica o algoritmo a ser usado para criptografia de mensagem na conexão ao transferir mensagens entre gerenciadores de filas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="0138c-121">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="0138c-122">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0138c-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0138c-123">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="0138c-123">-   RC4Stream</span></span><br /><span data-ttu-id="0138c-124">-AES</span><span class="sxs-lookup"><span data-stu-id="0138c-124">-   AES</span></span><br /><span data-ttu-id="0138c-125">-O valor padrão é `RC4Stream` .</span><span class="sxs-lookup"><span data-stu-id="0138c-125">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="0138c-126">Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="0138c-126">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="0138c-127">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="0138c-127">msmqProtectionLevel</span></span>|<span data-ttu-id="0138c-128">Especifica a maneira como as mensagens são protegidas no nível do transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0138c-128">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="0138c-129">A criptografia garante a integridade da mensagem, enquanto a assinatura e a criptografia garantem a integridade da mensagem e o não-repúdio.</span><span class="sxs-lookup"><span data-stu-id="0138c-129">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="0138c-130">Ou seja, a mensagem realmente veio do remetente e o remetente é quem eles dizem.</span><span class="sxs-lookup"><span data-stu-id="0138c-130">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="0138c-131">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0138c-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0138c-132">-Nenhum: sem proteção.</span><span class="sxs-lookup"><span data-stu-id="0138c-132">-   None: No protection.</span></span><br /><span data-ttu-id="0138c-133">-Sign: as mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="0138c-133">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="0138c-134">-EncryptAndSign: as mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="0138c-134">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="0138c-135">-O padrão é `Sign` .</span><span class="sxs-lookup"><span data-stu-id="0138c-135">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="0138c-136">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="0138c-136">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="0138c-137">Especifica o algoritmo de hash a ser usado para computar o resumo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="0138c-137">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="0138c-138">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0138c-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0138c-139">-MD5</span><span class="sxs-lookup"><span data-stu-id="0138c-139">-   MD5</span></span><br /><span data-ttu-id="0138c-140">-SHA1</span><span class="sxs-lookup"><span data-stu-id="0138c-140">-   SHA1</span></span><br /><span data-ttu-id="0138c-141">-SHA256</span><span class="sxs-lookup"><span data-stu-id="0138c-141">-   SHA256</span></span><br /><span data-ttu-id="0138c-142">-SHA512</span><span class="sxs-lookup"><span data-stu-id="0138c-142">-   SHA512</span></span><br /><br /> <span data-ttu-id="0138c-143">O padrão é `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="0138c-143">The default is `SHA1`.</span></span> <span data-ttu-id="0138c-144">Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="0138c-144">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="0138c-145">Devido a problemas de colisão com MD5 e SHA1, a Microsoft recomenda SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="0138c-145">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0138c-146">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0138c-146">Child Elements</span></span>  
 <span data-ttu-id="0138c-147">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0138c-147">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0138c-148">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0138c-148">Parent Elements</span></span>  
  
|<span data-ttu-id="0138c-149">Elemento</span><span class="sxs-lookup"><span data-stu-id="0138c-149">Element</span></span>|<span data-ttu-id="0138c-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="0138c-150">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="0138c-151">Define as configurações de segurança de transporte para transportes em fila.</span><span class="sxs-lookup"><span data-stu-id="0138c-151">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0138c-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="0138c-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="0138c-153">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="0138c-153">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="0138c-154">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="0138c-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0138c-155">Associações</span><span class="sxs-lookup"><span data-stu-id="0138c-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0138c-156">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="0138c-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0138c-157">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="0138c-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
