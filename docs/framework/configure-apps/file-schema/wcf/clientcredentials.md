---
title: '&lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8a1b3f5f7e8eea555be10870bc00f9b975c57a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="a1648-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="a1648-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="a1648-103">Especifica as credenciais usadas para autenticar o cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="a1648-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="a1648-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a1648-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a1648-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="a1648-105">\<behaviors></span></span>  
<span data-ttu-id="a1648-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a1648-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="a1648-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="a1648-107">\<behavior></span></span>  
<span data-ttu-id="a1648-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="a1648-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1648-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1648-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1648-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a1648-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a1648-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a1648-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1648-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1648-112">Attributes</span></span>  
  
|<span data-ttu-id="a1648-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="a1648-113">Attribute</span></span>|<span data-ttu-id="a1648-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1648-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="a1648-115">Um valor booleano que especifica se um usuário interativo pode estar envolvido na seleção de uma credencial de cliente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a1648-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="a1648-116">O valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="a1648-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="a1648-117">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="a1648-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1648-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a1648-118">Child Elements</span></span>  
  
|<span data-ttu-id="a1648-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1648-119">Element</span></span>|<span data-ttu-id="a1648-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1648-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1648-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="a1648-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="a1648-122">Especifica o certificado usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a1648-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="a1648-123">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a1648-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a1648-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="a1648-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="a1648-125">Especifica um digest usado para autenticar o cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a1648-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="a1648-126">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a1648-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="a1648-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="a1648-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="a1648-128">Especifica um tipo de token personalizado usado para autenticar o cliente para um Token STS (serviço seguro).</span><span class="sxs-lookup"><span data-stu-id="a1648-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="a1648-129">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a1648-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="a1648-130">\<par ></span><span class="sxs-lookup"><span data-stu-id="a1648-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="a1648-131">Especifica uma credencial de ponto a ponto atual.</span><span class="sxs-lookup"><span data-stu-id="a1648-131">Specifies a current peer credential.</span></span> <span data-ttu-id="a1648-132">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="a1648-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="a1648-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="a1648-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a1648-134">Especifica o certificado usado para autenticar o serviço para o cliente e fornece uma estrutura para definir opções de certificado.</span><span class="sxs-lookup"><span data-stu-id="a1648-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="a1648-135">Esse certificado deve ser fornecida fora de banda do serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="a1648-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="a1648-136">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a1648-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a1648-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="a1648-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="a1648-138">Especifica uma credencial do Windows.</span><span class="sxs-lookup"><span data-stu-id="a1648-138">Specifies a Windows credential.</span></span> <span data-ttu-id="a1648-139">O padrão é a credencial do thread atual.</span><span class="sxs-lookup"><span data-stu-id="a1648-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="a1648-140">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a1648-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1648-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a1648-141">Parent Elements</span></span>  
  
|<span data-ttu-id="a1648-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1648-142">Element</span></span>|<span data-ttu-id="a1648-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1648-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1648-144">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="a1648-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a1648-145">Especifica um comportamento de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a1648-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1648-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1648-146">Remarks</span></span>  
 <span data-ttu-id="a1648-147">As credenciais do cliente são usadas para autenticar o cliente para serviços em casos em que a autenticação mútua é necessária.</span><span class="sxs-lookup"><span data-stu-id="a1648-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="a1648-148">Esta seção de configuração também pode ser usada para especificar os certificados de serviço para cenários em que o cliente deve proteger as mensagens para um serviço com o certificado do serviço.</span><span class="sxs-lookup"><span data-stu-id="a1648-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1648-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1648-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="a1648-150">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="a1648-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="a1648-151">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)</span><span class="sxs-lookup"><span data-stu-id="a1648-151">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md)</span></span>
