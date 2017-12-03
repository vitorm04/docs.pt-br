---
title: '&lt;certificado&gt; de &lt;par&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8bf8cb80201f2501fb60df7c9abb5039d688dc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcertificategt-of-ltpeergt"></a><span data-ttu-id="ee2f7-102">&lt;certificado&gt; de &lt;par&gt;</span><span class="sxs-lookup"><span data-stu-id="ee2f7-102">&lt;certificate&gt; of &lt;peer&gt;</span></span>
<span data-ttu-id="ee2f7-103">Especifica um certificado usado por um colega.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-103">Specifies a certificate used by a peer.</span></span>  
  
 <span data-ttu-id="ee2f7-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ee2f7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ee2f7-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ee2f7-105">\<behaviors></span></span>  
<span data-ttu-id="ee2f7-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ee2f7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ee2f7-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="ee2f7-107">\<behavior></span></span>  
<span data-ttu-id="ee2f7-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ee2f7-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ee2f7-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="ee2f7-109">\<peer></span></span>  
<span data-ttu-id="ee2f7-110">\<certificado ></span><span class="sxs-lookup"><span data-stu-id="ee2f7-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2f7-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee2f7-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee2f7-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ee2f7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ee2f7-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee2f7-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="ee2f7-114">Attributes</span></span>  
  
|<span data-ttu-id="ee2f7-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="ee2f7-115">Attribute</span></span>|<span data-ttu-id="ee2f7-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee2f7-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="ee2f7-117">Uma cadeia de caracteres que contém o valor para pesquisar no repositório de certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="ee2f7-118">O tipo contido no atributo deve satisfazer os requisitos de especificado `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="ee2f7-119">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="ee2f7-120">Especifica o local do repositório de certificados x. 509 que o cliente usa para validar o certificado do par.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="ee2f7-121">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee2f7-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee2f7-122">-LocalMachine: o repositório de certificados atribuído ao computador local.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="ee2f7-123">-CurrentUser: o repositório de certificados atribuído ao usuário atual.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="ee2f7-124">O padrão é LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="ee2f7-125">Especifica o nome do repositório de certificados X.509 a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="ee2f7-126">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee2f7-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee2f7-127">-Catálogo de endereços: O repositório de certificados para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="ee2f7-128">-AuthRoot: Repositório de terceiros para autoridades de certificação (CAs) do certificado.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="ee2f7-129">-CertificateAuthority: Repositório de certificados intermediários para autoridades de certificação (CAs).</span><span class="sxs-lookup"><span data-stu-id="ee2f7-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="ee2f7-130">-Proibido: Repositório de certificados revogados de certificados.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="ee2f7-131">-My: Repositório de certificados pessoais do certificado.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="ee2f7-132">-Raiz: O repositório de certificados raiz confiável para autoridades de certificação (CAs).</span><span class="sxs-lookup"><span data-stu-id="ee2f7-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="ee2f7-133">-TrustedPeople: Repositório de certificados pessoas confiáveis diretamente e recursos.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="ee2f7-134">-TrustedPublisher: Repositório de certificados de editores confiáveis diretamente.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="ee2f7-135">O padrão é meu.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="ee2f7-136">Define o tipo de pesquisa x. 509 a ser executado.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="ee2f7-137">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ee2f7-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee2f7-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="ee2f7-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="ee2f7-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="ee2f7-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="ee2f7-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="ee2f7-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="ee2f7-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="ee2f7-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="ee2f7-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="ee2f7-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="ee2f7-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="ee2f7-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="ee2f7-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="ee2f7-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="ee2f7-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="ee2f7-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="ee2f7-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="ee2f7-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="ee2f7-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="ee2f7-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="ee2f7-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="ee2f7-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="ee2f7-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="ee2f7-149">-   FindByExtension</span></span><br /><span data-ttu-id="ee2f7-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="ee2f7-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="ee2f7-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="ee2f7-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="ee2f7-152">O tipo contido o `findValue` atributo deve satisfazer os requisitos de especificado `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="ee2f7-153">O valor padrão é FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee2f7-154">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ee2f7-154">Child Elements</span></span>  
 <span data-ttu-id="ee2f7-155">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee2f7-156">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ee2f7-156">Parent Elements</span></span>  
  
|<span data-ttu-id="ee2f7-157">Elemento</span><span class="sxs-lookup"><span data-stu-id="ee2f7-157">Element</span></span>|<span data-ttu-id="ee2f7-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee2f7-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee2f7-159">\<par ></span><span class="sxs-lookup"><span data-stu-id="ee2f7-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="ee2f7-160">Especifica as credenciais atuais de um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-160">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee2f7-161">Comentários</span><span class="sxs-lookup"><span data-stu-id="ee2f7-161">Remarks</span></span>  
 <span data-ttu-id="ee2f7-162">Este elemento de configuração contém um `X509Certificate2` instância usada ao autenticar vizinhos na malha de pontos.</span><span class="sxs-lookup"><span data-stu-id="ee2f7-162">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="ee2f7-163">Para obter mais informações sobre programação ponto a ponto, consulte [rede ponto a ponto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="ee2f7-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2f7-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee2f7-164">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="ee2f7-165">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="ee2f7-165">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="ee2f7-166">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="ee2f7-166">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="ee2f7-167">Autenticação de mensagens de canal par</span><span class="sxs-lookup"><span data-stu-id="ee2f7-167">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="ee2f7-168">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="ee2f7-168">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="ee2f7-169">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="ee2f7-169">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="ee2f7-170">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ee2f7-170">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
