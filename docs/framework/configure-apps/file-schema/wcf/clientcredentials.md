---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: ebe976df9af0c316e95a1e089412e57a575a6df1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673351"
---
# <a name="clientcredentials"></a><span data-ttu-id="af3a1-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="af3a1-101">\<clientCredentials></span></span>
<span data-ttu-id="af3a1-102">Especifica as credenciais usadas para autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="af3a1-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="af3a1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="af3a1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="af3a1-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="af3a1-104">\<behaviors></span></span>  
<span data-ttu-id="af3a1-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="af3a1-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="af3a1-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="af3a1-106">\<behavior></span></span>  
<span data-ttu-id="af3a1-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="af3a1-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af3a1-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af3a1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af3a1-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="af3a1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="af3a1-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="af3a1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af3a1-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="af3a1-111">Attributes</span></span>  
  
|<span data-ttu-id="af3a1-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="af3a1-112">Attribute</span></span>|<span data-ttu-id="af3a1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="af3a1-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="af3a1-114">Um valor booliano que especifica se um usuário interativo pode estar envolvido na seleção de uma credencial de cliente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="af3a1-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="af3a1-115">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="af3a1-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="af3a1-116">Uma cadeia de caracteres que especifica o tipo desse elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="af3a1-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af3a1-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="af3a1-117">Child Elements</span></span>  
  
|<span data-ttu-id="af3a1-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="af3a1-118">Element</span></span>|<span data-ttu-id="af3a1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="af3a1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af3a1-120">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="af3a1-120">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="af3a1-121">Especifica o certificado usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="af3a1-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="af3a1-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="af3a1-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="af3a1-123">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="af3a1-123">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="af3a1-124">Especifica um resumo usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="af3a1-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="af3a1-125">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="af3a1-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="af3a1-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="af3a1-126">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="af3a1-127">Especifica um tipo de token personalizado usado para autenticar o cliente para um Secure Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="af3a1-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="af3a1-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="af3a1-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="af3a1-129">\<peer></span><span class="sxs-lookup"><span data-stu-id="af3a1-129">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="af3a1-130">Especifica uma credencial de par atual.</span><span class="sxs-lookup"><span data-stu-id="af3a1-130">Specifies a current peer credential.</span></span> <span data-ttu-id="af3a1-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="af3a1-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="af3a1-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="af3a1-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="af3a1-133">Especifica o certificado usado para autenticar o serviço ao cliente e fornece uma estrutura para definir opções de certificado.</span><span class="sxs-lookup"><span data-stu-id="af3a1-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="af3a1-134">Esse certificado deve ser fornecida fora de banda do serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="af3a1-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="af3a1-135">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="af3a1-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="af3a1-136">\<windows></span><span class="sxs-lookup"><span data-stu-id="af3a1-136">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="af3a1-137">Especifica uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="af3a1-137">Specifies a Windows credential.</span></span> <span data-ttu-id="af3a1-138">O padrão é a credencial do thread atual.</span><span class="sxs-lookup"><span data-stu-id="af3a1-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="af3a1-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="af3a1-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af3a1-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="af3a1-140">Parent Elements</span></span>  
  
|<span data-ttu-id="af3a1-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="af3a1-141">Element</span></span>|<span data-ttu-id="af3a1-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="af3a1-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af3a1-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="af3a1-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="af3a1-144">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="af3a1-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af3a1-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="af3a1-145">Remarks</span></span>  
 <span data-ttu-id="af3a1-146">As credenciais do cliente são usadas para autenticar o cliente para serviços em casos em que a autenticação mútua é necessária.</span><span class="sxs-lookup"><span data-stu-id="af3a1-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="af3a1-147">Esta seção de configuração também pode ser usada para especificar os certificados de serviço para cenários em que o cliente deve proteger as mensagens para um serviço com o certificado do serviço.</span><span class="sxs-lookup"><span data-stu-id="af3a1-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af3a1-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af3a1-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="af3a1-149">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="af3a1-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="af3a1-150">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="af3a1-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
