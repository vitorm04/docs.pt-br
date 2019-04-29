---
title: Elemento <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: eea8130911ca3780a6e4e753c17877e58c50b139
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704317"
---
# <a name="certificate-element"></a><span data-ttu-id="e0ec4-102">\<certificado > elemento</span><span class="sxs-lookup"><span data-stu-id="e0ec4-102">\<certificate> Element</span></span>
<span data-ttu-id="e0ec4-103">Especifica um certificado X.509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="e0ec4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e0ec4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e0ec4-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="e0ec4-105">\<behaviors></span></span>  
<span data-ttu-id="e0ec4-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e0ec4-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e0ec4-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e0ec4-107">\<behavior></span></span>  
<span data-ttu-id="e0ec4-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e0ec4-108">\<clientCredentials></span></span>  
<span data-ttu-id="e0ec4-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="e0ec4-109">\<peer></span></span>  
<span data-ttu-id="e0ec4-110">\<certificate></span><span class="sxs-lookup"><span data-stu-id="e0ec4-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ec4-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0ec4-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0ec4-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e0ec4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e0ec4-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0ec4-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="e0ec4-114">Attributes</span></span>  
  
|<span data-ttu-id="e0ec4-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="e0ec4-115">Attribute</span></span>|<span data-ttu-id="e0ec4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0ec4-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="e0ec4-117">Uma cadeia de caracteres que contém o valor a ser pesquisado no repositório de certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="e0ec4-118">O tipo contido no atributo deve satisfazer os requisitos de especificado `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="e0ec4-119">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="e0ec4-120">Especifica o local do repositório de certificados X.509 que o cliente usa para validar o certificado do par.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="e0ec4-121">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0ec4-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e0ec4-122">-LocalMachine: o repositório de certificados atribuído ao computador local.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="e0ec4-123">-CurrentUser: o repositório de certificados atribuído ao usuário atual.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="e0ec4-124">O padrão é LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="e0ec4-125">Especifica o nome do repositório de certificados X.509 a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="e0ec4-126">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0ec4-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e0ec4-127">-Catálogo de endereços: Repositório de certificados para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="e0ec4-128">-AuthRoot: Repositório de certificados para autoridades de certificação de terceiros (CAs).</span><span class="sxs-lookup"><span data-stu-id="e0ec4-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="e0ec4-129">-CertificateAuthority: Repositório de certificados para autoridades de certificação intermediárias (CAs).</span><span class="sxs-lookup"><span data-stu-id="e0ec4-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="e0ec4-130">– Não permitido: Repositório de certificados para certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="e0ec4-131">-Minha: Repositório de certificados para certificados pessoais.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="e0ec4-132">-Raiz: Repositório de certificados para autoridades de certificação raiz confiável (CAs).</span><span class="sxs-lookup"><span data-stu-id="e0ec4-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="e0ec4-133">-TrustedPeople: Repositório de certificados para recursos e pessoas diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="e0ec4-134">-   TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="e0ec4-135">O padrão é meu.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="e0ec4-136">Define o tipo de pesquisa de X.509 a ser executada.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="e0ec4-137">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0ec4-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e0ec4-138">-   FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="e0ec4-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="e0ec4-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="e0ec4-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="e0ec4-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="e0ec4-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="e0ec4-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="e0ec4-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="e0ec4-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="e0ec4-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="e0ec4-143">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="e0ec4-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="e0ec4-144">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="e0ec4-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="e0ec4-145">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="e0ec4-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="e0ec4-146">-   FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="e0ec4-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="e0ec4-147">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="e0ec4-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="e0ec4-148">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="e0ec4-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="e0ec4-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="e0ec4-149">-   FindByExtension</span></span><br /><span data-ttu-id="e0ec4-150">-   FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="e0ec4-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="e0ec4-151">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="e0ec4-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="e0ec4-152">O tipo contido a `findValue` atributo deve satisfazer os requisitos de especificado `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="e0ec4-153">O valor padrão é FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0ec4-154">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e0ec4-154">Child Elements</span></span>  
 <span data-ttu-id="e0ec4-155">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0ec4-156">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e0ec4-156">Parent Elements</span></span>  
  
|<span data-ttu-id="e0ec4-157">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0ec4-157">Element</span></span>|<span data-ttu-id="e0ec4-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0ec4-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0ec4-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="e0ec4-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="e0ec4-160">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0ec4-161">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0ec4-161">Remarks</span></span>  
 <span data-ttu-id="e0ec4-162">Este elemento de configuração contém uma instância de X509Certificate2 usada ao autenticar vizinhos na malha ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="e0ec4-163">Para obter mais informações sobre a programação de peer-to-peer, consulte [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="e0ec4-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0ec4-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e0ec4-164">Example</span></span>  
 <span data-ttu-id="e0ec4-165">O código a seguir especifica como localizar o certificado usado em um cenário ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="e0ec4-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="e0ec4-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0ec4-166">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="e0ec4-167">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="e0ec4-167">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e0ec4-168">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="e0ec4-168">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="e0ec4-169">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e0ec4-169">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="e0ec4-170">[Autenticação personalizada de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e0ec4-170">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="e0ec4-171">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="e0ec4-171">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
