---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 9d28f3f08e9c3984c055567df03f2839709a1522
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204639"
---
# \<msmqTransportSecurity>

<span data-ttu-id="46d35-101">Especifica as configurações de segurança de transporte MSMQ para uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="46d35-101">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="46d35-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46d35-102">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46d35-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="46d35-103">Attributes and Elements</span></span>  

 <span data-ttu-id="46d35-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="46d35-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46d35-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="46d35-105">Attributes</span></span>  
  
|<span data-ttu-id="46d35-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="46d35-106">Attribute</span></span>|<span data-ttu-id="46d35-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="46d35-107">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="46d35-108">Especifica como a mensagem deve ser autenticada pelo transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="46d35-108">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="46d35-109">Se for definido como `None` , o valor do `msmqProtectionLevel` atributo também deverá ser definido como `None` .</span><span class="sxs-lookup"><span data-stu-id="46d35-109">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="46d35-110">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="46d35-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="46d35-111">-Nenhum: nenhuma autenticação.</span><span class="sxs-lookup"><span data-stu-id="46d35-111">-   None: No authentication.</span></span><br /><span data-ttu-id="46d35-112">-Windows: o mecanismo de autenticação usa Active Directory para obter o certificado X. 509 para o SID associado à mensagem.</span><span class="sxs-lookup"><span data-stu-id="46d35-112">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="46d35-113">Isso é usado para verificar a ACL da fila para garantir que o usuário tenha permissão para gravar na fila.</span><span class="sxs-lookup"><span data-stu-id="46d35-113">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="46d35-114">-Certificate: o canal Obtém o certificado do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="46d35-114">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="46d35-115">O valor padrão é Windows.</span><span class="sxs-lookup"><span data-stu-id="46d35-115">The default value is Windows.</span></span> <span data-ttu-id="46d35-116">Esse atributo é do tipo <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="46d35-116">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="46d35-117">Especifica o algoritmo a ser usado para criptografia de mensagem na conexão ao transferir mensagens entre gerenciadores de filas de mensagens.</span><span class="sxs-lookup"><span data-stu-id="46d35-117">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="46d35-118">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="46d35-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="46d35-119">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="46d35-119">-   RC4Stream</span></span><br /><span data-ttu-id="46d35-120">-AES</span><span class="sxs-lookup"><span data-stu-id="46d35-120">-   AES</span></span><br /><br /> <span data-ttu-id="46d35-121">O valor padrão é RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="46d35-121">The default value is RC4Stream.</span></span> <span data-ttu-id="46d35-122">Esse atributo é do tipo <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="46d35-122">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="46d35-123">Especifica como a mensagem é protegida no nível do transporte MSMQ.</span><span class="sxs-lookup"><span data-stu-id="46d35-123">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="46d35-124">A criptografia garante a integridade da mensagem enquanto o EncryptAndSign garante a integridade e o não-repúdio da mensagem; ou seja, a mensagem é realmente proveniente do remetente e o remetente é quem dizem eles.</span><span class="sxs-lookup"><span data-stu-id="46d35-124">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="46d35-125">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="46d35-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="46d35-126">-Nenhum: sem proteção.</span><span class="sxs-lookup"><span data-stu-id="46d35-126">-   None: No protection.</span></span><br /><span data-ttu-id="46d35-127">-Sign: as mensagens são assinadas.</span><span class="sxs-lookup"><span data-stu-id="46d35-127">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="46d35-128">-EncryptAndSign: as mensagens são criptografadas e assinadas.</span><span class="sxs-lookup"><span data-stu-id="46d35-128">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="46d35-129">O valor padrão é Sign.</span><span class="sxs-lookup"><span data-stu-id="46d35-129">The default value is Sign.</span></span> <span data-ttu-id="46d35-130">Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="46d35-130">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="46d35-131">Especifica o algoritmo a ser usado na computação do resumo como parte das assinaturas.</span><span class="sxs-lookup"><span data-stu-id="46d35-131">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="46d35-132">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="46d35-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="46d35-133">-MD5</span><span class="sxs-lookup"><span data-stu-id="46d35-133">-   MD5</span></span><br /><span data-ttu-id="46d35-134">-SHA1</span><span class="sxs-lookup"><span data-stu-id="46d35-134">-   SHA1</span></span><br /><span data-ttu-id="46d35-135">-SHA256</span><span class="sxs-lookup"><span data-stu-id="46d35-135">-   SHA256</span></span><br /><span data-ttu-id="46d35-136">-SHA512</span><span class="sxs-lookup"><span data-stu-id="46d35-136">-   SHA512</span></span><br /><br /> <span data-ttu-id="46d35-137">O valor padrão é SHA1.</span><span class="sxs-lookup"><span data-stu-id="46d35-137">The default value is SHA1.</span></span> <span data-ttu-id="46d35-138">Esse atributo é do tipo <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="46d35-138">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="46d35-139">Devido a problemas de colisão com MD5 e SHA1, a Microsoft recomenda SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="46d35-139">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46d35-140">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="46d35-140">Child Elements</span></span>  

 <span data-ttu-id="46d35-141">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="46d35-141">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46d35-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="46d35-142">Parent Elements</span></span>  
  
|<span data-ttu-id="46d35-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="46d35-143">Element</span></span>|<span data-ttu-id="46d35-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="46d35-144">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="46d35-145">Especifica as configurações necessárias para a interação com um remetente ou receptor de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="46d35-145">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="46d35-146">Especifica as propriedades de comunicação de filas para um serviço de Windows Communication Foundation (WCF) que usa o protocolo MSMQ nativo.</span><span class="sxs-lookup"><span data-stu-id="46d35-146">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46d35-147">Comentários</span><span class="sxs-lookup"><span data-stu-id="46d35-147">Remarks</span></span>  

 <span data-ttu-id="46d35-148">Para obter mais informações sobre segurança de transporte, consulte [segurança de transporte](../../../wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="46d35-148">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d35-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="46d35-149">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="46d35-150">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="46d35-150">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="46d35-151">Transportes</span><span class="sxs-lookup"><span data-stu-id="46d35-151">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="46d35-152">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="46d35-152">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="46d35-153">Associações</span><span class="sxs-lookup"><span data-stu-id="46d35-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="46d35-154">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="46d35-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="46d35-155">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="46d35-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="46d35-156">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="46d35-156">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
