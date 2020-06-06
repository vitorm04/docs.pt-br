---
title: <certificate>do <clientCertificate> elemento
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: d0c4ef9d3657d2dfa787feb3576beda09d1997a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400541"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="de28e-102">\<certificate>do \<clientCertificate> elemento</span><span class="sxs-lookup"><span data-stu-id="de28e-102">\<certificate> of \<clientCertificate> Element</span></span>
<span data-ttu-id="de28e-103">Especifica um certificado X. 509 usado para assinar e criptografar mensagens.</span><span class="sxs-lookup"><span data-stu-id="de28e-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="de28e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de28e-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de28e-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="de28e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="de28e-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="de28e-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de28e-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="de28e-107">Attributes</span></span>  
  
|<span data-ttu-id="de28e-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="de28e-108">Attribute</span></span>|<span data-ttu-id="de28e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="de28e-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="de28e-110">Uma cadeia de caracteres que contém o valor a ser procurado no repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="de28e-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="de28e-111">O tipo contido no atributo deve atender aos requisitos do X509FindType especificado.</span><span class="sxs-lookup"><span data-stu-id="de28e-111">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="de28e-112">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="de28e-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="de28e-113">Especifica o local do repositório de certificados X. 509 que o cliente usa para validar o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="de28e-113">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="de28e-114">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="de28e-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="de28e-115">-LocalMachine: o repositório de certificados atribuído ao computador local.</span><span class="sxs-lookup"><span data-stu-id="de28e-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="de28e-116">-CurrentUser: o repositório de certificados atribuído ao usuário atual.</span><span class="sxs-lookup"><span data-stu-id="de28e-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="de28e-117">O padrão é LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="de28e-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="de28e-118">Especifica o nome do repositório de certificados X.509 a ser aberto.</span><span class="sxs-lookup"><span data-stu-id="de28e-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="de28e-119">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="de28e-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="de28e-120">-Catálogo: repositório de certificados para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="de28e-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="de28e-121">-AuthRoot: repositório de certificados para CAs (autoridades de certificação) de terceiros.</span><span class="sxs-lookup"><span data-stu-id="de28e-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="de28e-122">-CertificationAuthority: repositório de certificados para CAs (autoridades de certificação) intermediárias.</span><span class="sxs-lookup"><span data-stu-id="de28e-122">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="de28e-123">-Não permitido: repositório de certificados para certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="de28e-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="de28e-124">-My: repositório de certificados para certificados pessoais.</span><span class="sxs-lookup"><span data-stu-id="de28e-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="de28e-125">-Root: repositório de certificados para autoridades de certificação raiz confiáveis (CAs).</span><span class="sxs-lookup"><span data-stu-id="de28e-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="de28e-126">-TrustedPeople: repositório de certificados para pessoas e recursos diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="de28e-126">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="de28e-127">-TrustedPublisher: repositório de certificados para editores diretamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="de28e-127">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="de28e-128">O padrão é My.</span><span class="sxs-lookup"><span data-stu-id="de28e-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="de28e-129">Define o tipo de pesquisa de X.509 a ser executada.</span><span class="sxs-lookup"><span data-stu-id="de28e-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="de28e-130">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="de28e-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="de28e-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="de28e-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="de28e-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="de28e-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="de28e-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="de28e-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="de28e-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="de28e-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="de28e-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="de28e-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="de28e-136">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="de28e-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="de28e-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="de28e-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="de28e-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="de28e-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="de28e-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="de28e-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="de28e-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="de28e-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="de28e-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="de28e-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="de28e-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="de28e-142">-   FindByExtension</span></span><br /><span data-ttu-id="de28e-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="de28e-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="de28e-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="de28e-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="de28e-145">O tipo contido no `findValue` atributo deve atender aos requisitos do X509FindType especificado.</span><span class="sxs-lookup"><span data-stu-id="de28e-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="de28e-146">O valor padrão é FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="de28e-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de28e-147">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="de28e-147">Child Elements</span></span>  
 <span data-ttu-id="de28e-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="de28e-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de28e-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="de28e-149">Parent Elements</span></span>  
  
|<span data-ttu-id="de28e-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="de28e-150">Element</span></span>|<span data-ttu-id="de28e-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="de28e-151">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="de28e-152">Comentários</span><span class="sxs-lookup"><span data-stu-id="de28e-152">Remarks</span></span>  
 <span data-ttu-id="de28e-153">O `<certificate>` elemento é usado quando o serviço deve ter o certificado do cliente com antecedência para se comunicar com segurança com o cliente.</span><span class="sxs-lookup"><span data-stu-id="de28e-153">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="de28e-154">Isso ocorre ao usar o padrão de comunicação duplex.</span><span class="sxs-lookup"><span data-stu-id="de28e-154">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="de28e-155">No padrão de solicitação/resposta mais comum, o cliente inclui seu certificado na solicitação, que o serviço usa para criptografar e assinar sua resposta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="de28e-155">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="de28e-156">No padrão de comunicação duplex, no entanto, o serviço não tem uma solicitação do cliente e, portanto, precisa do certificado do cliente com antecedência para proteger a mensagem para o cliente.</span><span class="sxs-lookup"><span data-stu-id="de28e-156">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="de28e-157">Portanto, você deve obter o certificado do cliente em uma negociação fora de banda e especificar o certificado usando esse elemento.</span><span class="sxs-lookup"><span data-stu-id="de28e-157">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="de28e-158">Para obter mais informações sobre os serviços duplex, consulte [como: criar um contrato duplex](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="de28e-158">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de28e-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de28e-159">Example</span></span>  
 <span data-ttu-id="de28e-160">O código a seguir especifica como encontrar um certificado X. 509 apropriado e um tipo de validação personalizado no `<authentication>` elemento.</span><span class="sxs-lookup"><span data-stu-id="de28e-160">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="de28e-161">Confira também</span><span class="sxs-lookup"><span data-stu-id="de28e-161">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="de28e-162">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="de28e-162">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="de28e-163">Como criar um serviço que utiliza um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="de28e-163">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="de28e-164">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="de28e-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
