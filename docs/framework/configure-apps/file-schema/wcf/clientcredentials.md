---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: c3e756f49b7054d6553eb6c3f1850f0fbce14943
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926127"
---
# <a name="clientcredentials"></a><span data-ttu-id="b8824-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b8824-101">\<clientCredentials></span></span>
<span data-ttu-id="b8824-102">Especifica as credenciais usadas para autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b8824-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="b8824-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8824-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8824-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b8824-104">\<behaviors></span></span>  
<span data-ttu-id="b8824-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b8824-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="b8824-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="b8824-106">\<behavior></span></span>  
<span data-ttu-id="b8824-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b8824-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8824-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8824-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8824-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b8824-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b8824-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b8824-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8824-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b8824-111">Attributes</span></span>  
  
|<span data-ttu-id="b8824-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="b8824-112">Attribute</span></span>|<span data-ttu-id="b8824-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8824-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="b8824-114">Um valor booliano que especifica se um usuário interativo pode estar envolvido na seleção de uma credencial de cliente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b8824-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="b8824-115">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="b8824-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="b8824-116">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="b8824-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8824-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b8824-117">Child Elements</span></span>  
  
|<span data-ttu-id="b8824-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8824-118">Element</span></span>|<span data-ttu-id="b8824-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8824-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8824-120">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="b8824-120">\<clientCertificate></span></span>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="b8824-121">Especifica o certificado usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b8824-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="b8824-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b8824-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="b8824-123">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="b8824-123">\<httpDigest></span></span>](httpdigest-element.md)|<span data-ttu-id="b8824-124">Especifica um resumo usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b8824-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="b8824-125">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b8824-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="b8824-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="b8824-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="b8824-127">Especifica um tipo de token personalizado usado para autenticar o cliente para um serviço de token seguro (STS).</span><span class="sxs-lookup"><span data-stu-id="b8824-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="b8824-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b8824-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="b8824-129">\<peer></span><span class="sxs-lookup"><span data-stu-id="b8824-129">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="b8824-130">Especifica uma credencial par atual.</span><span class="sxs-lookup"><span data-stu-id="b8824-130">Specifies a current peer credential.</span></span> <span data-ttu-id="b8824-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="b8824-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="b8824-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="b8824-132">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="b8824-133">Especifica o certificado usado para autenticar o serviço para o cliente e fornece uma estrutura para definir as opções de certificado.</span><span class="sxs-lookup"><span data-stu-id="b8824-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="b8824-134">Esse certificado deve ser fornecido fora de banda do serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="b8824-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="b8824-135">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b8824-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="b8824-136">\<windows></span><span class="sxs-lookup"><span data-stu-id="b8824-136">\<windows></span></span>](windows-of-clientcredentials-element.md)|<span data-ttu-id="b8824-137">Especifica uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="b8824-137">Specifies a Windows credential.</span></span> <span data-ttu-id="b8824-138">O padrão é a credencial do thread atual.</span><span class="sxs-lookup"><span data-stu-id="b8824-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="b8824-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b8824-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8824-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b8824-140">Parent Elements</span></span>  
  
|<span data-ttu-id="b8824-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8824-141">Element</span></span>|<span data-ttu-id="b8824-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8824-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8824-143">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="b8824-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b8824-144">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b8824-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8824-145">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8824-145">Remarks</span></span>  
 <span data-ttu-id="b8824-146">As credenciais do cliente são usadas para autenticar o cliente para serviços em casos em que a autenticação mútua é necessária.</span><span class="sxs-lookup"><span data-stu-id="b8824-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="b8824-147">Esta seção de configuração também pode ser usada para especificar certificados de serviço para cenários em que o cliente deve proteger mensagens para um serviço com o certificado do serviço.</span><span class="sxs-lookup"><span data-stu-id="b8824-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8824-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8824-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="b8824-149">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b8824-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b8824-150">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="b8824-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
