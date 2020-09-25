---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 6094006df24ee824c419a783ab29d7604757577c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201454"
---
# \<clientCredentials>

<span data-ttu-id="ea4b9-101">Especifica as credenciais usadas para autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-101">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="ea4b9-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea4b9-102">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea4b9-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ea4b9-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ea4b9-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea4b9-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="ea4b9-105">Attributes</span></span>  
  
|<span data-ttu-id="ea4b9-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="ea4b9-106">Attribute</span></span>|<span data-ttu-id="ea4b9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea4b9-107">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="ea4b9-108">Um valor booliano que especifica se um usuário interativo pode estar envolvido na seleção de uma credencial de cliente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-108">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="ea4b9-109">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-109">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="ea4b9-110">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-110">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea4b9-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ea4b9-111">Child Elements</span></span>  
  
|<span data-ttu-id="ea4b9-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="ea4b9-112">Element</span></span>|<span data-ttu-id="ea4b9-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea4b9-113">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="ea4b9-114">Especifica o certificado usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-114">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="ea4b9-115">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="ea4b9-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="ea4b9-116">Especifica um resumo usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-116">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="ea4b9-117">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HttpDigestClientElement> .</span><span class="sxs-lookup"><span data-stu-id="ea4b9-117">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="ea4b9-118">Especifica um tipo de token personalizado usado para autenticar o cliente para um serviço de token seguro (STS).</span><span class="sxs-lookup"><span data-stu-id="ea4b9-118">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="ea4b9-119">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenClientElement> .</span><span class="sxs-lookup"><span data-stu-id="ea4b9-119">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="ea4b9-120">Especifica uma credencial par atual.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-120">Specifies a current peer credential.</span></span> <span data-ttu-id="ea4b9-121">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="ea4b9-121">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="ea4b9-122">Especifica o certificado usado para autenticar o serviço para o cliente e fornece uma estrutura para definir as opções de certificado.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-122">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="ea4b9-123">Esse certificado deve ser fornecido fora de banda do serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-123">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="ea4b9-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="ea4b9-124">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="ea4b9-125">Especifica uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-125">Specifies a Windows credential.</span></span> <span data-ttu-id="ea4b9-126">O padrão é a credencial do thread atual.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-126">The default is the credential of the current thread.</span></span> <span data-ttu-id="ea4b9-127">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsClientElement> .</span><span class="sxs-lookup"><span data-stu-id="ea4b9-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea4b9-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ea4b9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ea4b9-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="ea4b9-129">Element</span></span>|<span data-ttu-id="ea4b9-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea4b9-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ea4b9-131">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-131">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea4b9-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea4b9-132">Remarks</span></span>  

 <span data-ttu-id="ea4b9-133">As credenciais do cliente são usadas para autenticar o cliente para serviços em casos em que a autenticação mútua é necessária.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-133">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="ea4b9-134">Esta seção de configuração também pode ser usada para especificar certificados de serviço para cenários em que o cliente deve proteger mensagens para um serviço com o certificado do serviço.</span><span class="sxs-lookup"><span data-stu-id="ea4b9-134">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4b9-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="ea4b9-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="ea4b9-136">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="ea4b9-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ea4b9-137">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="ea4b9-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
