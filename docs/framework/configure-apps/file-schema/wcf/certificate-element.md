---
title: Elemento <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400549"
---
# <a name="certificate-element"></a><span data-ttu-id="47c4e-102">\<Elemento de > de certificado</span><span class="sxs-lookup"><span data-stu-id="47c4e-102">\<certificate> Element</span></span>
<span data-ttu-id="47c4e-103">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="47c4e-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
<span data-ttu-id="47c4e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="47c4e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="47c4e-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="47c4e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="47c4e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="47c4e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="47c4e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="47c4e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="47c4e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="47c4e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="47c4e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="47c4e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="47c4e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> par**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="47c4e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="47c4e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de certificado**</span><span class="sxs-lookup"><span data-stu-id="47c4e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47c4e-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47c4e-112">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47c4e-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="47c4e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="47c4e-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="47c4e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47c4e-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="47c4e-115">Attributes</span></span>  
  
|<span data-ttu-id="47c4e-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="47c4e-116">Attribute</span></span>|<span data-ttu-id="47c4e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="47c4e-117">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="47c4e-118">Uma cadeia de caracteres que contém o valor a ser procurado no repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="47c4e-118">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="47c4e-119">O tipo contido no atributo deve atender aos requisitos do especificado `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="47c4e-119">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="47c4e-120">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="47c4e-120">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="47c4e-121">Especifica o local do repositório de certificados X. 509 que o cliente usa para validar o certificado do par.</span><span class="sxs-lookup"><span data-stu-id="47c4e-121">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="47c4e-122">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="47c4e-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="47c4e-123">-LocalMachine: o repositório de certificados atribuído ao computador local.</span><span class="sxs-lookup"><span data-stu-id="47c4e-123">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="47c4e-124">-CurrentUser: o repositório de certificados atribuído ao usuário atual.</span><span class="sxs-lookup"><span data-stu-id="47c4e-124">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="47c4e-125">O padrão é LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="47c4e-125">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="47c4e-126">Especifica o nome do repositório de certificados X.509 a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="47c4e-126">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="47c4e-127">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="47c4e-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="47c4e-128">Catálogo Repositório de certificados para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="47c4e-128">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="47c4e-129">- AuthRoot: Repositório de certificados para CAs (autoridades de certificação) de terceiros.</span><span class="sxs-lookup"><span data-stu-id="47c4e-129">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="47c4e-130">CertificateAuthority Repositório de certificados para CAs (autoridades de certificação) intermediárias.</span><span class="sxs-lookup"><span data-stu-id="47c4e-130">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="47c4e-131">Permitida Repositório de certificados para certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="47c4e-131">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="47c4e-132">Pasta Repositório de certificados para certificados pessoais.</span><span class="sxs-lookup"><span data-stu-id="47c4e-132">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="47c4e-133">Básica Repositório de certificados para autoridades de certificação raiz confiáveis (CAs).</span><span class="sxs-lookup"><span data-stu-id="47c4e-133">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="47c4e-134">TrustedPeople Repositório de certificados para pessoas e recursos diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="47c4e-134">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="47c4e-135">- TrustedPublisher: Repositório de certificados para Publicadores diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="47c4e-135">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="47c4e-136">O padrão é My.</span><span class="sxs-lookup"><span data-stu-id="47c4e-136">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="47c4e-137">Define o tipo de pesquisa de X.509 a ser executada.</span><span class="sxs-lookup"><span data-stu-id="47c4e-137">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="47c4e-138">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="47c4e-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="47c4e-139">-   FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="47c4e-139">-   FindByThumbPrint</span></span><br /><span data-ttu-id="47c4e-140">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="47c4e-140">-   FindBySubjectName</span></span><br /><span data-ttu-id="47c4e-141">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="47c4e-141">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="47c4e-142">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="47c4e-142">-   FindByIssuerName</span></span><br /><span data-ttu-id="47c4e-143">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="47c4e-143">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="47c4e-144">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="47c4e-144">-   FindBySerialNumber</span></span><br /><span data-ttu-id="47c4e-145">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="47c4e-145">-   FindByTimeValid</span></span><br /><span data-ttu-id="47c4e-146">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="47c4e-146">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="47c4e-147">-   FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="47c4e-147">-   FindByTemplateName</span></span><br /><span data-ttu-id="47c4e-148">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="47c4e-148">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="47c4e-149">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="47c4e-149">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="47c4e-150">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="47c4e-150">-   FindByExtension</span></span><br /><span data-ttu-id="47c4e-151">-   FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="47c4e-151">-   FindByKeyUsage</span></span><br /><span data-ttu-id="47c4e-152">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="47c4e-152">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="47c4e-153">O tipo contido no `findValue` atributo deve atender aos requisitos do especificado. `X509FindType`</span><span class="sxs-lookup"><span data-stu-id="47c4e-153">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="47c4e-154">O valor padrão é FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="47c4e-154">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47c4e-155">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="47c4e-155">Child Elements</span></span>  
 <span data-ttu-id="47c4e-156">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="47c4e-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47c4e-157">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="47c4e-157">Parent Elements</span></span>  
  
|<span data-ttu-id="47c4e-158">Elemento</span><span class="sxs-lookup"><span data-stu-id="47c4e-158">Element</span></span>|<span data-ttu-id="47c4e-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="47c4e-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47c4e-160">\<peer></span><span class="sxs-lookup"><span data-stu-id="47c4e-160">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="47c4e-161">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="47c4e-161">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47c4e-162">Comentários</span><span class="sxs-lookup"><span data-stu-id="47c4e-162">Remarks</span></span>  
 <span data-ttu-id="47c4e-163">Este elemento de configuração contém uma instância X509Certificate2 usada ao autenticar vizinhos na malha par.</span><span class="sxs-lookup"><span data-stu-id="47c4e-163">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="47c4e-164">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="47c4e-164">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="47c4e-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47c4e-165">Example</span></span>  
 <span data-ttu-id="47c4e-166">O código a seguir especifica como localizar o certificado usado em um cenário ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="47c4e-166">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47c4e-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47c4e-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="47c4e-168">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="47c4e-168">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="47c4e-169">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="47c4e-169">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="47c4e-170">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="47c4e-170">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="47c4e-171">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="47c4e-171">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="47c4e-172">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="47c4e-172">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
