---
title: Elemento <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400549"
---
# <a name="certificate-element"></a><span data-ttu-id="5d572-102">Elemento \<certificate></span><span class="sxs-lookup"><span data-stu-id="5d572-102">\<certificate> Element</span></span>
<span data-ttu-id="5d572-103">Especifica um certificado X. 509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="5d572-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="5d572-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d572-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d572-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5d572-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5d572-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5d572-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d572-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d572-107">Attributes</span></span>  
  
|<span data-ttu-id="5d572-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="5d572-108">Attribute</span></span>|<span data-ttu-id="5d572-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d572-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="5d572-110">Uma cadeia de caracteres que contém o valor a ser procurado no repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="5d572-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="5d572-111">O tipo contido no atributo deve atender aos requisitos do especificado `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="5d572-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="5d572-112">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="5d572-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="5d572-113">Especifica o local do repositório de certificados X. 509 que o cliente usa para validar o certificado do par.</span><span class="sxs-lookup"><span data-stu-id="5d572-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="5d572-114">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="5d572-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5d572-115">-LocalMachine: o repositório de certificados atribuído ao computador local.</span><span class="sxs-lookup"><span data-stu-id="5d572-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="5d572-116">-CurrentUser: o repositório de certificados atribuído ao usuário atual.</span><span class="sxs-lookup"><span data-stu-id="5d572-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="5d572-117">O padrão é LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5d572-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="5d572-118">Especifica o nome do repositório de certificados X.509 a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="5d572-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="5d572-119">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="5d572-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5d572-120">-Catálogo: repositório de certificados para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="5d572-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="5d572-121">-AuthRoot: repositório de certificados para CAs (autoridades de certificação) de terceiros.</span><span class="sxs-lookup"><span data-stu-id="5d572-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="5d572-122">-CertificateAuthority: repositório de certificados para CAs (autoridades de certificação) intermediárias.</span><span class="sxs-lookup"><span data-stu-id="5d572-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="5d572-123">-Não permitido: repositório de certificados para certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="5d572-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="5d572-124">-My: repositório de certificados para certificados pessoais.</span><span class="sxs-lookup"><span data-stu-id="5d572-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="5d572-125">-Root: repositório de certificados para autoridades de certificação raiz confiáveis (CAs).</span><span class="sxs-lookup"><span data-stu-id="5d572-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="5d572-126">-TrustedPeople: repositório de certificados para pessoas e recursos diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5d572-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="5d572-127">-TrustedPublisher: repositório de certificados para Publicadores diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5d572-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="5d572-128">O padrão é My.</span><span class="sxs-lookup"><span data-stu-id="5d572-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="5d572-129">Define o tipo de pesquisa de X.509 a ser executada.</span><span class="sxs-lookup"><span data-stu-id="5d572-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="5d572-130">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="5d572-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5d572-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="5d572-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="5d572-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="5d572-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="5d572-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="5d572-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="5d572-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="5d572-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="5d572-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="5d572-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="5d572-136">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="5d572-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="5d572-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="5d572-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="5d572-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="5d572-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="5d572-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="5d572-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="5d572-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="5d572-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="5d572-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="5d572-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="5d572-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="5d572-142">-   FindByExtension</span></span><br /><span data-ttu-id="5d572-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="5d572-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="5d572-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="5d572-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="5d572-145">O tipo contido no `findValue` atributo deve atender aos requisitos do especificado `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="5d572-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="5d572-146">O valor padrão é FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="5d572-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d572-147">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5d572-147">Child Elements</span></span>  
 <span data-ttu-id="5d572-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5d572-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d572-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5d572-149">Parent Elements</span></span>  
  
|<span data-ttu-id="5d572-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="5d572-150">Element</span></span>|<span data-ttu-id="5d572-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d572-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="5d572-152">Especifica as credenciais usadas ao autenticar clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="5d572-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d572-153">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d572-153">Remarks</span></span>  
 <span data-ttu-id="5d572-154">Este elemento de configuração contém uma instância X509Certificate2 usada ao autenticar vizinhos na malha par.</span><span class="sxs-lookup"><span data-stu-id="5d572-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="5d572-155">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="5d572-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d572-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d572-156">Example</span></span>  
 <span data-ttu-id="5d572-157">O código a seguir especifica como localizar o certificado usado em um cenário ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="5d572-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d572-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="5d572-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="5d572-159">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="5d572-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5d572-160">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="5d572-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="5d572-161">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5d572-161">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="5d572-162">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5d572-162">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="5d572-163">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="5d572-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
