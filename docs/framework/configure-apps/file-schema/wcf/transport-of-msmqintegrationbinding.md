---
title: <transport> de <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 03e6236d1e89f16a460860f5dffff19b7bed8a0a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169824"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="d3b1a-102">\<transport> de \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="d3b1a-102">\<transport> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="d3b1a-103">Define as configurações de segurança para o transporte de integração do enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="d3b1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3b1a-104">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3b1a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d3b1a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d3b1a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="d3b1a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3b1a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d3b1a-107">Attributes</span></span>  
  
|<span data-ttu-id="d3b1a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d3b1a-108">Attribute</span></span>|<span data-ttu-id="d3b1a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3b1a-109">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="d3b1a-110">Especifica como a mensagem deve ser autenticada pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-110">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="d3b1a-111">Se for definido como `None` , o valor do `msmqProtectionLevel` atributo também deverá ser definido como `None` .</span><span class="sxs-lookup"><span data-stu-id="d3b1a-111">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="d3b1a-112">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="d3b1a-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d3b1a-113">-Nenhum: nenhuma autenticação.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-113">-   None: No authentication.</span></span><br /><span data-ttu-id="d3b1a-114">-WindowsDomain: o mecanismo de autenticação usa Active Directory para obter o certificado X. 509 para o SID associado à mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-114">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="d3b1a-115">Isso é usado para verificar a ACL da fila para garantir que o usuário tenha permissão para gravar na fila.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-115">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="d3b1a-116">-Certificate: o canal Obtém o certificado do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-116">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="d3b1a-117">O valor padrão é WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-117">The default value is WindowsDomain.</span></span> <span data-ttu-id="d3b1a-118">Esse atributo é do tipo <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="d3b1a-118">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="d3b1a-119">Especifica o algoritmo a ser usado para criptografia de mensagem na conexão ao transferir mensagens entre gerenciadores de filas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-119">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="d3b1a-120">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="d3b1a-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d3b1a-121">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="d3b1a-121">-   RC4Stream</span></span><br /><span data-ttu-id="d3b1a-122">-AES</span><span class="sxs-lookup"><span data-stu-id="d3b1a-122">-   AES</span></span><br /><br /> <span data-ttu-id="d3b1a-123">O valor padrão é RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-123">The default value is RC4Stream.</span></span> <span data-ttu-id="d3b1a-124">Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="d3b1a-124">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="d3b1a-125">Especifica como a mensagem é protegida no nível do transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-125">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="d3b1a-126">A criptografia garante a integridade da mensagem enquanto o EncryptAndSign garante a integridade e o não-repúdio da mensagem; ou seja, a mensagem é realmente proveniente do remetente e o remetente é quem dizem eles.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-126">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="d3b1a-127">-Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d3b1a-127">-   Valid values include the following:</span></span><br /><span data-ttu-id="d3b1a-128">-Nenhum: sem proteção.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-128">-   None: No protection.</span></span><br /><span data-ttu-id="d3b1a-129">-Sign: as mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-129">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="d3b1a-130">-EncryptAndSign: as mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-130">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="d3b1a-131">O valor padrão é Sign.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-131">The default value is Sign.</span></span> <span data-ttu-id="d3b1a-132">Esse atributo é do tipo ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-132">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="d3b1a-133">-Especifica o algoritmo a ser usado na computação do resumo como parte das assinaturas.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-133">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="d3b1a-134">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="d3b1a-134">Valid values include the following:</span></span><br /><span data-ttu-id="d3b1a-135">-MD5</span><span class="sxs-lookup"><span data-stu-id="d3b1a-135">-   MD5</span></span><br /><span data-ttu-id="d3b1a-136">-SHA1</span><span class="sxs-lookup"><span data-stu-id="d3b1a-136">-   SHA1</span></span><br /><span data-ttu-id="d3b1a-137">-SHA256</span><span class="sxs-lookup"><span data-stu-id="d3b1a-137">-   SHA256</span></span><br /><span data-ttu-id="d3b1a-138">-SHA512</span><span class="sxs-lookup"><span data-stu-id="d3b1a-138">-   SHA512</span></span><br /><br /> <span data-ttu-id="d3b1a-139">O valor padrão é SHA1.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-139">The default value is SHA1.</span></span> <span data-ttu-id="d3b1a-140">Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="d3b1a-140">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="d3b1a-141">Devido a problemas de colisão com MD5 e SHA1, a Microsoft recomenda SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-141">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3b1a-142">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d3b1a-142">Child Elements</span></span>  

 <span data-ttu-id="d3b1a-143">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d3b1a-143">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3b1a-144">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d3b1a-144">Parent Elements</span></span>  
  
|<span data-ttu-id="d3b1a-145">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3b1a-145">Element</span></span>|<span data-ttu-id="d3b1a-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3b1a-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="d3b1a-147">Define as configurações de segurança para uma associação MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-147">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3b1a-148">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3b1a-148">Remarks</span></span>  

 <span data-ttu-id="d3b1a-149">Esse elemento encapsula as configurações de segurança para o transporte de integração do enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-149">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="d3b1a-150">As configurações são as mesmas para a integração do enfileiramento de mensagens e para os transportes em fila.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-150">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="d3b1a-151">Ele permite que você defina o modo de autenticação, o algoritmo de criptografia, o algoritmo de hash seguro e o nível de proteção.</span><span class="sxs-lookup"><span data-stu-id="d3b1a-151">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b1a-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="d3b1a-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="d3b1a-153">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d3b1a-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d3b1a-154">Associações</span><span class="sxs-lookup"><span data-stu-id="d3b1a-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d3b1a-155">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="d3b1a-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d3b1a-156">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d3b1a-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
