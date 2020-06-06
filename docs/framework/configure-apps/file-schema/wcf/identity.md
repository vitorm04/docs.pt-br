---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 15c9e38a141fc294c47863b1a932711444ac079a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855146"
---
# \<identity>
<span data-ttu-id="89e54-101">O elemento Identity permite que um desenvolvedor cliente especifique em tempo de design a identidade esperada do serviço.</span><span class="sxs-lookup"><span data-stu-id="89e54-101">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="89e54-102">No processo de handshake entre o cliente e o serviço, a infraestrutura Windows Communication Foundation (WCF) garantirá que a identidade do serviço esperado corresponda aos valores desse elemento e, portanto, possa ser autenticada.</span><span class="sxs-lookup"><span data-stu-id="89e54-102">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="89e54-103">Para obter mais informações, consulte [identidade de serviço e autenticação](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="89e54-103">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
## <a name="syntax"></a><span data-ttu-id="89e54-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89e54-104">Syntax</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89e54-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="89e54-105">Attributes and Elements</span></span>  
 <span data-ttu-id="89e54-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="89e54-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89e54-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="89e54-107">Attributes</span></span>  
 <span data-ttu-id="89e54-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="89e54-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="89e54-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="89e54-109">Child Elements</span></span>  
  
|<span data-ttu-id="89e54-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="89e54-110">Element</span></span>|<span data-ttu-id="89e54-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="89e54-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89e54-112">certificado</span><span class="sxs-lookup"><span data-stu-id="89e54-112">certificate</span></span>|<span data-ttu-id="89e54-113">Especifica as configurações de um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="89e54-113">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="89e54-114">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.CertificateElement> .</span><span class="sxs-lookup"><span data-stu-id="89e54-114">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="89e54-115">Ele contém um atributo `encodedValue` que é uma cadeia de caracteres, que especifica o valor codificado por esse certificado.</span><span class="sxs-lookup"><span data-stu-id="89e54-115">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="89e54-116">certificateReference</span><span class="sxs-lookup"><span data-stu-id="89e54-116">certificateReference</span></span>|<span data-ttu-id="89e54-117">Especifica as configurações para a validação de certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="89e54-117">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="89e54-118">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .</span><span class="sxs-lookup"><span data-stu-id="89e54-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="89e54-119">dns</span><span class="sxs-lookup"><span data-stu-id="89e54-119">dns</span></span>|<span data-ttu-id="89e54-120">Especifica o DNS de um certificado X. 509 usado para autenticar um serviço.</span><span class="sxs-lookup"><span data-stu-id="89e54-120">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="89e54-121">Esse elemento contém um atributo `value` que é uma cadeia de caracteres e contém a identidade real.</span><span class="sxs-lookup"><span data-stu-id="89e54-121">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="89e54-122">rsa</span><span class="sxs-lookup"><span data-stu-id="89e54-122">rsa</span></span>|<span data-ttu-id="89e54-123">Especifica o valor do campo RSA de um certificado X. 509 usado para autenticar um serviço para um cliente.</span><span class="sxs-lookup"><span data-stu-id="89e54-123">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="89e54-124">Esse elemento contém um atributo `value` que é uma cadeia de caracteres e contém a identidade real</span><span class="sxs-lookup"><span data-stu-id="89e54-124">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="89e54-125">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="89e54-125">servicePrincipalName</span></span>|<span data-ttu-id="89e54-126">Especifica uma identidade de SPN (nome principal do servidor), que é o nome principal usado por um cliente para identificar exclusivamente uma instância de um serviço.</span><span class="sxs-lookup"><span data-stu-id="89e54-126">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="89e54-127">Esse elemento contém um atributo `value` que é uma cadeia de caracteres e contém o nome da entidade de segurança real.</span><span class="sxs-lookup"><span data-stu-id="89e54-127">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="89e54-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="89e54-128">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="89e54-129">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="89e54-129">userPrincipalName</span></span>|<span data-ttu-id="89e54-130">Especifica uma identidade de UPN (nome principal do usuário), que é o tipo de nome de logon de um usuário em uma rede.</span><span class="sxs-lookup"><span data-stu-id="89e54-130">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="89e54-131">O nome principal do usuário consiste no nome do objeto de usuário usado em Active Directory, seguido pelo símbolo arroba ( \@ ) e, em seguida, normalmente, o domínio pai do sistema de nome de domínio.</span><span class="sxs-lookup"><span data-stu-id="89e54-131">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="89e54-132">Por exemplo, Jeff na árvore de domínio Fabrikam.com pode ter o nome principal do usuário [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .</span><span class="sxs-lookup"><span data-stu-id="89e54-132">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="89e54-133">Esse elemento contém um atributo `value` que é uma cadeia de caracteres e contém o nome da entidade de segurança real.</span><span class="sxs-lookup"><span data-stu-id="89e54-133">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="89e54-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="89e54-134">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89e54-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="89e54-135">Parent Elements</span></span>  
  
|<span data-ttu-id="89e54-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="89e54-136">Element</span></span>|<span data-ttu-id="89e54-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="89e54-137">Description</span></span>|  
|-------------|-----------------|  
|[\<custom>](custom.md)|<span data-ttu-id="89e54-138">Especifica um resolvedor de pares personalizado para um netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="89e54-138">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="89e54-139">Configura os pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="89e54-139">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="89e54-140">\<endpoint>desse\<client></span><span class="sxs-lookup"><span data-stu-id="89e54-140">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="89e54-141">Configura os pontos de extremidade do canal.</span><span class="sxs-lookup"><span data-stu-id="89e54-141">Configures channel endpoints.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="89e54-142">Especifica o serviço de token de segurança (STS) para o serviço federado.</span><span class="sxs-lookup"><span data-stu-id="89e54-142">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="89e54-143">Especifica o ponto de extremidade de metadados para o serviço de token de segurança (STS) de um serviço federado.</span><span class="sxs-lookup"><span data-stu-id="89e54-143">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="89e54-144">Define parâmetros para um token emitido em uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="89e54-144">Defines parameters for an issued token in a custom binding.</span></span>|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="89e54-145">Especifica um serviço de token de segurança (STS) local.</span><span class="sxs-lookup"><span data-stu-id="89e54-145">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89e54-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="89e54-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="89e54-147">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="89e54-147">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="89e54-148">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="89e54-148">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
