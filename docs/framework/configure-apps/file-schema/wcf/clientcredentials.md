---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400507"
---
# <a name="clientcredentials"></a><span data-ttu-id="91672-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="91672-101">\<clientCredentials></span></span>
<span data-ttu-id="91672-102">Especifica as credenciais usadas para autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="91672-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
<span data-ttu-id="91672-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91672-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91672-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="91672-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="91672-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="91672-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="91672-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="91672-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="91672-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="91672-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="91672-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientCredentials >**</span><span class="sxs-lookup"><span data-stu-id="91672-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91672-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91672-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91672-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="91672-110">Attributes and Elements</span></span>  
 <span data-ttu-id="91672-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="91672-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91672-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="91672-112">Attributes</span></span>  
  
|<span data-ttu-id="91672-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="91672-113">Attribute</span></span>|<span data-ttu-id="91672-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="91672-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="91672-115">Um valor booliano que especifica se um usuário interativo pode estar envolvido na seleção de uma credencial de cliente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="91672-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="91672-116">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="91672-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="91672-117">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="91672-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91672-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="91672-118">Child Elements</span></span>  
  
|<span data-ttu-id="91672-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="91672-119">Element</span></span>|<span data-ttu-id="91672-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="91672-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91672-121">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="91672-121">\<clientCertificate></span></span>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="91672-122">Especifica o certificado usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="91672-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="91672-123">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="91672-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="91672-124">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="91672-124">\<httpDigest></span></span>](httpdigest-element.md)|<span data-ttu-id="91672-125">Especifica um resumo usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="91672-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="91672-126">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="91672-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="91672-127">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="91672-127">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="91672-128">Especifica um tipo de token personalizado usado para autenticar o cliente para um serviço de token seguro (STS).</span><span class="sxs-lookup"><span data-stu-id="91672-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="91672-129">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="91672-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="91672-130">\<peer></span><span class="sxs-lookup"><span data-stu-id="91672-130">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="91672-131">Especifica uma credencial par atual.</span><span class="sxs-lookup"><span data-stu-id="91672-131">Specifies a current peer credential.</span></span> <span data-ttu-id="91672-132">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="91672-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="91672-133">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="91672-133">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="91672-134">Especifica o certificado usado para autenticar o serviço para o cliente e fornece uma estrutura para definir as opções de certificado.</span><span class="sxs-lookup"><span data-stu-id="91672-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="91672-135">Esse certificado deve ser fornecido fora de banda do serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="91672-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="91672-136">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="91672-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="91672-137">\<windows></span><span class="sxs-lookup"><span data-stu-id="91672-137">\<windows></span></span>](windows-of-clientcredentials-element.md)|<span data-ttu-id="91672-138">Especifica uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="91672-138">Specifies a Windows credential.</span></span> <span data-ttu-id="91672-139">O padrão é a credencial do thread atual.</span><span class="sxs-lookup"><span data-stu-id="91672-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="91672-140">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="91672-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91672-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="91672-141">Parent Elements</span></span>  
  
|<span data-ttu-id="91672-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="91672-142">Element</span></span>|<span data-ttu-id="91672-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="91672-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91672-144">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="91672-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="91672-145">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="91672-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91672-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="91672-146">Remarks</span></span>  
 <span data-ttu-id="91672-147">As credenciais do cliente são usadas para autenticar o cliente para serviços em casos em que a autenticação mútua é necessária.</span><span class="sxs-lookup"><span data-stu-id="91672-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="91672-148">Esta seção de configuração também pode ser usada para especificar certificados de serviço para cenários em que o cliente deve proteger mensagens para um serviço com o certificado do serviço.</span><span class="sxs-lookup"><span data-stu-id="91672-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91672-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91672-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="91672-150">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="91672-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="91672-151">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="91672-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
