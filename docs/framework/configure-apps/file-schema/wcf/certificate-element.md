---
title: Elemento <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 8cc0404a5896dd23cffce6f1f77b91a2f01f23d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151084"
---
# <a name="certificate-element"></a><span data-ttu-id="41a5f-102">Elemento \<certificate></span><span class="sxs-lookup"><span data-stu-id="41a5f-102">\<certificate> Element</span></span>

<span data-ttu-id="41a5f-103">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="41a5f-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="41a5f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="41a5f-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41a5f-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="41a5f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="41a5f-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="41a5f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41a5f-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="41a5f-107">Attributes</span></span>  
  
|<span data-ttu-id="41a5f-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="41a5f-108">Attribute</span></span>|<span data-ttu-id="41a5f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="41a5f-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="41a5f-110">Uma cadeia de caracteres que contém o valor a ser procurado no repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="41a5f-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="41a5f-111">O tipo contido no atributo deve atender aos requisitos do especificado `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="41a5f-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="41a5f-112">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="41a5f-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="41a5f-113">Especifica o local do repositório de certificados X. 509 que o cliente usa para validar o certificado do par.</span><span class="sxs-lookup"><span data-stu-id="41a5f-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="41a5f-114">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="41a5f-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41a5f-115">-LocalMachine: o repositório de certificados atribuído ao computador local.</span><span class="sxs-lookup"><span data-stu-id="41a5f-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="41a5f-116">-CurrentUser: o repositório de certificados atribuído ao usuário atual.</span><span class="sxs-lookup"><span data-stu-id="41a5f-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="41a5f-117">O padrão é LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="41a5f-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="41a5f-118">Especifica o nome do repositório de certificados X.509 a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="41a5f-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="41a5f-119">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="41a5f-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41a5f-120">-Catálogo: repositório de certificados para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="41a5f-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="41a5f-121">-AuthRoot: repositório de certificados para CAs (autoridades de certificação) de terceiros.</span><span class="sxs-lookup"><span data-stu-id="41a5f-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="41a5f-122">-CertificateAuthority: repositório de certificados para CAs (autoridades de certificação) intermediárias.</span><span class="sxs-lookup"><span data-stu-id="41a5f-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="41a5f-123">-Não permitido: repositório de certificados para certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="41a5f-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="41a5f-124">-My: repositório de certificados para certificados pessoais.</span><span class="sxs-lookup"><span data-stu-id="41a5f-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="41a5f-125">-Root: repositório de certificados para autoridades de certificação raiz confiáveis (CAs).</span><span class="sxs-lookup"><span data-stu-id="41a5f-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="41a5f-126">-TrustedPeople: repositório de certificados para pessoas e recursos diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="41a5f-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="41a5f-127">-TrustedPublisher: repositório de certificados para Publicadores diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="41a5f-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="41a5f-128">O padrão é My.</span><span class="sxs-lookup"><span data-stu-id="41a5f-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="41a5f-129">Define o tipo de pesquisa de X.509 a ser executada.</span><span class="sxs-lookup"><span data-stu-id="41a5f-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="41a5f-130">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="41a5f-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41a5f-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="41a5f-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="41a5f-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="41a5f-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="41a5f-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="41a5f-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="41a5f-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="41a5f-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="41a5f-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="41a5f-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="41a5f-136">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="41a5f-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="41a5f-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="41a5f-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="41a5f-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="41a5f-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="41a5f-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="41a5f-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="41a5f-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="41a5f-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="41a5f-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="41a5f-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="41a5f-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="41a5f-142">-   FindByExtension</span></span><br /><span data-ttu-id="41a5f-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="41a5f-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="41a5f-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="41a5f-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="41a5f-145">O tipo contido no `findValue` atributo deve atender aos requisitos do especificado `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="41a5f-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="41a5f-146">O valor padrão é FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="41a5f-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41a5f-147">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="41a5f-147">Child Elements</span></span>  

 <span data-ttu-id="41a5f-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="41a5f-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41a5f-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="41a5f-149">Parent Elements</span></span>  
  
|<span data-ttu-id="41a5f-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="41a5f-150">Element</span></span>|<span data-ttu-id="41a5f-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="41a5f-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="41a5f-152">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="41a5f-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41a5f-153">Comentários</span><span class="sxs-lookup"><span data-stu-id="41a5f-153">Remarks</span></span>  

 <span data-ttu-id="41a5f-154">Este elemento de configuração contém uma instância X509Certificate2 usada ao autenticar vizinhos na malha par.</span><span class="sxs-lookup"><span data-stu-id="41a5f-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="41a5f-155">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="41a5f-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41a5f-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41a5f-156">Example</span></span>  

 <span data-ttu-id="41a5f-157">O código a seguir especifica como localizar o certificado usado em um cenário ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="41a5f-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41a5f-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="41a5f-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="41a5f-159">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="41a5f-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="41a5f-160">Rede peer-to-peer</span><span class="sxs-lookup"><span data-stu-id="41a5f-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="41a5f-161">[Autenticação de mensagem de canal par](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="41a5f-161">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="41a5f-162">[Autenticação personalizada do canal par](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="41a5f-162">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="41a5f-163">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="41a5f-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
